---
title: "file(1) command in Ubuntu incompatible with standard BSD one"
date: 2009-06-30
forum: General Help
---

### Post by bsilver6 on 2009-06-30
I am trying to write a script using the file(1) command that will work across Linux (and possibly Mac OS and other Unix) platforms.
Currently, the two necessary platforms are Ubuntu > 8.10 and CentOS.

The file(1) command in Ubuntu is not compatible with the one in CentOS.
The one in Ubuntu is version 4.24 and the one in CentOS is 4.10, so I'm guessing this is the problem, but maybe the one in Ubuntu is a separate branch altogether? I can't seem to find a changelog for file because it is so old.

My question is, does anyone know of a way to make the Ubuntu file(1) 4.24 work with the CentOS file(1) 4.10.

One specific compatibility problem I've run into is that ASCII/Unicode files containing "PART ONE", "PART TWO" etc are reported to be "Par archive data" rather than "ASCII text".

I've tried the --exclude option which is present on the Ubuntu but not on the CentOS version. "--exclude token" doesn't work at all and "--exclude soft" makes the output too soft, i.e. as far as I can tell just about everything outputs "ASCII text", including known binary data.

My main requirement is to be able to detect binary data from text data, and to be able to distinguish between charsets, or at least Unicode / multibyte charsets from ASCII.

---

