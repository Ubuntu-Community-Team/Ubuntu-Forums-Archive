---
title: "migrate to new hard drive"
date: 2011-06-09
forum: General Help
---

### Post by DanBender on 2011-06-09
I'm about to migrate from a single 1TB drive on my Mythbuntu system to a two-disk setup with a 500GB drive for boot, root, home, etc. and the entire 1TB drive reserved for MythTV and shared videos.

In addition to being on a different hard drive than now, the partition numbers are somewhat wonky currently; I originally dual-booted Windows on sda1, which will no longer be the case. sda2 is the current myth partition and is the back half of the drive for some reason I won't go into here. Partitions 3 through 7 work all right now as root, swap, home, and space reserved for a virtual machine, but I'd like them to be 1 through whatever just for keeping me sane.

Is there a good way to do this? I was going to use remastersys to install my current install there, but I'm not certain all the data I need for a seamless install will fit on the 4 GB jump drive I have. I can mount the old partitions and copy some stuff over afterwards, but it would be nice if there were a way to just dump it on and have it mostly work. I've had to jump through some hoops to get it working the way it is now (which is quite well) and I'd like to avoid doing that again. Plus, with MythTV, there's a lot of setup involved after installation which I'd like to avoid since it's correct now.

If there is a good way to clone the partitions to the new drive, a big thing would be that the boot sector has to come over too, or can be rebuilt without needing an install. I've had a situation where that *didn't* happen, and the result was a lot of wasted time and effort.

Anyway, thanks in advance for the suggestions!

-Dan

---

### Post by DanBender on 2011-06-13
Okay, I found a way to clone my / and /home partitions using dd. So I did that and reconnected the new drive so the new partition to be root is sda1, and now I need to repair my GRUB2 data.

I've booted into a live session using my Mythbuntu 10.10 CD, and am trying to follow the directions in this post: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). It isn't exactly what I'm doing, but it sounds like it's close enough.

Only problem is, I can't seem to mount my partition! The link says to use the "places" menu to mount it, but that does't exist in the Mythbuntu environment. I haven't found any mounting utilities in the menu. I can run "mount" in the terminal, but I get an error saying "Only root can do that." does anyone know what the user and password are for the live session?

---

### Post by wildmanne39 on 2011-06-13
> **DanBender said:**
> Okay, I found a way to clone my / and /home partitions using dd. So I did that and reconnected the new drive so the new partition to be root is sda1, and now I need to repair my GRUB2 data.

I've booted into a live session using my Mythbuntu 10.10 CD, and am trying to follow the directions in this post: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). It isn't exactly what I'm doing, but it sounds like it's close enough.

Only problem is, I can't seem to mount my partition! The link says to use the "places" menu to mount it, but that does't exist in the Mythbuntu environment. I haven't found any mounting utilities in the menu. I can run "mount" in the terminal, but I get an error saying "Only root can do that." does anyone know what the user and password are for the live session?
Hi in terminal use sudo for root. Does mythubuntu have disk utility you can use it to mount a drive, if not install gparted and mount it.

---

### Post by DanBender on 2011-06-13
I'm aware of using sudo. The issue is the password. I didn't think to try with a blank password until after I posted last, but I'll try that after I put the baby to bed.

---

### Post by psusi on 2011-06-13
It is better to use cp -ax or rsync to copy the files from the old partition to the new.  dd will waste time copying free space, and requires that the source and destination partitions be exactly the same size.

---

### Post by DanBender on 2011-06-13
> **psusi said:**
> ...requires that the source and destination partitions be exactly the same size.
...or larger. Which is okay, as one was already the size I wanted, and the other I wanted to expand. The wasted time wasn't an issue either,since I had to go to the store and eat dinner during the two writes.

EDIT: The blank password was it. I was able to mount the partition and install Grub2 to the drive. I had to nano the fstab file for the drive, but that wasn't any big deal. The remaining partition work and file transfers I'll be able to do the normal way.

---

### Post by psusi on 2011-06-14
Ohh, and I forgot to mention that dd also preserves any fragmentation present.

---

### Post by DanBender on 2011-06-14
Also a good thing to know about. I'll have to defrag later.

---

### Post by T.E.N. on 2011-08-15
> **psusi said:**
> It is better to use cp -ax or rsync to copy the files from the old partition to the new.  dd will waste time copying free space [...]Encountered some strange effects after cp -ax on all partitions (and grub-install to the new /dev/sdc from a Live CD chroot of course):
No user but root would be allowed to log on (and even that one, fortunately given a password contrary to Ubuntu defaults) only to a text console).

So, the exact parameters to be used for cp or rsync are very important - which are the ones you recommend?

Having created partitions (some larger) on the new drive through "System/Administration/Disk Utility", I found them to have visibly more restricted privileges (cf. padlock symbols in the attached screenshot) but could not find what exactly the difference is. Does Live-CD default user "ubuntu" assume ownership of these partitions somehow as soon as formatted to ext4?

At any rate, here's what I did as su:
> cp -ax /media/49149403-34b5-4058-a80a-aa09baf689a9/* /media/boot
cp -ax /media/293e12cd-fa3f-44c5-9c1a-f8cb84ba5497/* /media/root
cp -ax /media/86edd332-27ad-4dda-818c-d2b6be85504d/* /media/usr
cp -ax /media/faaec839-7973-47fc-8dad-c7d6f940927e/* /media/home
cp -ax /media/381a30ab-daa3-4e2a-81c8-a2f0c2790b4b/* /media/var
Is this missing a few .* hidden files (unlike rsync?) ? At any rate it seems to mess up the user/group numbers somehow, and hence would not let me log on; "Unable to cd to '/home/user'" ...

I'll try rsync -xavuP /* /mnt/yournewpartition (on all of the above partitions but /boot) as recommended by [http://forums.whirlpool.net.au/archive/1038925#r16497194](http://forums.whirlpool.net.au/archive/1038925#r16497194) next, while [http://wiki.ubuntuusers.de/Ubuntu_umziehen#Daten-mit-dem-Programm-rsync-kopieren](http://wiki.ubuntuusers.de/Ubuntu_umziehen#Daten-mit-dem-Programm-rsync-kopieren) seems to suggest a variant not limited to --one-file-system (though I think it should be).

---

