---
title: "encrypting a directory"
date: 2011-06-29
forum: General Help
---

### Post by fantastic on 2011-06-29
I am currently running an LTS version and would like to encrypt a directory.

How do I go about doing it, and what is the best way to back that folder up on an external drive?

---

### Post by haqking on 2011-06-29
> **fantastic said:**
> I am currently running an LTS version and would like to encrypt a directory.

How do I go about doing it, and what is the best way to back that folder up on an external drive?

using seahorse

gksudo seahorse

or from system preferences choose passwords and encryption keys.

from terminal install seahorse plugins

 sudo apt-get install seahorse-plugins

then either log out and log back in or from terminal

killall nautilus && nautilus &

then you using seahorse create a PGP key (using a strong passphrase not a password) remember it or you are screwed ;-)

then right click on folder or file and you wil see encrypt option

and here is a link to use GUI, it mentions decrypt file, which i covered with seahorse plugins

[http://www.liberiangeek.net/2010/10/create-encrypted-files-folders-ubuntu-10-0410-10-maverick-meerkat-seahorse/](http://www.liberiangeek.net/2010/10/create-encrypted-files-folders-ubuntu-10-0410-10-maverick-meerkat-seahorse/)

enjoy

---

### Post by jim_deadlock on 2011-06-29
I've found truecrypt to be fantastic, you end up with a single encrypted file which you can move/copy anywhere you like and you just mount it as a drive and use it like you would a usb disk. There are versions for linux, win and mac so you can mount the drive just about on any computer, it's great and very easy to use too:

[http://www.truecrypt.org]("http://www.truecrypt.org")

---

