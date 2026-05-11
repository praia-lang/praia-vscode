# Praia

Syntax highlighting and editor support for the [Praia](https://praia.sh) programming language in VS Code.

## What is Praia?

Praia is a small, modern scripting language for everyday tasks — servers, scripts, automation. It has a clean syntax, async/await, a useful standard library out of the box (HTTP, JSON, SQLite, crypto, regex), and a single-binary install. See [praia.sh](https://praia.sh) for documentation.

```praia
use "router"
use "middleware"

let app = router.create()
app.use(middleware.jsonBody())

@app.get("/users/:id")
func getUser(req, params) {
    let user = db.findOne("users", {id: params.id})
    if (user == nil) { return http.json({error: "not found"}, 404) }
    return http.json(user)
}

app.listen(8080)
```

## Features

- Syntax highlighting for `.praia` files
- String interpolation: `"Hello, %{name}!"`
- Triple-quoted multiline strings: `"""..."""`
- Nested block comments: `/* outer /* inner */ outer */`
- Shebang detection (`#!/usr/bin/env praia`)
- Bracket matching, auto-closing pairs, smart indent
- Region folding via `// region` / `// endregion`
- Stdlib-aware: highlights for namespaces (`sys`, `http`, `json`, `time`, …) and concurrency primitives (`Lock`, `Queue`, `SharedMap`, `CancellationToken`)

## Recommended settings

Add to your `settings.json` for the best editing experience:

```jsonc
{
    "[praia]": {
        "editor.tabSize": 4,
        "editor.insertSpaces": true,
        "editor.detectIndentation": false
    }
}
```

## Links

- [Language website and docs](https://praia.sh)
- [Praia compiler](https://github.com/praia-lang/praia)
- [Issues & contributions](https://github.com/praia-lang/praia-vscode)

## License

[MIT](https://github.com/praia-lang/praia-vscode/blob/main/LICENSE)
