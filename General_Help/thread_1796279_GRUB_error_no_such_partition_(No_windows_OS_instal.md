---
title: "GRUB error: no such partition (No windows OS installed)"
date: 2011-07-03
forum: General Help
---

### Post by hydn79 on 2011-07-03
I've been serching the forum for hours and every thread related to "GRUB error: no such partition" that i've read relates to fixing the issue for users with windows OS also installed or trying to get windows to boot.

How it happened:
I edited partitions and now I get GRUB error: no such partition. I ONLY have Linux installed.

I was able to boot the OS by typing:

```
set partition=(hd0,1)/boot/grub
set root=(hd0,1)
insmod normal
normal
```Then in terminal i did a **sudo update-grub** and rebooted but it still comes up with **GRUB error: no such partition**.

At which point if i type **set **it shows:

```
prefix=(hd0,msdos1)/[COLOR=Red]mnt[/COLOR]/boot/grub
root=hd0,msdos1
```This use to just be prefix=(hd0,msdos1)/boot/grub but I tried to follow instructions on another Grub rescue thread and all it did was change prefix=(hd0,msdos1)/boot/grub to to prefix=(hd0,msdos1)/[COLOR=Red]mnt[/COLOR]/boot/grub.

It seems all i need to get it to boot automatically is to change

```
prefix=(hd0,msdos1)/mnt/boot/grub
root=hd0,msdos1

```to
```

prefix=(hd0,1)/boot/grub
root=hd0,1
```But how?

Please help me out.

---

### Post by mikejonesey on 2011-07-03
```
sudo os-prober
sudo update-grub2
```

---

### Post by hydn79 on 2011-07-03
will try thx

---

### Post by hydn79 on 2011-07-03
error: file not found.
grub rescue>

and set shows: 

prefix=(hd0,msdos1)/[COLOR=Red]mnt[/COLOR]/boot/grub root=hd0,msdos1

---

### Post by drs305 on 2011-07-03
Manually edit the entry in the Grub to get it to boot. Once you have booted into your real installation, run:
```
sudo grub-install
sudo update-grub
```
The first command should read where it is running from and create a new MBR entry and generate a new core.img file. I think that, combined with the update-grub command, which will generate a new grub.cfg, should fix it.

If you still have problems, click the "BIS" link in my signature line, run the boot info script and post the contents of the RESULTS.txt file it generates.

---

### Post by hydn79 on 2011-07-03
f it! Been on this for 6 hours now. I just copied my home folder to another drive. I'm going to just boot with USB and select erase entire disk, then just reinstall Linux.

Its so hard to find threads with users who have ONLY Linux installed. Guess I should not have wiped my win7 that came with laptop a few months back. Not! I'm so glad to be rid of windows.

Will be back up in less than 15 mins.

thx

---

### Post by hydn79 on 2011-07-03
Done! Able to boot, files restored and just installing the updates.

---

