---
title: "Restore full hd image(dd):  filesystem check filed"
date: 2010-12-08
forum: General Help
---

### Post by john99 on 2010-12-08
Hello,


I cloned my entire harddisk (booted from CD-ROM, volume not mounted ) with the following command:


# dd if=/dev/hda  | bzip2 -c > /media/disk-2/hda-image.bz2


and restored it with the image with


# cat  /media/disk-2/hda-image.bz2 ¦ bzip2 -d ¦ dd of=/dev/hda


After rebooting the system , the system says "Filesystem Check failed" and suggest to enter the root password for maintenance :-(

Since I am not at all experienced with Linux I didn't know what is advisable in such a situation.



Question:
What am I doing wrong? Or is such a filesystem check often required after a full hd restore?


Any feedback is apprecaited very much! Thank you!

John

---

### Post by SlugSlug on 2010-12-08
not normally the way I do dd backups but if your getting to the recovery mode thats half a good sign.

once there enter your root password and then
```

fsck /dev/hda
```

(providing hda is the correct drive that gets mentioned in the output on screen)

---

### Post by john99 on 2010-12-08
Thank's a lot SlugSlug for the help! I am going to try your suggestion :-) 

By the way:
What approach would you suggest if really the whole harddisk should be imaged/cloned?


Cheers!

John

---

### Post by SlugSlug on 2010-12-08
> **john99 said:**
> Thank's a lot SlugSlug for the help! I am going to try your suggestion :-) 

By the way:
What approach would you suggest if really the whole harddisk should be imaged/cloned?


Cheers!

John

similar to what you do, I use it to clone FTP sever installs, I just dnt use gunzip
First I dd to external drive

dd if=/dev/sda of=/dev/sdb

then from a live boot
dd if=/dev/sdb of=/dev/sda

reboot and all is good

dd takes over night tho!

We did look into remastersys but could never get it to work, other ppl on here say clonezilla is good -- i've never got round to trying it

---

