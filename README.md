# Password Wordlists

A collection of themed wordlists for authorized password auditing, security research, and CTFs.

I build these lists for my own testing and share them here for others to use. The collection combines candidate words and phrases based on sports, New York geography, English vocabulary, and popular culture.

Use them directly as dictionaries or as starting points for rule-based candidate generation with tools such as Hashcat and John the Ripper.

## Wordlists

| File | Contents | Entries | Last Update |
| --- | --- | ---: | --- |
| [ilovesports.txt](ilovesports.txt) | Sports teams, players, cities, abbreviations, and related terms. | 651 |  |
| [ny_targeted.txt](ny_targeted.txt) | New York geographic names, including counties, towns, lakes, and rivers. | 1,107 |  | 
| [passphrases.txt](passphrases.txt) | Music references, movie quotes, popular culture, and everyday expressions. | 39,613 |  |
| [top3kenglishwords.txt](top3kenglishwords.txt) | A general English vocabulary list containing approximately 3,000 words. | 2,999 |  | 


## About the honeypot data

## Getting started

```bash
git clone https://github.com/really-gabagool/Password-Wordlists.git
cd Password-Wordlists
```

Each text file contains one candidate per line. Capitalization, spaces, punctuation, and accented characters may be significant. Preserve them unless your testing requires a specific transformation.

### Hashcat

Run a dictionary attack against hashes you are authorized to audit:

```bash
hashcat -m <hash_mode> -a 0 hashes.txt passphrases.txt
```

Apply a rule file to a themed list:

```bash
hashcat -m <hash_mode> -a 0 hashes.txt ilovesports.txt -r /path/to/rules.rule
```

Replace `<hash_mode>` with the correct mode for your hash format. Rules can expand base candidates through capitalization changes, substitutions, and appended characters. Larger rule sets increase candidate counts and processing time.

### John the Ripper

```bash
john --wordlist=passphrases.txt hashes.txt
```

With wordlist rules:

```bash
john --wordlist=ilovesports.txt --rules hashes.txt
```

Select the appropriate hash format if it is not detected correctly.

## Limitations

- These are focused lists, not exhaustive password dictionaries.
- Themed words and phrases are candidate material, not evidence of actual password use.
- Honeypot observations reflect the sensors and collection period, not all attacks.
- The English list's filename is approximate; its source and statistical ranking are not documented here.
- Some phrases contain profanity or other explicit language.

Do not use these public lists to choose passwords for your own accounts.

## Contributing

Suggestions, corrections, and additional themed lists are welcome through issues or pull requests. For new data, describe its source, how it was collected or generated, and any filtering or deduplication performed. Include attribution and applicable source terms for third-party material.

Please do not submit account identifiers, password-to-account mappings, API keys, or other private information.

## Responsible use

Use these wordlists only against systems, accounts, and hashes you own or have explicit permission to test. Stay within the agreed scope.

## License

See [LICENSE](LICENSE) for the repository's GNU General Public License, version 3.
