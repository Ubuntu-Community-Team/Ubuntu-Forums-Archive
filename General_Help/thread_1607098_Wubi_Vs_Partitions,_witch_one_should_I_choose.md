---
title: "Wubi Vs Partitions, witch one should I choose?"
date: 2010-10-27
forum: General Help
---

### Post by Lancro on 2010-10-27
Now I use wubi installation, Im upgrading it to 10.10 because I saw in the live cd that It solves my microphone bug issue, but I saw a tutorial about changing wubi installation to partition installation, and now I ask myself, why?, Its any performance issue I should know?, am I using a "bad" ubuntu installation?, Its about performance maybe?, My computer could be faster?...

And in case is better to use the partition system, is there any software free to resize the windows partition?, I tried gparted but I cannot resize that partition, and with windows manager it only takes 33GB of 87 to resize, and I would like to take more...

Thanks for your advise!!

---

### Post by Silent Warrior on 2010-10-27
I don't use Wubi myself, but from what I've heard it's mostly intended as a convenience. What I HAVE heard (or read, rather) is of people having some unexpected problems, quite foreign to those of us who install the 'proper' (partition) way. If you install Ubuntu in its own partition, you will obviously have to reboot to switch between Windows and Ubuntu - the one point in Wubi's favour, to my knowledge.

As far as resizing NTFS-partitions, Windows-native tools are recommended. Note that you can have a pretty lavish installation reserving just ~15 Gb for / (/home and swap getting the rest), and that you can access the Windows-partition through Ubuntu. If you have a bunch of data on the Windows-partition, you should be able to keep on using it, so if your /home can't be as big as you like, that's no reason to fret.

---

### Post by Lancro on 2010-10-27
So, if I take a 33GB partition, with 4GB for swap (my ram is 4GB), and the rest for ubuntu, I wont need more space?, I can use windows partition for data with no problem?, I love installing programs in ubuntu xD, I have photoshop in ubuntu, Can I install ubuntu aplications on NTFS file system?.

Thanks.

---

### Post by Verbeck on 2010-10-27
> **Lancro said:**
> So, if I take a 33GB partition, with 4GB for swap (my ram is 4GB), and the rest for ubuntu, I wont need more space?, I can use windows partition for data with no problem?, I love installing programs in ubuntu xD, I have photoshop in ubuntu, Can I install ubuntu aplications on NTFS file system?.

Thanks.
ubuntu programs cannot be installed on a ntfs partition. 33gb would be enough for ubuntu if you plan to use a separate data partition

---

### Post by boghadab on 2010-10-27
from my experience in ubuntu and kubuntu, i certainly know that proper installation is slightly better, for regular daily basis usage, you will not notice a big difference, and if you defrag your partition all the time, you will be fine, i run it on 6 gigs of ram, i just love it, i use wubi, and i am not planning to change the installation to proper, wish this helps.

---

### Post by WorMzy on 2010-10-27
Wubi is a way of trying out Ubuntu, it isn't supposed to be used as a permanent solution. Kernel updates will occasionally break Wubi installations, and you will suffer from a slight reduction in performance. Also, your root.disk (where all your Ubuntu files are stored) is at the mercy of the Windows chkdsk utility which has been reported to occasionally remove it to a "recovered files" folder without warning; it is also susceptible to malware attacks. However, you don't need to worry about messing up your partitions if you install with Wubi, so it's not all bad.

I recommend installing to partitions.

---

### Post by Lancro on 2010-10-27
> **Verbeck said:**
> ubuntu programs cannot be installed on a ntfs partition. 33gb would be enough for ubuntu if you plan to use a separate data partition

Well, all my MP3 is in the windows partition, 20 GB of MP3, I started using wubi only for LAMP, Im learning web programming, but as days pased by I dont use a lot lamp, and I use a lot ubuntu, I love it xD, and I want it to be at the best perfomance, and to upgrade it in the future as new releases come, I want it at full capacity, so I wont have to resize partitions or something else, a long term installation, for always, I tried It and now I love it, thats why I ask you, that knows ubuntu better than me, I dont want to lose my ubuntu instalation as well, but I  saw the tutorial for going wubi to partitions is well accepted and It donts brings any problem, so Im divided...

Thanks.

---

### Post by Verbeck on 2010-10-27
what i meant by not being able to install ubuntu programs on an ntfs file system is that the programs are not organised as it is in windows (everything in c:/program files) .
but as you've already stated, there are several HOWTO's to migrate from wubi  ,retaining all the currently installed programs

sorry if i confused you ..

---

### Post by Lancro on 2010-10-27
> **Verbeck said:**
> what i meant by not being able to install ubuntu programs on an ntfs file system is that the programs are not organised as it is in windows (everything in c:/program files) .
but as you've already stated, there are several HOWTO's to migrate from wubi  ,retaining all the currently installed programs

sorry if i confused you

Dont worry, I have read a lot of tutorials, first I upgraded my wubi installation of 10.04 to 10.10, the bug appeared, but I knew its solution and its working, now Im on windows resizing partitions, I will change it to partitions, the only thing is that the splash screen, before the login one, now doesnt displays the ubuntu logo, now it says, in plain text "UBUNTU 10.10" and its a little ugly, It also shows me the commands of starting apache 2, and at shutdown the same, but the system is working nice, I will continue my travel thruoght partitions xD, I expect everything goes ok.

Thanks.

---

### Post by mcduck on 2010-10-27
> **Lancro said:**
> So, if I take a 33GB partition, with 4GB for swap (my ram is 4GB), and the rest for ubuntu, I wont need more space?, I can use windows partition for data with no problem?, I love installing programs in ubuntu xD, I have photoshop in ubuntu, Can I install ubuntu aplications on NTFS file system?.

Thanks.

33GB is plenty of space for Ubuntu. Linux software is pretty efficient in disk usage, much thanks to common use of shared libraries, so you'll have to install quite a lot of programs to even fill a 10GB root partition. It's pretty much just a question of how much space you want for your personal files on that partition. 

Like already mentioned, you won't be able to install Linux programs into Windows partition, and you can't use it as your home directory either. But you will be able to access it easily so you can keep most of your personal files there if you want to.


... And yes, I definitely recommend a normal install over Wubi. Wubi installs don't really provide any other benefits than not having to partition your drive, but they have worse performance, are more likely to break, and much harder to fix than normal installs are. (You can easily boot with a live-CD and mount a real Linux partition to fix stuff in necessary, doing the same for a Wubi install is rather complicated)

---

### Post by Lancro on 2010-10-27
As windows partition program is lasting a lot xD, I will ask two questions, I will use the tutorial of going from wubi to a partition, will I have the same performance as a clean partition installation?, and when I install it to partitions, I can unistall wubi from windows, so I will have 30  GB more of space to clean, can I resize my linux partition with Gparted usin unallocated space?.

Thanks.

---

### Post by irv on 2010-10-27
Here is a snapshot of my hard drive, and as you can see, sda5 the linux partition is only using 24 GiB and has 33 GiB free and I have a large install. I also have a NTFS partition for Data files and set it at 72 GiB, it is sda4. The reason I set it up like this, is because I can get at my files from either Windows or Ubuntu. I feel I have a good balance in using the space on my 300 GiB hard drive.
[ATTACH]173652[/ATTACH]
I tried Wubi, but I only did it to see what it was like. I found it worked OK, but I am in Ubuntu about 98% of the time so I like this setup much better. I only use windows for one thing now, so Ubuntu is my main OS.

---

### Post by Lancro on 2010-10-27
All done, thanks to all, I have a new bug xD, but I will work it in another threat, see you.

---

