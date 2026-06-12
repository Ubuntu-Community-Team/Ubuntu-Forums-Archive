---
title: "how do I compress and encrypt files/folders?"
date: 2010-10-30
forum: General Help
---

### Post by Ascenti0n on 2010-10-30
I currently have a bash script that runs and backs up my daily files onto a separate partition using Rsync, but I thought it would be good to use the Ubuntu-one service as an ADDITIONAL backup for really important files. 

How do I compress then encrypt those files, and can I add any commands that will do this to my existing bash script?

I am running Ubuntu 10.04

---

### Post by peculiar penguin on 2010-10-30
Either use an archive format with built-in encryption (7-Zip, GPG-/PGP-ZIP,...), or create a normal .tar.gz/.tar.bz2 archive and then encrypt that file with something else (GnuPG, bcrypt, OpenSSL,...).

Maverick comes with GnuPG preinstalled (dunno about Lucid) and includes [gpg-zip]("http://www.gnupg.org/documentation/manuals/gnupg/gpg_002dzip.html") ("an gpg-ized tar using the same format as used by PGP's PGP Zip"). You'd probably want the --symmetric option unless you've already wrapped your head around public key encryption.

All of these work on the command line so scripting them isn't hard.

---

