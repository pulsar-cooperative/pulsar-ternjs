# atom-ternjs

<!-- Pulsar Cooperative Package Repository Template, place underneath the first h1 heading in the original readme -->

> [!NOTE]
> This package was originally created by [`tststs`](https://github.com/tststs) and has now been forked under the [`pulsar-cooperative`](https://github.com/pulsar-cooperative) organization.
> By forking this package we hope to allow new maintainers to work on this package as needed, without being limited by its previous [archived] status, helping to ensure this package stays up to date and functional for as long as possible without the huge responsibility implied by forking and maintaining this under a personal account.
>
> For more info on the Pulsar Cooperative initiative please read [the documentation](https://github.com/pulsar-cooperative/.github/blob/main/CONTRIBUTING.md).

<!-- Original Readme to follow -->

> JavaScript code intelligence for atom with [Tern](https://github.com/ternjs/tern).
Adds support for ES5, ES6, ES7, ES8, Node.js and more. Extendable via plugins.
Uses suggestion provider by [autocomplete-plus](https://github.com/pulsar-edit/autocomplete-plus).

## Get started (configure your project)

* Open any JavaScript file from within your project
* Navigate to Packages -> Pulsar Ternjs -> Configure project
* The config view appears. Configure to your needs.
* Hit "Save & Restart Server" to create/update the .tern-project file. The configuration is now active.

## Get started (in case you can't use configure your project)
* In your project root create a file named .tern-project. See docs @ http://ternjs.net/doc/manual.html#configuration.
* Restart the server via *Packages -> Pulsar Ternjs -> Restart server*

Example `.tern-project` file (customize to your own needs):

```json
{
  "ecmaVersion": 8,
  "libs": [
    "browser"
  ],
  "loadEagerly": [
    "path/to/your/js/**/*.js"
  ],
  "dontLoad": [
    "node_modules/**",
    "path/to/your/js/**/*.js"
  ],
  "plugins": {
    "es_modules": {},
    "node": {},
    "doc_comment": {
      "fullDocs": true,
      "strong": true
    }
  }
}
```

### EcmaVersion
* 5: use ECMAScript5
* 6: use ECMAScript6
* 7: use ECMAScript7
* 8: use ECMAScript8 (default)

### Libs
* browser: completion for browser features like document.querySelector (optional)
* chai: completion for chai (optional)
* jquery: completion for jQuery (optional)
* react: completion for React (optional)
* underscore: completion for underscore (optional)

### Options
* loadEagerly: provide the path to your projects JavaScript. For relative paths do not use `./` as a prefix. This sometimes leads to an unexpected behavior.
* **loadEagerly is expensive. Do not add paths like `node_modules`.**
* dontLoad: can be used to prevent Tern from loading certain files. It also takes an array of file names or glob patterns.

### Plugins
* For a list of build in server plugins, visit: http://ternjs.net/doc/manual.html#plugins

### Example configurations
* RequireJS: https://github.com/tststs/atom-ternjs-using-requirejs

### Keybindings
List of [keybindings](#features).
To use your own keybindings goto `pulsar-ternjs` package settings and disable keybindings.

## Third party plugins
In order to use third party plugins (e.g. [tern-node-express](https://github.com/angelozerr/tern-node-express)):
```
$ cd ~/.pulsar/packages/pulsar-ternjs
$ npm install tern-node-express
```
Add the plugin to your .tern-project file:
```json
{
  "ecmaVersion": 8,
  "libs": [
    "browser"
  ],
  "loadEagerly": [
    "app/**/*.js"
  ],
  "plugins": {
    "node-express": {}
  }
}
```

Third party plugins are still an issue and sometimes do not work as expected, especially if the plugin requires a tern version that does not match the tern version that is used by pulsar-ternjs.

Restart the server: *Packages -> Pulsar Ternjs -> Restart server*

## .tern-project created/modified
* After the file was created or has been modified, restart the server via *Packages -> Pulsar Ternjs -> Restart server*

## Features
* Completion (autocompletion triggers automatically), or via the keybindings:
  * <kbd>ctrl+space</kbd>
  * <kbd>ctrl+alt+space</kbd> (force autocompletion in any context)

![pulsar-ternjs](http://www.tobias-schubert.com/github/completion-1.png)

![pulsar-ternjs](http://www.tobias-schubert.com/github/completion-2.png)
* Find references (set your cursor position to one of variable, function or instance -> open context-menu and trigger "Find references" or use the keybindings:
  * <kbd>ctrl+shift+r</kbd> (macOS, Windows)
  * <kbd>ctrl+alt+shift+e</kbd> (Linux)

Click any item in the generated reference-list and navigate directly to file and position

![pulsar-ternjs](http://www.tobias-schubert.com/github/reference-1.png)

* Documentation
  * Show documentation for the thing under the cursor via <kbd>alt+o</kbd> (macOS, Windows, Linux)
  ![pulsar-ternjs](http://www.tobias-schubert.com/github/docs.png)
  * Also displayed if a suggestion with a valid documentation is selected in the autocomplete-plus select-list

* Find definition (set your cursor position to one of variable, function or instance -> open context-menu and trigger "Find definition") or use the keybindings:
  * <kbd>cmd+click</kbd> (macOS, Windows, Linux), requires https://web.pulsar-edit.dev/packages/hyperclick. Since <kbd>cmd+click</kbd> is also used for multi-line editing in macOS you should change the default hyperclick settings.
  * <kbd>ctrl+alt+shift+d</kbd> (macOS, Windows, Linux)

* Navigate back or forward
  * <kbd>ctrl+shift+cmd+left</kbd> (macOS, Windows, Linux)
  * <kbd>ctrl+shift+cmd+right</kbd> (macOS, Windows, Linux)

* Rename variable (set your cursor position to a variable -> open context-menu and trigger "Rename") or use the keybindings:
  * <kbd>ctrl+alt+c</kbd> (macOS, Windows)
  * <kbd>ctrl+alt+shift+c</kbd> (Linux)
