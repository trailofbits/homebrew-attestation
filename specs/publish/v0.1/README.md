# Homebrew publish attestation (v0.1)

The Homebrew publish attestation conforms to the [in-toto attestation spec (v1.0)].

[in-toto attestation spec (v1.0)]: https://github.com/in-toto/attestation/tree/v1.0/spec/v1.0

## Statement

```json
{
  "_type": "https://in-toto.io/Statement/v1",
  "subject": [{
    "name": "pkg:brew/homebrew/homebrew-core/formula-foo@1.4.3",
    "digest": { "sha256": "01ba4719c8..." }
  }],
  "predicateType": "https://github.com/Homebrew/attestation/tree/v0.1/specs/publish/v0.1",
  "predicate": {
    "bottle-name": "formula-foo--1.4.3.sometag.bottle.tar.gz",
    "bottle-digest": { "sha256": "64eeece96..." }
  }
}
```

* `subject[0].name`: A `brew` [package url (purl)]
* `subject[0].digest`: SHA256 digest of the formula source ([`Formula#ruby_source_checksum`])
* `predicate.bottle-name`: The bottle name ([`Bottle::Filename`])
* `predicate.bottle-digest`: The SHA256 digest of the bottle

[package url (purl)]: https://github.com/package-url/purl-spec

[`Formula#ruby_source_checksum`]: https://github.com/Homebrew/brew/blob/3480dda0c7297bc161b7726d026395efec0815bd/Library/Homebrew/formula.rb#L2193-L2197

[`Bottle::Filename`]: https://rubydoc.brew.sh/Bottle/Filename.html
