---
title: "Solid State Disk as cache for regular hard drives?"
date: 2010-11-16
forum: General Help
---

### Post by Darxus on 2010-11-16
60 gigabyte SSDs are down around US$100.

It seems like the optimal use would be as a cache for the regular hard drives in my computer.  Eliminating the need for a fast hard drive, so I can just use a slow 2TB (~US$100) drive with a SSD cache.

Is there a good way to do this yet?

It seems like it would be nice to be able to exclude some files from caching, for things like bittorrent.

Reviews of some SSDs:
[http://www.silentpcreview.com/Consumer_SSDs](http://www.silentpcreview.com/Consumer_SSDs)

---

### Post by never say never on 2010-11-16
I would not use an SSD as a cache.  That is not what it does well.  Without special hardware it would not function that way and would simply increase the load on the system.

What I would do is install linux on the SSD and use your large hard drive to mount /home and /var and maybe swap (depending on amount of RAM system usages . . .  That way you have fast access to the file system for linux, but the stuff with frequent writes, large files . . . are stored on a normal hard drive where you don't need the speed and you don't need to worry about writes wearing out the SSD.

---

### Post by Darxus on 2010-11-16
Why wouldn't it work wonderfully?  At least as a read cache?  Why special hardware?

---

### Post by deconstrained on 2010-11-16
Why on Earth would you want to use a SSD just as a swap device, when you can have swap AND root/boot filesystems on it to take advantage of the speed? SSD's beg to be used as boot/root fs drives. Getting one just to have a faster swap partition seems like a waste of money.

Install the base system on a SSD and put your /home files in a separate HDD and you've got a lightning-fast system. I did that recently - and even with my root/swap as logical volumes inside an encrypted LUKS partition, it's still pretty freaking fast.

---

### Post by Darxus on 2010-11-16
I don't want to use an SSD as a swap partition.  I wouldn't need to ask how to do that, and that would be a massive waste losing everything on it every reboot.

I want to use it as a file cache because I want all the advantages of using it as a boot/root partition plus that excellent speed for anything else that'll fit.  

Just using it for boot/root seems like a waste, when I could have a cache optimizing what's stored on it based on usage.

---

### Post by deconstrained on 2010-11-17
> **Darxus said:**
> I want to use it as a file cache because I want all the advantages of using it as a boot/root partition plus that excellent speed for anything else that'll fit.

Just using it for boot/root seems like a waste, when I could have a cache optimizing what's stored on it based on usage.
If that's what you're asking...then I'm completely stumped, because the best I can come up with as far as a translation of this is "I want Linux to automatically store smaller, frequently used files on the SSD and larger files on the HDD, thus using both devices so that space on them is used most optimally for both speed and storage capacity." Sorry, but I have no idea if any feature of Linux (or any OS, for that matter) like that even exists. 

You could always mount SSD partitions at /var, /tmp, /bin and /lib (they contain files that are accessed quite frequently; for example, apt's package cache is in /var/cache/apt), but the result would not be better than simply putting the whole thing on the SSD. Furthermore, this bears asking: why do you need more than 60 GB for a root fs? I've rarely needed more than 15, and that's with the unwieldy behemoths Matlab and Mathematica installed. I'm not even sure if every package available in the standard Ubuntu repos would fill more than 25GB.

Anyone else care to offer suggestions? I'm completely stumped.

---

### Post by dcstar on 2010-11-17
> **Darxus said:**
> 
........
Just using it for boot/root seems like a waste, when I could have a cache optimizing what's stored on it based on usage.

Which is why Hybrid drives have been invented that do exactly that.

I use a 500GB one my system right now.

---

### Post by weblordpepe on 2010-11-18
I understand where you're coming from Darxus. Its an intermediary cache for disk-access, not swap. You're wanting to speed up your disk access, not use a flash drive as swap.

The idea is sound, really. If you don't give a **** about lifespan of the drives (which isn't so bad really). What you want to do is somehow overlay the partitions somehow or divide the workload.

I'm not sure exactly how you could do it. You could always have the fast drive mounted in a certain folder, and you could just tell your programs to save files in that folder. That would be the simplest way. (invloving editing the fstab file to configure what partition goes where)

There are a million other options though arguably more complicated.

---

### Post by Darxus on 2010-11-18
I submitted this idea here:  [http://brainstorm.ubuntu.com/idea/26498/](http://brainstorm.ubuntu.com/idea/26498/)

---

### Post by deconstrained on 2010-11-19
Actually sounds like a great future kernel feature: software-hybrid drives. Sorry for the antagonism!

---

### Post by Darxus on 2010-11-28
Looks like this has actually already been implemented in the kernel: 

CONFIG_CACHEFILES: 

This permits use of a mounted filesystem as a cache for other filesystems - primarily networking filesystems - thus allowing fast local disk to enhance the speed of slower devices. 

See Documentation/filesystems/caching/cachefiles.txt for more information.

---

### Post by mightyiam on 2013-02-25
Yea, install the cachefilesd package. I'll try it.

---

### Post by lisati on 2013-02-25
> **DawnLight said:**
> Yea, install the cachefilesd package. I'll try it.

If a thread hasn't hasn't had any activity for over a year, it is possible that something has changed that makes the information out of date. You are, however, welcome to start a new thread linking back to the old thread.

Old thread closed.

---

