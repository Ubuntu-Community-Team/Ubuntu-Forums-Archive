---
title: "long package descriptions in aptitude"
date: 2010-11-16
forum: General Help
---

### Post by anontrol on 2010-11-16
I was wondering if anyone knew how to get long package descriptions which searching for packages with aptitude.

my search results have package descriptions that are truncated even if the terminal is expanded to allow longer one-line package descriptions.

Thanks in advance...

---

### Post by lykeion on 2010-11-16
Maybe you can pipe it through the *tr* command to replace newlines with spaces. 
In this example I get output using the apt-cache show command for the package seahorse, but the principle is the same for whatever command you use to get output:
```
apt-cache show seahorse | tr '\n' ' '
```
EDIT:
Actually there are multitude of commands you can use to replace newlines with spaces, see [here]("http://linux.dsplabs.com.au/rmnl-remove-new-line-characters-tr-awk-perl-sed-c-cpp-bash-python-xargs-ghc-ghci-haskell-sam-ssam-p65/")

---

