---
title: "add/remove broken after downgrade"
date: 2009-10-25
forum: General Help
---

### Post by clear_runway on 2009-10-25
the add/remove programs application, upon trying to reload the list of available apps, keeps giving me multiple 111 errors. why would it refuse to connect? also, it wont install anything at all, because my computer type is "i386" whatever that means.

this is particularly unusual because I just reinstalled ubuntu, after upgrading to 9.10. so now after I downgrade (actually a total partition wipe) it doesn't work despite working perfectly well before

---

### Post by razorboy5 on 2009-10-25
could u add the actual error?

i386 just means that ur using 32bit (i believe)

---

### Post by clear_runway on 2009-10-25
here they are:

upon trying to download a random program:

"W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Failed to fetch [http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://cl.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to cl.archive.ubuntu.com:80 (200.24.234.62). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead."

and below said random program:

"20.000 Light Years Into Space cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

you are correct, it is 32bit, but *every single program* apparently cant run in 32bit mode, which I know isn't right because I was running them just a few days ago.

---

### Post by clear_runway on 2009-10-25
makes no sense.

---

