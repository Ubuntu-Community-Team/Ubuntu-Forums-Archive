---
title: "Multiple Linux Distros along with Windows 7"
date: 2011-02-05
forum: General Help
---

### Post by Rushyang on 2011-02-05
Bonjour guys,

I can't stay without ubuntu a single day. That's it. I said it. But I definitely need windows 7 cause I'm a heavy gamer. But I also like to keep and use other distros like Fedora.

I came to read that only ubuntu uses GRUB 2.0 and it automatically detects all the distros which should be listed by GRUB 1.0. My question is, 

How Can i set up the Multiple OS machine Ubuntu + Fedora / BackTrack / Suse + Windows 7 ??

Someone on IRC channel told me that I just install Ubuntu last and it will detect all operating systems automatically.. But I'm a quite reluctant to that kind of short answer. It's now your call experts. 

PS: Please, Please don't tell me to try out Virtual Machines. I have used them like 1000 times.

---

### Post by techunit on 2011-02-05
It just isn't practical to do this without virtual machines or multiple harddrives. You will also run into problems partitioning as you can only have 4 primary partitions you could create an extended partition with the other OSes intalled in it.

Unless you want to manually add entries into grub you need to either install all of your distros and reinstall grub2 at the end othe process or finish installing your distros with a distro with grub2. Otherwise you won't have everything or anything listed correctly.

Do some serious reseach into multiboots. I have only dualbooted so I can't tell you much.

---

### Post by Rushyang on 2011-02-05
> **techunit said:**
> It just isn't practical to do this without virtual machines or multiple harddrives. 

Fair enough. Let's say I'm ready to use my another PC's internal HDD too. So now I have now 2 HDDs. 

> **techunit said:**
> Do some serious reseach into multiboots. 

Done with it. No search result in google is left.

---

### Post by oldfred on 2011-02-05
Herman has this guide for installing to a second drive.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

See this:
kansasnoobs multiboot:
[http://ubuntuforums.org/showthread.php?t=1679088](http://ubuntuforums.org/showthread.php?t=1679088)



This is older and uses grub legacy but shows the planning required.
chainboot 145 systems - saikee
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by techunit on 2011-02-05
Well sure go a head. Make sure you do everything in the right order so you always have a boot loader and you have that harddrive with the boot loader start first. Now it still isn't practical at all.

Could I suggest USB drives with persistent volumes? It seams like a waste if you don't use both. Hell, if it weren't for photoshop I wouldn't have windows installed next to Ubuntu.

---

### Post by Rushyang on 2011-02-07
> **techunit said:**
> Could I suggest USB drives with persistent volumes? It seams like a waste if you don't use both. Hell, if it weren't for photoshop I wouldn't have windows installed next to Ubuntu.

Well, I do have 640 GB portable. But I wouldn't like to mess with it, because it carries all of my data backups.

To Oldfred,

Thanks man.. I will look into your helpful links and report here soon. :)

---

### Post by techunit on 2011-02-07
NO NO NO NO NO NO NO NO NO Do not try making a portable hard drive a bootable live media! Really Really Really Bad IDEA!

I think that about sums up how I feel about it. use USB drives please!

---

