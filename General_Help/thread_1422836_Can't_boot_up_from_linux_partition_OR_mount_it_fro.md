---
title: "Can't boot up from linux partition OR mount it from other partitions"
date: 2010-03-05
forum: General Help
---

### Post by antman8969 on 2010-03-05
> Boot from (hd0,0) ext3 5108701a-641d-43b182eb-aeb6da348d62
Starting up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough ?)
- Check root = (did the system wait for the right device ?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/5108701a-641d-43b182eb-aeb6da348d62 does not
exist . Dropping to a shell!


Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


That is the message I get when I tried to boot into my 64bit Ubuntu 9.1 partition with grub2. I've been reading about the problem and it seems that most people experience it after a new installation of kernel update, but mine seems to have come out of nowhere. I updated the kernel a few days ago, but the machine has been on and off multiple times since then, so I don't see how that can be the problem. 

I've been trouble shooting from a 32 bit ubuntu partition on the same laptop (what I'm typing on now). I reinstalled grub from my 32 bit partition, but all that did was remove my 64bit partition from the boot table when starting up... not that it mattered much, I couldn't even boot into it in safe mode.

I'm pretty sure that I got that error message because linux could not mount the partition (/dev/sda7) to read from. 




it's odd because I can still see that the partition exists. In gparted it still sees it as an ext4, under sda7. But in 'Disk Utility' it comes up as 'Unknown or Unused'.

I don't even really care about trying to make it bootable again, all I want to do is mount it ONCE so I can take my files from it and put them on another partition. ANY help is greatly appreciated!!!


EDIT: maybe this goes without saying, but I can't seem to find a UUID for the partition either

---

### Post by antman8969 on 2010-03-05
ok so I was able to mount the partition, and I'm currently copy/ pasting all of my files onto my 32 bit partition. But this implies to me that there really isn't a disk error or anything, and it can be fixed.

if I have to at this point I can just copy all of my files out, delete the partition and reinstall, but thats kind of lame. If no one ends up getting back to me and I dont find anything then I guess thats what ill end up doing :(

---

### Post by byStanderone on 2010-03-05
...do i get it right, uuid of your sda7 is not listed in /etc/fstab ?

---

### Post by antman8969 on 2010-03-05
> **byStanderone said:**
> ...do i get it right, uuid of your sda7 is not listed in /etc/fstab ?

yep, and when I try to get a list of UUIDs my sda7 isn't on that list. BUT I can get a direct path...

---

### Post by antman8969 on 2010-03-05
> **antman8969 said:**
> yep, and when I try to get a list of UUIDs my sda7 isn't on that list. BUT I can get a direct path...

ok very odd. All I did was mount that partition through the terminal like so

```
sudo mount -t ext4 /dev/sda7 /mount
```

and restart, and all of a sudden my computer recognizes it again. But sadly I removed it from the  grub boot list so I could still use some help trying to get it back on...

---

### Post by akand074 on 2010-03-05
Its a little more complicated using Grub2 I use to just edit the menu.lst file, I find the grub.cfg file more confusing but you can learn all about Grub 2 here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Just add your 64bit Ubuntu entry

---

### Post by antman8969 on 2010-03-05
> **akand074 said:**
> Its a little more complicated using Grub2 I use to just edit the menu.lst file, I find the grub.cfg file more confusing but you can learn all about Grub 2 here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Just add your 64bit Ubuntu entry

thanks a lot :)

---

### Post by byStanderone on 2010-03-06
...ok, try a sudo update-grub, and see if things correct itself, if not you'll have to edit your fstab file, and enter the right uuid for that drive.

---

