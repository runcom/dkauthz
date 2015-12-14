# Credits

Inspired by David's awesome [dkvolume](https://github.com/calavera/dkvolume) and adapted for the authZ api.

# Docker authz extension api.

Go handler to create external authz extensions for Docker.

## Usage

This library is designed to be integrated in your program.

1. Implement the `dkauthz.Plugin` interface.
2. Initialize a `dkauthz.Handler` with your implementation.
3. Call either `ServeTCP` or `ServeUnix` from the `dkauthz.Handler`.

### Example using TCP sockets:

```go
  p := MyAuthZPlugin{}
  h := dkauthz.NewHandler(p)
  h.ServeTCP("test_plugin", ":8080")
```

### Example using Unix sockets:

```go
  p := MyAuthZPlugin{}
  h := dkauthz.NewHandler(p)
  h.ServeUnix("root", "test_plugin")
```

## Full example plugins

- https://github.com/runcom/docker-novolume-plugin

## License

MIT
