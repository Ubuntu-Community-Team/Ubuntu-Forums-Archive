---
title: "Ubuntu 12.04 completely freeze"
date: 2012-08-22
forum: General Help
---

### Post by javi_m on 2012-08-22
Hi everyone.

I couldn't find information about this:


[B]With no warnings, the system freezes completeley. From that point, i can't move the mouse pointer, open a TTY, or anything. It just keeps freezed until i press the power button for a couple of seconds.
[/B]

Hardware:
I have a Lenovo G570 laptop, I3 Sandy Bridge, 3GB DDR3 RAM, graphics Intel HD.

OS:
Ubuntu 12.04, updated
Unity wm


Don't know what the problem is.

The soft usually open is:


/*work*/
Apache with PHP and MySQL
Chromium
Firefox
Sublime Text 2
VirtualBox with Win XP virtualized (1GB RAM and 32MB video, 1 core)
Filezilla
Gimp


/*applets / plugins*/
Webapps (the plugin for chromium)
Ubuntu One indicator
Dropbox
Radiotray
weather indicator
caffeine


I really really appreciate some clues here, i'm working with lots of problems because of this. 

Thanks in advance

---

### Post by javi_m on 2012-08-22
bump

---

### Post by javi_m on 2012-08-22
bump again, sorry, but it's something really bad to me.

---

### Post by 2F4U on 2012-08-23
Did you look into the system log? This is the first thing to do when such problems start to happen. Did you check your RAM by running memtest?

---

### Post by Statia on 2012-08-23
Have you set up (enough) swap?
On my Kubuntu 12.04, just the system plus desktop (with a few widgets) consumes 1GB. 
(I read here somewhere today that KDE uses less RAM than Unity)
You give 1G to VirtualBox, that leaves 1G for two browsers, Gimp and some more applications. Having no or insufficient swap in that situation might cause problems.

---

### Post by Atitudes on 2012-08-23
Hey there, 

Sorry if this is a true noobish reply but I had the same problem about a month ago. I installed 12.04 64bits with a bootable USB but the drive wasn't big enough to have an acceptable transfer area (my mistake...) It installed ubuntu and it booted without a problem. After a while (could be 1 minute or 1 hour)it used to freeze just like you reported. 

In my case, I formatted everything to NTFS and re-installed ubuntu with a larger flash drive this time and everything worked and still works perfectly. Re-installing it without deleting all ext-4 partitions kept giving the same problem over and over... I don't know if the installer was modified meantime but i assume it was because i used to edit files in order for it to boot from the flash drive (else it'd give an error) which i don't need to perform anymore...

Good luck with your issue, i acknowledge it's is pretty annoying :(

---

### Post by javi_m on 2012-08-23
Thanks for the answers, i really appreciate them.

first: I DO looked up into var/log/ , xorg and syslog, but nothing's there (i assume that the system is completely freezed up and locked up, so there's no filled log)

second: i have a 2GB swap partition, i thinks it's more than enough, isn't it?


third: virtualbox is not always on. I can't say "VirtualBox is not the problem", but i'm quite sure that is not, because like i said, it's not running 24/7.

fourth: i didn't see how much ram unity claims, but the entirely OS is running smoothly, even when virtualbox is running. There is only a small amount of "lag" when chromium have more than 10 tabs, and XP is virtualized with VB.


Do you think virtualbox or the size of the swap partitions is causing this freeze?

Thanks!

PS: Sorry about my poor english!

---

### Post by javi_m on 2012-08-23
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)


The same bug in launchpad. There's no fix or answer, and a few folks misunderstood it, thinking it was an X bug.

---

### Post by nuttzo31 on 2012-08-23
I have been using 12.10 and with the latest 3.5 kernel updates my freezing problems  seemed to have  stopped.I will try reinstalling 12.04 later and upgrade the kernel to 3.5 and see what happens.

---

### Post by javi_m on 2012-08-24
@nuttzo31 that could be a solution. I'm unable to experiment that much, since i need to work. All my data is in another partition, but install and configure the whole thing again, it's just a terrific waste of time for me.

Anyway, my laptop stop freezing at the moment (2 days without issues). But, i'm paranoic saving everything all the time, quite annoying.

---

### Post by d4m1r on 2012-08-24
It could be a RAM usage....That is a lot of resource heavy applications to be running at the same time with only 3GB of RAM....I'd upgrade it.

---

### Post by bootedguy on 2012-08-24
I was having freeze ups on my laptop which I "fixed" by removing a mounted SMB share, that I really didn't need.

When you reboot after a freezup, checking the /var/log/kern.log can be very useful.

---

### Post by nuttzo31 on 2012-08-27
> **javi_m said:**
> @nuttzo31 that could be a solution. I'm unable to experiment that much, since i need to work. All my data is in another partition, but install and configure the whole thing again, it's just a terrific waste of time for me.

Anyway, my laptop stop freezing at the moment (2 days without issues). But, i'm paranoic saving everything all the time, quite annoying.

I have been running 12.04 with kernel 3.5 for a couple of days with no freezes.You can install the 3.5 mainline kernel over the top of the ubuntu 12.04 kernel without reinstalling(always wise to have a backup regardless).

Follow the instructions here

[http://www.itworld.com/software/289576/install-linux-kernel-351-linux-mint-13-or-ubuntu-1204](http://www.itworld.com/software/289576/install-linux-kernel-351-linux-mint-13-or-ubuntu-1204)

If things don't work you can go back to the previous kernel by holding shift at the grub menu and choose previous version from there.

The freezes could be a sandy bridge issue(i am using asus p8p67pro board)

---

### Post by javi_m on 2012-09-08
After some tests, i can tell you one thing:

The problem is related with virtualbox. I can tell you this because i didn't need to open virtualbox in a couple of weeks (i need top open it for some specific jobs). i didn't exèriment any freeze those days.

But, a couple of days ago i opened virtualbox again (some work to do) and voila! the freezes appear again.

Maybe it really is a RAM problem, in which case i will buy some more.

Thanks to every of you guys.

---

