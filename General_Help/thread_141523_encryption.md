---
title: "encryption?"
date: 2006-03-08
forum: General Help
---

### Post by issueperson on 2006-03-08
So encryption sounds kinda fun to me.  My question is (i have no background doing anything with this) what encryption software could be run from a windows box that would allow decryption in Linux?  PGP is just a windows application, correct?

I'm looking for something as powerful as that.

one thought i had was having a "comments" section on a webpage, and when you submit it, having it automatically encrypted with a public key before submission.  in that case, i would want something that could potentially be run online as well.

any of this sounding reasonable?

any ideas?

---

### Post by Heliix on 2006-03-08
hi,
GPG is what you are looking for
visit the web page for more details but afaik it is very close to PGP (pretty good privacy ;-))
installation is a piece of cake:
apt-get install gnupg
it's small, smart and easy to use. enjoy it!

---

### Post by issueperson on 2006-03-08
is it a completely secure program?  or is there any known way yet to break the code?  i'm just wanting to know how strong an encryption it is.

---

### Post by engla on 2006-03-08
[QUOTE=issueperson]is it a completely secure program?  or is there any known way yet to break the code?  i'm just wanting to know how strong an encryption it is.[/QUOTE]
I can't tell off hand, but you can ask gpg which ciphers it can use, and look up them in Wikipedia. Wikipedia have lots of great articles on cryptography, so if you're just a little bit interested, it could cost you all evening to read about this.. 

Links below:
> $ gpg --version
gpg (GnuPG) 1.4.1
Copyright (C) 2005 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.

Home: ~/.gnupg
Supported algorithms:
Pubkey: [RSA,]("http://en.wikipedia.org/wiki/RSA") RSA-E, RSA-S, ELG-E, [DSA]("http://en.wikipedia.org/wiki/Digital_Signature_Algorithm")
Cipher: [3DES,]("http://en.wikipedia.org/wiki/3DES") [CAST5,]("http://en.wikipedia.org/wiki/CAST5") [BLOWFISH,]("http://en.wikipedia.org/wiki/Blowfish_%28cipher%29") [AES,]("http://en.wikipedia.org/wiki/Advanced_Encryption_Standard") AES192, AES256, [TWOFISH]("http://en.wikipedia.org/wiki/Twofish")
Hash: MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512
Compression: Uncompressed, ZIP, ZLIB, BZIP2

Basically many of these are modern, very secure ciphers. Some are NSA-approved, some are a bit obsolete. You have to use "big enough" key size with all of them.

---

### Post by issueperson on 2006-03-08
i have seahorse running... but it's kinda confusing the daylights out of me.  i've never used PGP or any other encryption software.  Anyone know of any newbie-esque tutorials on this?

---

### Post by skymt on 2006-03-08
[QUOTE=issueperson]i have seahorse running... but it's kinda confusing the daylights out of me.  i've never used PGP or any other encryption software.  Anyone know of any newbie-esque tutorials on this?[/QUOTE]
Well, sort of. GnuPG has a lot of documentation [here](http://www.gnupg.org/(en)/documentation/index.html), including a step-by-step [handbook](http://www.gnupg.org/gph/en/manual.html) that explains a lot of the concepts. As for Seahorse specifically, there's not so much. The manual that comes with it is somewhat... lacking. It explains how to do everything, but not what you're doing. For that see the GPG handbook.

---

### Post by issueperson on 2006-03-08
gracias.  i think i like the command line better anyways.  it seems more educational for the time being.  ditching seahorse.

*hey look ma... i just encrypted my first file*

---

