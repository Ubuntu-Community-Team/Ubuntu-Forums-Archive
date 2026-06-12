---
title: "Using LiveCD to recover files from windows"
date: 2010-05-10
forum: General Help
---

### Post by professorchaos on 2010-05-10
Ever since my MS Windows stopped booting I've been using a Ubuntu 9.04 Live CD until I was able to get a flash drive to back up my files. I've been able to access my Windows files without problems until the most recent time I booted from the CD, and it doesn't seem to find any of the files from Windows anymore, as it isn't showing up under "Places" or "Computer," which it did previously. Is there anything that may be causing this that I could correct? Thanks

---

### Post by finlost on 2010-05-10
I am guessing your HDD is failing.

---

### Post by Apv507 on 2010-05-10
Yes it sounds like a hard drive failure. You may have just learned the hard way to backup everything either before things get bad or at the very first sign of it. Honestly the second it stopped booting up I would have considered myself lucky that I was able to access the files at all and would have copied them to an external hard drive asap. Sorry but unless you get lucky it looks like you are out of luck. I have had HDDs magically work after dieing, but only for a little while. Good luck.

---

### Post by x C0MMAND0 x on 2010-05-10
If it's critical data that you can't live without I would consider purchasing Spinrite ( [http://www.grc.com/intro.htm]("http://www.grc.com/intro.htm") ).  It is an excellent Live-CD program I have used many times to recover data.

---

### Post by professorchaos on 2010-05-12
Thanks x C0MMAND0 x; I tried Spinrite but it failed.

---

### Post by spydeyrch on 2010-05-12
> **professorchaos said:**
> Thanks x C0MMAND0 x; I tried Spinrite but it failed.

Does your BIOS and POST recognize the HDD as being present? No need to boot into Ubuntu or Windows, just see if your BIOS detects it in setup and if POST shows it being present.

-Spydey :guitar:

---

### Post by obaid on 2010-05-12
Ubuntu will not mount hard drives if it has dirty bit.
a hard drive gets dirty bit when it is not safely removed, like when you shutdown a computer suddenly from power button.

try to mount your laptop's H.D.D manually:

> sudo mount -t ntfs-3g -f /dev/sda* /mnt

-t tells mount partition type, and -f or -o forcefuly mounts it (not sure check man page "man mount"), the * in /dev/sda* would be the partition which you want to access and /mnt is mount directory.

---

