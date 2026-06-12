---
title: "Ubuntu 10.10 fails to load after rebooting"
date: 2010-12-15
forum: General Help
---

### Post by haydemon on 2010-12-15
Here I was, humming happily along on my Ubuntu 10.10 machine, when thanks to a stupid Windows proprietary task that I NEEDED to perform, I rebooted in Windows later this morning. When I was done with the task, I tried to reboot again back in Ubuntu, but lo & behold, it wouldn't start. I tried several times, I tried recovery mode, I tried previous versions, and NADA! It's as if the kernel only existed in name only. So now I don't know what to do, because I cannot access my Ubuntu files from Windows (which luckily still works), plus I cannot abide the idea of having to give up on Ubuntu for good and going back to Windows! I'm willing to reinstall the whole thing again, so I've downloaded a new .iso image to create a new  install CD, but I cannot seem to successfully create the new CD image either. I'm tempted to download Wubi, but I'm not sure if that's a permanent solution either. I need some suggestions, please! And remember: I'm not very technically savvy, so please include detailed instructions with any solution proposed. Thanks in advance!:???:

---

### Post by bcbc on 2010-12-15
You didn't say what happens when you try and boot Ubuntu other than "it doesn't start", which isn't a lot to go on - or what that 'proprietary task' was - maybe it has something to do with your problem?

If you download a tool called [ext2read]("http://ext2read.blogspot.com/") it can access ext2/3/4 partitions - even the virtual disk used by wubi - so you should be able to retrieve important data if you are planning to reinstall. But it's best to try and fix - in case the problem reoccurs or to understand how to prevent it reoccurring.

So run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and post back your results.

---

### Post by drewsus on 2010-12-15
> **bcbc said:**
> If you download a tool called [ext2read]("http://ext2read.blogspot.com/") it can access ext2/3/4 partitions - even the virtual disk used by wubi - so you should be able to retrieve important data 

I would not recommend accessing an ext4 filesystem with such a tool. Corruption is a definite possibility. 
Alternatively, you can boot from a live CD and mount whatever partition you want and copy stuff from there to your NTFS partition or an external HDD.

---

### Post by drewsus on 2010-12-15
Furthermore, I would recommend that you manually partition your hard drive when installing Ubuntu. 
Have a "/" partition as your system files. A "/home" partition for your home directory. And a "swap" partiton that is 2x the size of your system RAM. This way, you can reinstall Ubuntu any time you like, formatting the "/" and using your existing swap and /home partitions (DO NOT REFORMAT YOUR HOME PARTITION OTHERWISE THIS DEFEATS THE PURPOSE AND YOU LOSE ALL YOUR DATA). 

This way, you can keep all your configuration files and folders as well as your personal data. Just reinstall the filesystem.

---

### Post by haydemon on 2010-12-15
> **bcbc said:**
> You didn't say what happens when you try and boot Ubuntu other than "it doesn't start", which isn't a lot to go on - or what that 'proprietary task' was - maybe it has something to do with your problem?

Well, nothing happens! Nothing starts. I don't get an error message, I don't get an icon, just a black screen with a blinking cursor at the top left of the screen. OK. First Grub starts, and the options of OS to choose from--I DO get that; that's how come I can start Windows, otherwise I'd really be hosed (particularly since it's my work machine--:p), but where usually when I waited a few seconds Ubuntu would start all on its own, now it doesn't; so when I press <enter> to select Ubuntu, that's when the screen goes black--as described above. The Windows task was connecting with my bank online; I had to scan a document to send to them. Nothing else. I restarted the computer to go back to Ubuntu, and that's when all hell broke loose. I went back to Windows and checked a few forums and discovered that there have been some problems with the latest updates that came down; other people were having similar problems. The issue is that the solutions given are WAY above my head, and they include using a live CD, which I don't have.

---

### Post by bcbc on 2010-12-15
OK just to be clear, the first screen you see when your machine boots (after the BIOS) looks like this:

> [CENTER]**GNU GRUB version 1.98...**[/CENTER]

Ubuntu, with Linux generic 2.xxxxx 
Ubuntu, with Linux generic 2.xxxxx (recovery mode)
etc.
Memtest
Windows


Or it looks like this:
> **[CENTER]Windows Boot Manager[/CENTER]**

Microsoft Windows Vista
Ubuntu

And you installed version 10.10 (or did you upgrade to 10.10)?

---

### Post by haydemon on 2010-12-15
> **bcbc said:**
> OK just to be clear, the first screen you see when your machine boots (after the BIOS) looks like this:



Or it looks like this:


And you installed version 10.10 (or did you upgrade to 10.10)?
It looks like the first example. I upgraded to v.10.10 but it's been a while (at least a month).

---

### Post by bcbc on 2010-12-15
> **haydemon said:**
> It looks like the first example. I upgraded to v.10.10 but it's been a while (at least a month).

How did you originally install without an Ubuntu CD, or do you have an older version CD. If you have any Ubuntu CD you should be able to boot it and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"), then post the results back.

---

### Post by haydemon on 2010-12-15
> **bcbc said:**
> How did you originally install without an Ubuntu CD, or do you have an older version CD. If you have any Ubuntu CD you should be able to boot it and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"), then post the results back.
I installed with a 9.10 CD and upgraded from there. I don't think I still have the original CD tho. :(

---

### Post by bcbc on 2010-12-15
> **haydemon said:**
> I installed with a 9.10 CD and upgraded from there. I don't think I still have the original CD tho. :(

What version of grub does it say on the top?
When you hit 'e' on the first entry, what partition is it booting? (command "set root='(hdX,Y)'" or "set root='(msdosX,Y)'")
Does it refer to the partition with the UUID in the line starting "linux /boot/vmlinuz.... root=UUID=xxx ..." or is it "linux /boot/vmlinuz... root=/dev/sdXY ..."?

---

### Post by haydemon on 2010-12-16
> **bcbc said:**
> What version of grub does it say on the top?
When you hit 'e' on the first entry, what partition is it booting? (command "set root='(hdX,Y)'" or "set root='(msdosX,Y)'")
Does it refer to the partition with the UUID in the line starting "linux /boot/vmlinuz.... root=UUID=xxx ..." or is it "linux /boot/vmlinuz... root=/dev/sdXY ..."?
set root='(hd0, msdos6)'
linux /boot/vmlinuz-2.6.35-24-generic root=UUID=a33acf9c-0574-45bc-8\f14-a07000149892 ro quiet splash.

---

### Post by haydemon on 2010-12-16
> **drewsus said:**
> Furthermore, I would recommend that you manually partition your hard drive when installing Ubuntu. 
Have a "/" partition as your system files. A "/home" partition for your home directory. And a "swap" partiton that is 2x the size of your system RAM. This way, you can reinstall Ubuntu any time you like, formatting the "/" and using your existing swap and /home partitions (DO NOT REFORMAT YOUR HOME PARTITION OTHERWISE THIS DEFEATS THE PURPOSE AND YOU LOSE ALL YOUR DATA). 

This way, you can keep all your configuration files and folders as well as your personal data. Just reinstall the filesystem.
Can you be a little more specific with this? I'm always afraid of screwing things up when manually partitioning the HD; I tried that with a netbook I have @home and totally bungled the whole thing (not to mention the fact that I didn't have enough RAM, but that's a whole 'nother story). So what I need, if you can provide is this: a step-by-step instruction as to how much memory to assign to each partition, etc. I have a large hard drive, so there's no memory problem; however, I do have a dual boot system. with Windows (the hog) on the other side. Thx.

---

### Post by haydemon on 2010-12-16
MY  PROBLEM IS SOLVED and I'm back in the saddle again! Thanks to all who replied to my messages.:KS

This is how it went down: I was about to reinstall the netbook version from a USB drive (which I already had), when I decided to try rebooting from one of the older kernels in Recovery Mode (this hadn't worked before either), and voila. First I picked 'GRUB Bootloader" from the menu, then "Repair Broken Packages." At the end of the task, I rebooted and everything worked!

Thanks again y'all!

---

