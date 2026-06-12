---
title: "unable to decrypt encfs folder after renaming volume"
date: 2011-02-22
forum: General Help
---

### Post by karmic-koala on 2011-02-22
I have a 2TB USB verbatim hard drive.

This hard drive had a folder called /office which was encrypted using encfs.

The external drive had no volume name before and appeared in /media/ as a long number (something like 576856349837649837).

I added a volume and called it verbatim (using GParted). Now the volume appears as /media/verbatim which is easier to type and remember.

But since renaming I am unable to decrypt my encrypted folder /office.

Any ideas how to recover my files?

---

### Post by pi3832 on 2012-02-21
You don't really "encrypt a folder" with EncFS.  You mount the folder as a virtual partition in user space (using FUSE) and you encrypt/decrypt the files on that partition as FUSE accesses them.

Point being, something, somewhere is "mounting" your encrypted partition.  Whatever does that doesn't know about the new location.

Are you using [CryptKeeper](http://tom.noflag.org.uk/cryptkeeper.html)?

Maybe the "Import EncFS folder" function is what you want?

---

