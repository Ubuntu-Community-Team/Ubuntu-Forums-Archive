---
title: "Live CD: mount HD partitions &amp; grub restore problems"
date: 2006-06-19
forum: General Help
---

### Post by mvaniersel on 2006-06-19
Hey

I've got a dual-boot machine with Dapper and WinXP Pro on it. I needed to reinstall WindowsXP, and, as a consequence I lost the Grub boot menu.

I've then tried to get it back with the Dapper Live CD, and I ran into 2 problems:

1) I can't seem to mount my harddrive partitions. E.g. if I go to places->My computer and click on any partition, I get a popup with this error:

```

error: device /dev/sda2 is not removable

error: could not execute pmount"

```

Is there a trick to this? Could it be related to me having a SATA harddrive?

2) I'm trying the following procedure to restore grub:

> 
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

However, I don't know which partition number to type in step 4. But anyway I always get the following error:

```

grub> root (hd0,2)

Error 21: Selected disk does not exist

```

---

### Post by aysiu on 2006-06-19
I'm not sure how /dev/sda2 translates, but isn't (hd0,2) /dev/hda3?

---

### Post by mvaniersel on 2006-06-19
Maybe, but that doesn't matter, because I don't know which partition I need in the first place. Isn't there some autodetect command?

---

### Post by aysiu on 2006-06-19
Well this command will tell you what partitions you have (mounted or unmounted): ```
sudo fdisk -l
```

---

### Post by mvaniersel on 2006-06-20
Thanks, but I still run into problems.

using fdisk -l, and then subsequently mounting all the linux partitions I get, I've determined that the correct partition (the one containing /) is /dev/sda2

Are you required to mount partitions in order for grub to find them? Anyway, after that I did

```

grub
root (hd0,1)
setup (hd0)

```

This appeared to work fine, I didn't get any errors.

But then, after rebooting I don't get a grub menu as expected. I can't even boot windows anymore. Instead I get "please select boot device" or something like that.

Please help!

---

### Post by mvaniersel on 2006-06-21
Finally, I solved with the help of somebody on #ubuntu. Just for the sake of completeness:

I used 
```

grub-install --root-directory=/dev/sda2 /dev/sda

```

This got me the boot menu back. But still there was something wrong as I could only boot into windows, not linux. 
Turns out that by reinstalling windows XP, the order of the partitions got messed up. So what was /dev/sda3 before, was now /dev/sda2. 

So then I needed to edit /etc/fstab and /boot/grub/menu.list, and correct all occurences of /dev/sda? and (hd0,?).

Thanks windows XP! For being so cooperative with other operating systems :p

---

