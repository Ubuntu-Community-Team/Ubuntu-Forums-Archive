---
title: "Bare metal backup to Truecrypt-encrypted external hard-drive"
date: 2012-08-28
forum: General Help
---

### Post by na5h on 2012-08-28
Hi,
I wish to do a so-called "bare metal backup" of my hard-drive using Clonezilla or similar software. The only problem is that I would like the destination of the backup to be an external hard-drive which has been encrypted using Truecrypt.

Since Truecrypt isn't included in the Clonezilla LiveCD, the external hard-drive obviously can't be mounted so easily. Any suggestions on possible workarounds or other software?

---

### Post by dragonfly41 on 2012-08-28
Here is an alternative .. which I have installed recently .. 

[http://ubuntuforums.org/showthread.php?t=2047307](http://ubuntuforums.org/showthread.php?t=2047307)

I guess this approach might be adapted to use TrueCrypt

and you could place your encrypted archives in the cloud (AWS S3 buckets).

---

### Post by na5h on 2012-08-29
Thanks...but do you have any ideas on how to mount a Truecrypt volume in Clonezilla (or similar)?

I suppose I could just do the backup to a regular external hard-drive and simply move it to my Trucrypt volume, but...

---

### Post by dragonfly41 on 2012-08-30
I'm a bit preoccupied at the moment trying to recover some files on my configuration .. but this thread might help you ..

[http://sourceforge.net/projects/clonezilla/forums/forum/663168/topic/3676076](http://sourceforge.net/projects/clonezilla/forums/forum/663168/topic/3676076)

---

### Post by na5h on 2012-08-31
Yes, that seems to be exactly what I've been looking for! Thank you! :)

---

