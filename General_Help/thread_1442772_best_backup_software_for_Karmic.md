---
title: "best backup software for Karmic"
date: 2010-03-30
forum: General Help
---

### Post by Rubi1200 on 2010-03-30
Could anyone please suggest some possible backup programs for Ubuntu? I am looking for something that is relatively easy to setup and use, but powerful too. I intend on backing up to an external hard-drive if that helps.
Thanks in advance.

---

### Post by Nisal on 2010-03-30
y dont u use ubuntu one ?

---

### Post by colorlessprism on 2010-03-30
remastersys will take you current install and turn it into a LiveCD. i then use usb startup disc creator to put my remastersys backup on flash drive. then if i need to restore, i just "install" from usb and im back up and running in no time. since it is an "iso" format you will be limited to the size it can back up. i use tar.gz to backup my Documents, Music, Pictures, Video, and .wine

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by cjhabs on 2010-03-30
> **Rubi1200 said:**
> Could anyone please suggest some possible backup programs for Ubuntu? I am looking for something that is relatively easy to setup and use, but powerful too. I intend on backing up to an external hard-drive if that helps.
Thanks in advance.

You'll probably get a lot of different answers to this one.
I use the "dump" command (and the corresponding "restore")for my system partition - it is in the repos. It says it is for ext2, but it handles my ext4 just fine. It is command line, I have it in a script and it can be scheduled.

I use rsync for my data - there is a gui front end for it - grsync I believe.

---

### Post by jmszr on 2010-03-30
Rubi1200,

Back-in-time might be of interest to you: [http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html](http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html)

---

### Post by Rubi1200 on 2010-03-30
Thanks all! jmszr, I like the look of Back-in-Time and will check it out some more.
Again, thanks for all the suggestions
:)

---

### Post by kiwinsn on 2010-04-03
I have been looking as well, and came across deja-dup a couple of days ago.

Works a treat, and will detect if your external drive is mounted or not, before proceeding.

I back up to an internal drive, and then just copy/paste to an external once a week.

Cheers

---

### Post by garvinrick4 on 2010-04-03
clonezilla makes an image of your whole drive or an image of a partition. I really like
the idea of image available to restore just as you had it.
 Make a CD of it and boot off of it so all partitions are not mounted and do as you will.
It is sweet.

---

### Post by durand on 2010-04-03
> **jmszr said:**
> Rubi1200,

Back-in-time might be of interest to you: [http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html](http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html)

This is great! I've been looking for a replacement for TimeVault for a few years, and this is exactly it. Thanks!

---

