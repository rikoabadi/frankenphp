# Build TurboPHP Locally

This short guide explains how to compile TurboPHP on your own machine.

## Requirements

- Go 1.22 or newer
- PHP 8.2 or newer compiled with `--enable-embed` and `--enable-zts`
- [xcaddy](https://github.com/caddyserver/xcaddy) build tool

## Steps

1. Clone the repository and enter it:
   ```bash
   git clone <repo-url>
   cd frankenphp
   ```
2. Run the build command:
   ```bash
   CGO_ENABLED=1 \
   XCADDY_GO_BUILD_FLAGS="-ldflags='-w -s'" \
   CGO_CFLAGS=$(php-config --includes) \
   CGO_LDFLAGS="$(php-config --ldflags) $(php-config --libs)" \
   xcaddy build \
       --output turbophp \
       --with github.com/dunglas/frankenphp/caddy
   ```

The resulting `turbophp` binary will be available in the current directory.
