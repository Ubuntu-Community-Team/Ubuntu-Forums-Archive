---
title: "chroot then &quot;update-grub&quot; gives errors"
date: 2010-06-24
forum: General Help
---

### Post by s3a on 2010-06-24
Ok so I have a USB external hard drive with Ubuntu 10.04 LTS on it but I did something to ruin it's grub or something.

_So what I did to make my USB HDD bootable again is_:

```
sudo mkdir -p /mnt/chroot
sudo mount /dev/sdc1 /mnt/chroot
sudo mkdir -p /mnt/dev
sudo mount --bind /dev /mnt/dev
sudo mkdir -p /mnt/proc
sudo mount --bind /proc /mnt/proc
sudo mkdir -p /mnt/sys
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt/chroot
```

_After that I did:_
```
root@ubuntu:/# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
root@ubuntu:/# 
```

I don't know what to do about that error. It took me a while to understand how to learn chroot and thanks to some youtube videos I finally learned how and then it felt like a climax when I was about to issue the **update-grub** command and then when it didn't work, I felt bad lol :(.

So if someone could help me, it would be GREATLY appreciated!
Thanks in advance!

---

### Post by mr clark25 on 2010-06-24
that seems strange...

i like to chroot a little differently:
[http://mrclark.ath.cx/linux/linux/howchroot.html](http://mrclark.ath.cx/linux/linux/howchroot.html)

---

### Post by wilee-nilee on 2010-06-24
It is easier to just reinstall grub2 with the two commands from this link. You don't have to chroot.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you really want to fix this, post the bootscript in my sig with the external plugged in. Post it in code tags.

---

### Post by s3a on 2010-06-25
Ok first of all, thanks for both your responses. I tried the other chroot method and it gave me problems (it didn't even let me get into the chroot). But nobody knows what I'm doing wrong with my method? As for the grub installing, I'll keep that in mind too but I actually want to learn how to do this the chroot way because this is not the only thing that I need to chroot for but at the moment, I'd just like it if someone could tell me why I'm getting that error with my method and tell me how to solve it without making me attempt completely different solutions.

---

### Post by WorMzy on 2010-06-25
The problem with what you've listed above is that you're not mounting /dev and /proc inside the mounted filesystem, you're mounting the file system in one folder, proc in a completely unrelated folder, and /dev in another unrelated folder. You should mount /proc in /mnt/**chroot/**proc, and /dev in /mnt/**chroot/**dev

Oh, and /sys too, if you want. I've never bothered with it though, and I've never had any problems.

---

### Post by s3a on 2010-06-26
_WorMzy:_ I tried what you said in Ubuntu 10.04 and then just in case it was a bug, I also tried it in Ubuntu 9.04. Sadly, your suggestion is not working. Am I doing something wrong?

_Here is what I get:_
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mkdir -p /mnt/chroot
root@ubuntu:~# mkdir -p /mnt/chroot/dev
root@ubuntu:~# mkdir -p /mnt/chroot/sys
root@ubuntu:~# mkdir -p /mnt/chroot/proc
root@ubuntu:~# mount -o bind /dev /mnt/chroot/dev
root@ubuntu:~# mount -o bind /sys /mnt/chroot/sys
root@ubuntu:~# mount -o bind /proc /mnt/chroot/proc
root@ubuntu:~# mount /dev/sda1 /mnt/chroot
root@ubuntu:~# chroot /mnt/chroot
root@ubuntu:/# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

_Edit:_ I think I'm doing something wrong because it seems that the system does not control the chrooted operating system. I tested this by doing uname -r which gave me the kernel of Ubuntu 9.04 which is the live CD I'm running right now instead of that of the chrooted Ubuntu 10.04 system.

_Edit 2:_ Actually, I tried installing pidgin through the chroot and it worked like normal. Something does seem off though.

---

### Post by WorMzy on 2010-06-26
You had the order right the first time: Mount sdc1, then proc, dev and sys. Now what you're doing is mounting proc, dev and sys, then immediately mounting over them with sdc1. You don't need to make the directories for proc, dev and sys either, they'll exist once you mount sdc1.

So the following will work:
```

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mkdir /mnt/chroot
root@ubuntu:~# mount /dev/sda1 /mnt/chroot
root@ubuntu:~# mount -o bind /dev /mnt/chroot/dev
root@ubuntu:~# mount -o bind /sys /mnt/chroot/sys
root@ubuntu:~# mount -o bind /proc /mnt/chroot/proc
root@ubuntu:~# chroot /mnt/chroot
root@ubuntu:/# update-grub

```

---

### Post by drs305 on 2010-06-26
Here is a "one-liner" to chroot for sdc1:
```

sudo mount /dev/sd**c1** /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys  && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

```
After running the command you will be in the chroot environment and any commands run will affect your real installation on sdc1.

---

### Post by s3a on 2010-06-26
_drs305:_ It worked flawlessly! I have a few questions though.

Firstly, to mount things, I thought I had to first create the directories with "mkdir" but it seems that I don't need to; does mounting auto-create the directories required?

Secondly, what's the point of /etc/resolv.conf? I noticed that, like previously mentionned, the /dev /proc and /sys need to be within the chroot mount point but I also noticed the /etc/resolv.conf and I'm trying to make sense of it.

Lastly, is there an important difference between mount -o bind and mount --bind. What if I did just mount by completely ignoring the "bind" part, would that make the command not work?

Sorry for the additional questions but I would just like to understand this instead of just memorize it.

Thanks!

---

### Post by WorMzy on 2010-06-26
-o bind and --bind do the same thing: bind an already existing folder to another location. A normal mount (mount -t) mounts a partition, not a folder, which is why you can't use it instead of --bind (or -o bind).

When you mount a partition with Linux installed on it, all the files and folders on that partition get mounted too, which is why you don't need to create /dev /proc or /sys -- they already exist on the partition.

---

### Post by s3a on 2010-06-26
That would be a good explanation :) except I'm just curious about one more thing: Are the /dev (and other locations) that I am "mount --bind"-ing mounting the /dev (and other locations) of the live CD's (for example) /dev (and other locations) to that of the chroot?

Assuming I am right about this, is this what gives control to the chroot so that it can do things like "update-grub"?

---

### Post by WorMzy on 2010-06-26
Sort of. The contents of these folders are generated at boot time, they're not stored on a hard disk or the Live CD. For example /dev contains a list of the hard drives and partitions that your PC has connected to it (either internally or externally), when Ubuntu boots, it essentially creates a list of these disks and partitions and stores in in /dev. When you mount a Linux filesystem in /mnt or wherever, it will have a blank /dev folder, because it hasn't been booted; so you mount --bind your current /dev to it's /dev so that when you chroot into it, you'll be able to see the list of hard drives and partitions.

This is a very simplified way of explaining what it does, but I think you'll see what I mean. The same thing happens for other devices, and running processes (/proc) and system variables (/sys). resolv.conf doesn't really need to be copied over, unless you're using a dynamic IP address and need to use the internet (for whatever reason) on the chrooted filesystem.

---

### Post by s3a on 2010-06-27
That was another great explanation! Are you a teacher? ;) And sorry for being so inquisitive, but what are "system variables"?

---

### Post by WorMzy on 2010-06-27
Nah, not a teacher, although I do like explaining things like this, because it helps me learn it myself.

I was wrong about /sys (I did say earlier that I've never bothered with it, that's my excuse. ;P), I've looked into it, and it apparently it contains information about devices and drivers.

[http://en.wikipedia.org/wiki/Sysfs]("http://en.wikipedia.org/wiki/Sysfs")

---

### Post by s3a on 2010-06-28
That IS a good excuse ;) lol. Is there a point to importing drivers to the chrooted OS though? I mean like this reminds me a bit of virtualbox where, unless I am mistaken, all that should matter is that the host OS picks up the hardware so that the client OS can use it.

---

### Post by WorMzy on 2010-06-28
I don't know if there's a specific reason to mount it, but I guess it can't hurt to mount it anyway. Like I said, I've never had any problems before when not using it, but I've never used chroot for much more than fixing grub from a Live CD. It could be that you need to have /sys mounted for more complicated tasks.

---

### Post by s3a on 2010-07-01
Ok thanks. :) I'm marking this thread as solved.

---

### Post by Farmer of Bricks on 2010-09-13
THis thread helped me in getting my booting Windows 7 install to dualboot with my nonbooting Ubuntu 10.04 install. I had had Win 7 installed beforehand, and installed Ubuntu to a partition. This nixed the Win7 install somehow, and because Win 7 was on a Microsoft Dynamic Disk volume, the Windows install DVD couldn't repair it. I reinstalled Windows 7 to the original Windows 7 partition, nixing GRUB from the MBR. 
When I reinstalled Windows 7, it took the partition all the way from the front of the drive, removing a little 63-sector spot that GRUB likes to keep its core.img in when it's installed to the MBR. Because of that missing gap, I couldn't install GRUB to the MBR. 
I ended up using Gparted on the LiveCD to move Windows right a few megabytes, then fixed Windows so it would boot with the Windows install disk. Installing GRUB was problematic, but your post helped greatly. 
```

sudo apt-get install grub
sudo mount /dev/sda5 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys 
sudo chroot /mnt
sudo update-grub

```
Apt-getting grub is necessary because not all of GRUB is contained on the Kubuntu 10.04 x64 LiveCD that I was using.
Without binding sys, grub can't find the WIndows 7 install, because it can't find the list of partitions.

```

ubuntu@ubuntu:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-legacy-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 918kB of archives.
After this operation, 303kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid/main grub 0.97-29ubuntu60 [918kB]
Fetched 918kB in 9s (100kB/s)                                                  
Preconfiguring packages ...
(Reading database ... 72114 files and directories currently installed.)
Removing grub-pc ...
Processing triggers for man-db ...
Selecting previously deselected package grub.
(Reading database ... 71893 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu60_amd64.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu60) ...
ubuntu@ubuntu:/$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:/$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:/$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:/$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:/$ sudo chroot /mnt
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:/$

```

---

