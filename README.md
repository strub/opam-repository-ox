# OPAM repository for OxCaml

This repository is a package repository for the [opam package manager](https://opam.ocaml.org). It contains [OxCaml](https://github.com/oxcaml/oxcaml), together with Jane Street libraries and necessary patches to other packages.

## Installation

Start by creating a new switch including our repository in OPAM:

```sh
# Update to make sure you get the latest version of all packages
opam update --all
# This may take some time to install
opam switch create 5.2.0+ox --repos ox=git+https://github.com/oxcaml/opam-repository.git,default
eval $(opam env --switch 5.2.0+ox)
```

If the installation was successful, you can now use OxCaml!

OxCaml supports developer tooling such as `ocamlformat` or `merlin`:

```sh
opam install ocamlformat merlin ocaml-lsp-server utop
```

Jane Street libraries such as Base and Core support many OxCaml features. Install them with `opam install`, and read their documentation and interface files to learn more. For a general introduction to OCaml and our libraries, refer to [Real World OCaml](https://dev.realworldocaml.org/index.html).

## Known issues

### Platforms other than x86_64 or ARM64

OxCaml does not yet support architectures other than x86_64 or ARM64.

### Windows

OxCaml does not yet support Windows. Windows users are recommended to use WSL 2.

## Autoconf

Installing OxCaml requires [autoconf](https://www.gnu.org/software/autoconf/).
Normally, OPAM will prompt you to install autoconf through your system package manager if needed,
but if that doesn't work, you might have to install it manually.

## Beta extensions

Some Jane Street extensions, like `comprehensions`, are unstable and thus hidden behind the `-extension-universe` compiler flag.
You can use the `flags` field in `dune` files to enable them:

```ocaml
(library
 (name your_lib)
 (flags (:standard -extension-universe beta)))
```

## SIMD support on ARM

The SIMD compiler extension is not yet supported on ARM architectures.
