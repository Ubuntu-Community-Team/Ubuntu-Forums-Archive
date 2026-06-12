---
title: "Slave Hard Drive Died, Now Grub Error 15"
date: 2009-06-30
forum: General Help
---

### Post by Brandon! on 2009-06-30
So I have my buntu machine running with 3 hard drives.  Well I had 3.  The other day, one of my hard drives (named Junior) died.  I knew Junior was unstable, so I haven't put anything important on him for quite some time -- just some DVD ISOs and some copies of music I had elsewhere.  When the drive died, I simple disconnected him and tried to reboot.  Unfortunately, now I get an error like this:
> Booting from local disk...
GRUB Loading stage1.5.


GRUB loading please wait...
Error 15

I did my initial googling and it looks like my boot config may be wrong.  Unfortunately, I don't know how to correct this.  I tried multiple "walkthroughs" to try and reinstall grub, but I couldn't get anything to work with my setup.  Here's some information that will probably be helpful and speed this process up a bit:
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ccfbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5905    47431881    7  HPFS/NTFS
/dev/sda2            5906        5967      498015   82  Linux swap / Solaris
/dev/sda3            5968        9729    30218265   83  Linux
ubuntu@ubuntu:~$ 

This hard drive was used for dual booting early on, but I've since decided that I could care less about XP on this machine, so I never use it.  Bonus points if someone can fix this problem WHILE removing the XP partition to let 'buntu stretch its legs a little.

Also, once I started troubleshooting this, I decided to remove my data drive for simplicity (so that's why there is only 1 drive showing right now).

Thanks guys.

---

### Post by blueridgedog on 2009-06-30
The dead drive may have re-ordered your drives and grub sees them differently than before.  I would try and reinstall grub.  Booting off of a live CD, here are the steps:

Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will result in a "grub>" prompt. At grub>. enter these commands
```

find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to use as the source for the new mbr.

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Note, if you want to put the new mbr in another hard drive, you will need to adjust it accordingly.

Finally exit the grub shell
```

quit
```

If you get it booting again, you can either format the NTFS partition to use with Ubuntu as another partion, or delete it and expand your Ubuntu partition.  Once done, you may need to re-install grub again as the partition number will change.

---

### Post by Brandon! on 2009-06-30
Thanks for the reply.  I get this error still:
```
grub> find /boot/grub/stage1

Error 15: File not found

grub> 
```

Any ideas?

---

### Post by blueridgedog on 2009-06-30
While booted on the live CD, can you access your hard drive and post the contents of /boot/grub/menu.lst?

---

### Post by Brandon! on 2009-06-30
menu.lst is missing:
```
ubuntu@ubuntu:/media/disk/boot/grub$ ls
device.map
ubuntu@ubuntu:/media/disk/boot/grub$ 
```

---

### Post by blueridgedog on 2009-07-01
Are there kernels in the /boot directory? Can you post an ls of that?

---

### Post by Brandon! on 2009-07-01
Wow, I feel dumb!  When I did the ls like you requested, I saw that I had a folder called grub_old.  I swapped it with grub and the computer booted up.  I have NO IDEA what I did to my grub, but I do remember tinkering with it now (something about a custom boot screen I think).  Anyways, thanks a ton for the help.

---

### Post by pro003 on 2009-07-01
> **Brandon! said:**
> Wow, I feel dumb!  When I did the ls like you requested, I saw that I had a folder called grub_old.  I swapped it with grub and the computer booted up.  I have NO IDEA what I did to my grub, but I do remember tinkering with it now (something about a custom boot screen I think).  Anyways, thanks a ton for the help.

Just a bit curious about this. Do you actually remember did you intentionally renamed this folder 'grub' into 'grub_old'?

Cause I don't know how could this happen otherwise?

Again: just curious ;)

---

### Post by blueridgedog on 2009-07-01
I too am curios.  I was about to talk the OP through re-installing grub via a chroot live cd environment and I am frankly glad I don't have to as it is process I only know from research.

---

### Post by ronaldprettyman on 2009-07-01
> **blueridgedog said:**
> I too am curios.  I was about to talk the OP through re-installing grub via a chroot live cd environment and I am frankly glad I don't have to as it is process I only know from research.
Its alot like installing gentoo, except you don't have to compile anything and it doesn't take as long. I've actually used the gentoo manual as a reference when chrooting a system back to life, as its easier to find then the debian/ubuntu equivalent which is near the end of the installation tutorial, where it is the installation tutorial for gentoo, only difference being apt, and you don't have to extract any archives just debootstrap. Makes for a great barebones system when cloning

---

### Post by Brandon! on 2009-07-01
Yeah, as embarrassed as I am for not remembering what I broke, I guess I might as well explain the whole thing (its the least I could do for wasting your time):

So I've been using Ubuntu as a second computer (mostly for web development projects) for a few months now and I am starting to get the hang of it.  Typically when that happens, I start to get cocky.  In this case, I decided I would try and toy with a custom boot screen (I think it was this tutorial, but its currently down [http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)).  Before I made changes, I was smart enough to make a backup copy (hell, I was probably instructed to, but I'll take credit for now).  I think I gave it a few attempts and I guess at some point I gave up.  Flash forward a few days/weeks to when I had a hard drive crash.  I never reboot this machine, so by now I had completely forgotten that I even tried to do this "customization".  When I tried to reboot after taking the hard drive out, all hell had broken loose.

All-in-all, I'm pretty bad with Ubuntu, and add to that the fact I am very forgetful, I become pretty dangerous.  But this is how I learn I guess.

---

### Post by ronaldprettyman on 2009-07-02
> **Brandon! said:**
> Yeah, as embarrassed as I am for not remembering what I broke, I guess I might as well explain the whole thing (its the least I could do for wasting your time):

So I've been using Ubuntu as a second computer (mostly for web development projects) for a few months now and I am starting to get the hang of it.  Typically when that happens, I start to get cocky.  In this case, I decided I would try and toy with a custom boot screen (I think it was this tutorial, but its currently down [http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)).  Before I made changes, I was smart enough to make a backup copy (hell, I was probably instructed to, but I'll take credit for now).  I think I gave it a few attempts and I guess at some point I gave up.  Flash forward a few days/weeks to when I had a hard drive crash.  I never reboot this machine, so by now I had completely forgotten that I even tried to do this "customization".  When I tried to reboot after taking the hard drive out, all hell had broken loose.

All-in-all, I'm pretty bad with Ubuntu, and add to that the fact I am very forgetful, I become pretty dangerous.  But this is how I learn I guess.
Its the best way to learn, its like in the military is the difference between an officer straight out a college and an officer with enlisted experience. Experience is everything.

---

