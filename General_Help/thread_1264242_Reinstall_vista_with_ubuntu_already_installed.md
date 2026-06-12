---
title: "Reinstall vista with ubuntu already installed"
date: 2009-09-11
forum: General Help
---

### Post by zandreas on 2009-09-11
Hello everyone!
As this is the first time I write in this forum, sorry if I'm a bit out of spirit.

I have a small problem. I have a dual-boot DELL latitude D830 laptop with VISTA and UBUNTU hardy installed. Apparently, the ù*$:*£ VISTA don't work: The computer just turns off randomly (at first after startup, now DURING startup). Could be due to the fact that I replaced the cooling fan recently...?

Anyway, I guess I have to reinstall VISTA. The partitions are all there, everything's fine from this point of view, here are the results of  sudo fdisk -l:

/dev/sda1               1          29      232911   de  Dell Utility
/dev/sda2              30         291     2097152    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *         291        6665    51200000    7  HPFS/NTFS
/dev/sda4            6666       19457   102751740    5  Extended
/dev/sda5            6666       10312    29294496   83  Linux
/dev/sda6           10313       18822    68356543+  83  Linux
/dev/sda7           18823       19065     1951866    b  W95 FAT32
/dev/sda8           19066       19457     3148708+  82  Linux swap / Solaris

(now that I notice, I don't know what "Partition 2 does not end on cylinder boundary." means).

I have the VISTA installation cd and all, I'd like a little help if possible to reinstall vista without losing my ubuntu installation and configuration.

Thanks a lot!

---

### Post by iswear on 2009-09-11
Have you tried repairing vista?

---

### Post by zandreas on 2009-09-12
Actually, I did what VISTA has suggested me from time to time (start in repair mode or sth). The problem persists, so I guess I don't have some other solution: Even if I get windows started, it shuts down after a few minutes, so I don't have time to repair anything!

Did you have something in particular in mind?

---

### Post by rocket16 on 2009-09-12
**This might be the work of a Virus. By the way, did you try the "shutdown" commands in Windows, along with the /a parameter? This will cancel the Shutdown.**

---

### Post by Hangwire on 2009-09-12
I hope this might help you in some way. 
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm) 
Just format the windows partition to a clean NTFS one from Ubuntu using gparted 
From what I've heard, Vista can mess up the bootloader. 
If you dont have GParted, install it by using sudo apt-get install gparted, and run it from the terminal using sudo gparted (yes, it requires root privileges). 

Good luck!

---

### Post by smooch101 on 2009-09-12
Hello,

Yes i think a dual boot will be the best way to go then you will have Ubuntu + Vista :)

Thanks

---

### Post by zandreas on 2009-09-12
I'm also thinking it might be a virus, in any case it's not hardware, since I don't have the problem with Ubuntu. What COULD also be the problem is that a few months ago, I had a serious crash due to cooling fan malfunction (hardware this time) and DELL changed a few parts inside the laptop. I was wondering if, for some reason, Vista don't see some of tha parts that were changed (although I get no error message or sth).

With regards to "shutdown" with the /a option, sorry, could you explain this a bit more? Where do I specify this /a parameter?
Sorry, but I'm not too experienced, at least under windows (ESPECIALLY vista) I have never played around to see the operating system and its options itsself, I just use it!
Should I start windows in a specific way? Or should I just type "shutdown" (along with sth else) in a command line after I normally start windows? In this case, it's not obvious to do so, since the pc keeps shutting down!

---

### Post by zandreas on 2009-09-12
Hi, thanks for the tip!
I had also looked at this link, although it describes how to install vista when the hard drive is all linux. I was wondering if there would be some difference now that the windows partition already exists..

I guess I'll just try what the site describes in about a week, when I'll have my vista installation CD back....

---

### Post by chinmaya_n on 2009-09-12
If u have a ubuntu live cd.... its quite easy!

1. Install Vista in the same partitions as before! Dont make any changes to the linux partitions
2. During the installation it will overwrite the GRUB.
3. After completely installing the windows. boot the live cd and follow the instructions specified in this page : 
   [http://chinmaya_n.hyperphp.com/node/4](http://chinmaya_n.hyperphp.com/node/4)

Good luck! ( you dont loose any data in linux partitions )

---

### Post by rocket16 on 2009-09-12
Sure. To abort the Shutdown, you need to go to the Command Prompt (or simply open a run windows). Now, type exactly "shutdown /a", in case it doesn't work, type "shutdown -a". Now, this will about the Shutdown. And, if you wish to do it repeatedly, just make a new shortcut at Desktop and give the shortcut command as "shutdown /a". Whenever you click this shortcut, the Shutdown will abort.

---

### Post by zandreas on 2009-09-12
Thanks a lot for the help everyone!
I'll try to see what's wrong with vista at first, if I don't get somewhere I'll just reinstall them following your instructions as soon as I get my hands on my vista CD.
Apparently other people have similar problems, I'll let you know how it goes.

Thanks again!

---

