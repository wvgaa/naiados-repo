# naiados-repo

The pacman repository of [NaiadOS](https://github.com/wvgaa/NaiadOS). The packages are in the [x86_64 release](https://github.com/wvgaa/naiados-repo/releases/tag/x86_64), this repository holds the kernel build files (PKGBUILD, config, hooks).

NaiadOS installs set this up already. To add it by hand, put this at the end of `/etc/pacman.conf`:

```
[naiados-repo]
SigLevel = Required DatabaseOptional
Server = https://github.com/wvgaa/naiados-repo/releases/download/x86_64
```

All packages are signed. Trust the signing key first (`naiados.gpg` in this repository), then install `naiados-keyring` so later key changes arrive as updates:

```
curl -LO https://raw.githubusercontent.com/wvgaa/naiados-repo/main/naiados.gpg
sudo pacman-key --add naiados.gpg
sudo pacman-key --lsign-key D1D54F405F3F8A4FD67A6BC8D7900ED576F6C787
sudo pacman -Sy naiados-keyring
```

Signing key: `NaiadOS Package Signing`, fingerprint `D1D5 4F40 5F3F 8A4F D67A 6BC8 D790 0ED5 76F6 C787`.

## Packages

- `linux-naiados`: NaiadOS kernel, latest stable series
- `linux-naiados-lts`: NaiadOS kernel, LTS series
- `naiadcheck`: system health check
- `naiados-keyring`: the signing key
