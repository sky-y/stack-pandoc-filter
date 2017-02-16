# A Custom Template for Pandoc Filter

This is a custom filter with Haskell Stack for writing a custom [Pandoc](http://pandoc.org/) filter.

## Usage

```
$ stack new my-filter https://raw.githubusercontent.com/sky-y/stack-pandoc-filter/master/pandoc-filter.hsfiles
$ cd my-filter
$ stack setup
(Write your custom filter in src/Main.hs)
$ stack build
(It might take a couple of minutes...)
```

Check your filter as:

```
$ pandoc input.md -t json | stack exec my-filter | pandoc -f json -o output.md
```

Finally, copy it to `~/.local/bin` (set it in PATH in your shell):

```
$ stack install
```

Now you can use it as:

```
$ pandoc input.md -t json --filter my-filter -o output.md
```

# Trouble Shooting

When build fails, versions of `pandoc` and `pandoc-types`
might not match with Stack resolver (that specify GHC version).

If you installed the lastest version of Pandoc (as client binary):

- Check pandoc version: `$ pandoc --version`
    - Check versions of `pandoc` itself and `pandoc-types`
- Fix my-filter.cabal as the checked versions above are satisfied
- Fix resolver's version to be the newest

## See also

- How to write your Pandoc filter:
    - [Pandoc - Scripting with pandoc](http://pandoc.org/scripting.html)
- How to build it with Stack:
    - [Home - The Haskell Tool Stack](https://docs.haskellstack.org/en/stable/README/)
- How to custom this Stack template:
    - [commercialhaskell/stack-templates: Project templates for stack new](https://github.com/commercialhaskell/stack-templates)

## License
BSD3
