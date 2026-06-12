---
title: "Help.  My computer lost power during 9.10 upgrade"
date: 2009-11-04
forum: General Help
---

### Post by yippieayae on 2009-11-04
Greetings all.  I have a bit of a problem.   I was downloading v 9.10 and in the middle of the installiation, my computer shut itself down.  (Toshiba Satellite with a sketchy primary cooling fan.)  Does anyone know how I can re-load the o.s. with only access to the bios settings.  If the complete os tries to load up tons of error messages are displayed.  I guess that power interrupt couldn't have come at a worse time.  Any help would be greatly appreciated.  
Carlos

---

### Post by nikgare on 2009-11-04
You need to reformat and reinstall from scratch.

---

### Post by P4man on 2009-11-04
You say upgrade.. if its an upgrade you may be able to fix it. Can you boot into a recovery console and select a root shell? If not, do you have a liveCD ?

From a root shell, run:

```
dpkg --configure -a
```
If you can only boot a live cd, you have to do the same but after chrooting into your broken install:

```
 sudo su
```

now mount your ubuntu install

```
mount /dev/sda[COLOR="Red"]x[/COLOR] /mnt
```

replace x with your root partition number

```
mount -o bind /dev /mnt/dev
mount -o bind /proc /mnt/proc
 chroot /mnt
```

then try the above command

---

### Post by undecim on 2009-11-04
It's probably best to backup your home directory and do a fresh install. I would have recommended a fresh install anyways, since Karmic brings the much faster ext4 filesystem.

---

### Post by yippieayae on 2010-04-09
Thanks to everybody for all of the help.  The problem is fixed.  I tried several times during the initial sequence of the computer start up freezing the automated sequence and selecting the boot from cd option.  It eventually took and began reading from the v9.10 live disk.  Initially, on the first startup from the cd-rom, I got an error message saying that the kernel had been corrupted.  So, I ran the entire re-install procedure and she's right as rain!!  The moral of the story is don't let your computer lose power during a kernel re-write!  Again, thanks to everybody for your support.  I am looking forward to learning a thing or two about Linux!

---

