---
title: "Which ubuntu version can install with just 2GB RAM?"
date: 2011-05-20
forum: General Help
---

### Post by dragonfly41 on 2011-05-20
I've tried to install ubuntu 10.10 on a rather old Acer 3610 1.5 GHZ notebook previously running Windows XP.

The problem I've encountered is that Acer Aspire 3613 WLMi is restricted to 2 GB RAM.

But ubuntu 10.10 stops installation process (using LiveCD) because the Acer RAM is detected to be less than the 2.5 GB minimum expected by ubuntu.

Also no Internet connection is detected when LiveCD is run .. but that is another problem.  
The Internet connection on my ubuntu 10.10 is fine as this post proves!

What ubuntu version (or other linux distro) is recommended to install with just 2 GB RAM?

---

### Post by insane_alien on 2011-05-20
when did that happen? I know it require 2GB of free hdd space but ram should be fine at even 700mb

---

### Post by walt.smith1960 on 2011-05-20
I had a desktop install running on an old Thinkpad with 384 MB. RAM. it installed fine. There's something else going on.  It DOES require about 2.5 GB H.D. space minimum.

---

### Post by 3xp10r3r|X13 on 2011-05-20
I can just agree with the previous post...really weird.
Ubuntu is designed to run on low performance hardware. (It is definitely able to)

---

### Post by corrytonapple on 2011-05-20
It cannot be the RAM that is the issue, it is the HDD space.  If you can boot a Live CD and get to the desktop, post the output of:
```
df -a
```
Or, go the GUI way.  Open GParted by going to **System > Administration > GParted**, and take a screenshot of that window by going to **Applications > Accessories > Take Screenshot**, then post it here.

---

### Post by aysiu on 2011-05-20
I've installed Ubuntu 8.04, 8.10, 9.04, 9.10, 10.04, 10.10, and 11.04 all successfully on my netbook with 2 GB of RAM. I can assure you 2 GB of RAM is plenty. I've even installed all those versions in VirtualBox with only 512 MB of RAM.

Perhaps your .iso download corrupted during download?

---

### Post by sanderj on 2011-05-20
> **dragonfly41 said:**
> I've tried to install ubuntu 10.10 on a rather old Acer 3610 1.5 GHZ notebook previously running Windows XP.

The problem I've encountered is that Acer Aspire 3613 WLMi is restricted to 2 GB RAM.

But ubuntu 10.10 stops installation process (using LiveCD) because the Acer RAM is detected to be less than the 2.5 GB minimum expected by ubuntu.

Also no Internet connection is detected when LiveCD is run .. but that is another problem.  
The Internet connection on my ubuntu 10.10 is fine as this post proves!

What ubuntu version (or other linux distro) is recommended to install with just 2 GB RAM?

2GB *RAM* is more than enough.

However, 2 (or 2.5) GB *harddisk* space is probably too little.

So: make up your mind: what's the problem?

Or better: post a picture (and/or exact message) of the Ubuntu install complaining ...

---

### Post by Jouke74 on 2011-05-20
Hi TS,

Please realize that there is computer working memory which is called RAM. For most of current day laptops it ranges between 512 MB and 4 GB. Everything above 512 MB is more than enough for Ubuntu to run without problems. 

Then there is a second thing in you computer which is the harddisk. Note that with current laptops this can also be a Solid State Disk. On this disk the Ubuntu system, as well as your user data is stored. Furthermore other operating systems can be stored here as well. When you start Ubuntu all required components are read from this disk and loaded into memory. Ubuntu needs a minimum of 2.5 GB of disk space (4 GB on average) to work. Given that you have a problem with installing I assume that not enough disk space is allocated / free for Ubuntu. You need to delete some stuff from your harddisk until there is enough free. Note that you make sure you do not need the stuff you are going to delete. Also make sure you do your disk partitioning the right way, don't erase anything important in this step.

---

### Post by ki4jgt on 2011-05-20
I've installed every version of ubuntu since 9.10 on my netbook. It's only got 1 gb of ram.

---

### Post by claracc on 2011-05-20
2 GB of ram of memory is more than enough to install ubuntu from live cd.

I am posting from a very old laptop (1997 bios), with 512 MB of ram, from which, 64 MB go for sis 630 graphics card, cpu 1 GHz, 20  GB HDD. I have ubuntu lucid lynx in it, installed from live cd without any problem ( so, with  2 GB of ram your computer has to "fly"), installation took for one hour, operating system takes 3,5 GB in HD space.

System enterely responsive and working.

---

### Post by corrytonapple on 2011-05-20
I am just saying, but since everyone is coming in and posting the same thing with the terms being confused, should we not just wait until the OP comes back and gives us the needed information instead of different users echoing the same thing as everyone else?  That is nine responses now.  
Just my 0.2

---

### Post by dragonfly41 on 2011-05-20
Sorry for the delay in coming back .. but I had to go back 
to reinstalling ubuntu 10.10 .. and in fact the 2.5 GB does refer to disk rather than RAM.

But on first installation the expected green tick against this 2.5 GB was a cross, as was the internet connection.

It took over an hour to reinstall ubuntu on Acer and my Dell Inspiron ubuntu 10.10 was down during this time..

Thanks to all the posters who corrected me on this misunderstanding on my part. I was writing from memory.

For some reason the internal 120 GB HDD was not detected on my first try 
although it had been pre-partitioned as an external drive on a working ubuntu.

In fact on first installation attempt I somehow got into BusyBox with

Alert!
/dev/disk/by-uuid/<long UUID string> .. does not exist

dropping to Shell

/proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=<long UUID string> ro quiet splash

Those problems are now history.

There are some issues on the recently re-installed ubuntu 10.10 


[LIST]
[*]delay in launching ubuntu (black screen plus blinking cursor for a period)
[*]Internet not working
[*]default password at installation not recognised when logging in
[/LIST]

but I'll keep those for other posts.

My configuration is

sda1 (ntfs) 41.9 GB .. unused .. reserved for possible later Windows installation
sda5 (ext4) 10.5 GB .. for "/" mount
sda6 (ext4) 41.9 GB .. for "/home" mount
sda7 (ntfs) 25.7 GB .. for shared files between windows and ubuntu

---

