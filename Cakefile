require 'shortcake'

use 'cake-publish'
use 'cake-version'

task 'clean', 'clean project', ->
  exec 'rm -rf dist'

task 'build', 'build project', ->
  handroll = require 'handroll'

  bundle = yield handroll.bundle
    entry: 'src/index.coffee'
  yield bundle.write format: 'es'
  yield bundle.write format: 'cjs'

task 'watch', 'watch project', ->
  watch 'src/*.coffee', (filename) ->
    console.log filename, 'modified, rebuilding'
    invoke 'build' if not running 'build'
