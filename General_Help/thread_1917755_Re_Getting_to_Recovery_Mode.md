---
title: "Re: Getting to Recovery Mode"
date: 2012-01-30
forum: General Help
---

### Post by Aldentron on 2012-01-30
I have this problem but my keyboard is not wireless. My monitor gives me an "Out of Range" error and I am trying to get to recovery mode to fix it. Holding down shift during boot-up gives me Out of Range. Holding down CTRL during boot-up gives me Out of Range. Holding Space during boot-up gives me Out of Range. All of the solutions for "Out of Range" problems require recovery mode and I can't even get to it. This is really irking me, because I'm pretty sure I know exactly what the problem is and can't fix it.

---

### Post by lisati on 2012-01-30
Moved to own thread.

---

### Post by drs305 on 2012-01-30
The 'out of range' message doesn't refer to wireless. It can be produced by a variety of issues.

One thing to try if you can boot a LiveCD is to alter grub.cfg to simplify video issues. Substitute the correct values for your Ubuntu drive/partition (sda5, sdb1, etc) for XY:

```
sudo mount /dev/sdXY /mnt
gksu gedit /mnt/boot/grub/grub.cfg

```

Edit two lines and add the third, changing the values to match if they are different than what I posted. Save the file and reboot. Don't run update-grub. (There is a bit of redundancy in the changes, but it servers its purpose.)

> insmod part_msdos
if loadfont /usr/share/grub/unicode.pf2 ; then
[COLOR="DarkRed"]  set gfxmode=640x480[/COLOR]
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos11)'
  search --no-floppy --fs-uuid --set=root 5d6017f0-4140-4901-afb9-2537097cceae
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
[COLOR="DarkRed"]terminal_input console[/COLOR]
terminal_output [COLOR="DarkRed"]console[/COLOR]



After booting your normal instllation, make the changes permanent by editing /etc/default/grub and then running update-grub if you aren't able to figure out what the underlying problem is.

---

### Post by Aldentron on 2012-01-30
The original post was from another thread where the problem was the user's wireless keyboard. I believe my problem is that the screen resolution currently set is incompatible with the start-up screens.

Is there a solution without using a disc? I let my friend borrow mine :/

---

### Post by drs305 on 2012-01-30
> **Aldentron said:**
> The original post was from another thread where the problem was the user's wireless keyboard. I believe my problem is that the screen resolution currently set is incompatible with the start-up screens.

Is there a solution without using a disc? I let my friend borrow mine :/

Yes, the problem is often a monitor resolution issue, which is what the changes I proposed try to circumvent.

Do you have access to any linux recovery CD's or USB's. Anything that can boot to a linux command prompt would do, since at that point you could mount your Ubuntu partition and make the changes.

The only other option I can think of at the moment would be if you had an OS on another drive with a separate bootloader. You could change the boot order in BIOS to the other drive, thus bypassing the MBR instructions on your current drive. Or if you have an external monitor hooked up to a laptop, perhaps unplugging it to enable the laptop screen. ... Yeah I'm grasping at straws...

---

### Post by Aldentron on 2012-01-30
> **drs305 said:**
> One thing to try if you can boot a LiveCD is to alter grub.cfg to simplify video issues. Substitute the correct values for your Ubuntu drive/partition (sda5, sdb1, etc) for XY:

```
sudo mount /dev/sdXY /mnt
gksu gedit /mnt/boot/grub/grub.cfg

```


I got my hands on a USB with 10.10 on it. How do I find out what the correct partition is from the desktop? Do I enter this code into Terminal? Bear with me, I'm new...

---

### Post by drs305 on 2012-01-30
If you run the command "sudo fdisk -l" (lowercase L) it will show your partitions. The output will most likely display two linux partitions  - your Ubuntu partition (Linux) and a swap partition (Linux swap / Solaris). It is the Ubuntu partition  you would want to mount.

The first is the Ubuntu partition, the second is the swap partition.

> /dev/sda5       167108256   177759224     5325484+  83  Linux
/dev/sda6       177759288   186032699     4136706   82  Linux swap / Solaris

---

