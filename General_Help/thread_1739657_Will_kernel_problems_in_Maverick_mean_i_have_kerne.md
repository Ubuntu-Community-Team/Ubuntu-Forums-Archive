---
title: "Will kernel problems in Maverick mean i have kernel problems in Natty?"
date: 2011-04-26
forum: General Help
---

### Post by MorrisseyJ on 2011-04-26
Hi all, 

Question about installing Natty, given that i have had kernel problems in Maverick. 

My problem is that i have not been able to get any of the kernels working for Maverick since 2.6.35-22. All of -23 - -28 have resulted in my system randomly freezing up, with me not being able to find anything in the file logs with which to report a bug (see: [http://ubuntuforums.org/showthread.php?t=1633453](http://ubuntuforums.org/showthread.php?t=1633453) & [http://ubuntuforums.org/showthread.php?t=1683195](http://ubuntuforums.org/showthread.php?t=1683195)). 

I have managed to run 11.04 off a live USB without a problem, but i am not sure if that means the kernel problems are resolved. For example, i haven't meddled with my system as much when using the live USB so i am not sure if some conflict might be happening with something i have yet to try on 11.04. 

So, some questions:

1. Are the problems i am having with the more recent kernels in Maverick likely to have an impact in Natty?
2. If i install Natty and have problems, would i be able to install the old 2.6.35-22 kernel and run Natty off that?
3. If no to 2.; if i install Natty and have problems and thus seek to reinstall Maverick, would i be able to do so off the old kernel, or will my reinstall of Maverick mean that i only get the 2.6.35-28 kernel?

If anyone can help me out on this, or point me to a site with relevant information, that would be great.

Thanks,

---

### Post by MorrisseyJ on 2011-04-28
Solution looks something like:

Get relevant kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), add it to the GRUB screen and try run Maverick off it. 

To do so you need to grab the latest stable kernel ('rc' in the kernel name means release candidate). This entails downloading the three debs appropriate to your architecture (i386 for 32-bit, amd64 for 64-bit) - To find out put > uname -a in a terminal.

e.g. for 32-bit:

linux-headers-2.6.38-02063804-generic_2.6.38-02063804.201104221009_i386.deb
linux-headers-2.6.38-02063804_2.6.38-02063804.201104221009_all.deb
linux-image-2.6.38-02063804-generic_2.6.38-02063804.201104221009_i386.deb

Save them into the same directory, ideally with nothing else in it, then in a terminal cd to that directory and install, e.g.:

> $ cd download/kernel
$ sudo dpkg -i *.deb

This will install the kernel. 

One should keep in mind that it's likely that any proprietary graphics drivers (probably nvidia, almost definitely fglrx) will break and not install correctly unless you have the x-swat ppa added to your software sources.

With thanks to the good person on the UK Ubuntu email list.

---

### Post by KegHead on 2011-04-28
Hi!

Have you tried;

sudo apt-get install linux-image -f

KegHead

---

### Post by MorrisseyJ on 2011-04-28
No, sorry. What is that likely to do?

---

### Post by KegHead on 2011-04-28
Hi!

It will upgrade the kernel for your version of Ubuntu.

I use the command at least one a day!

Restart.

[COLOR="Red"]No harm or foul.[/COLOR]

KegHead

---

### Post by MorrisseyJ on 2011-04-28
But my problem is that the latest kernels - anything after -22 - all give me problems. 

Will this command likely solve those issues on the later kernels, or will it just put me on the latest kernel.

Sorry if i am not understanding, i appreciate the advice.

---

### Post by jimfixx on 2011-05-14
Has anyone found a solution to this? Without the need to downgrade?

Would an upgrade to 11.04 solve this issue? Has anyone tried?

I'm desperate! My system hangs every 1-2 days... :(

---

### Post by MorrisseyJ on 2011-05-15
I am not sure, i'll be trying an upgrade later this week - i'll let you know how it goes. 

One way to partially test the system would be to run 11.04 of a live USB. Problem is that a crash every 1-2 days means that you'd need to fiddle with the flash for a pretty long time before you found out.

---

### Post by jimfixx on 2011-05-15
Thanks for the reply!

I actually got impatient and upgraded this morning.. Lol

Seems to have gone relatively smoothly.. Hung near the end but I was able recover and complete the upgrade.

Air video, Xbmc, mdadm all seem to be working properly.. My raid was detected and mounted automatically on the first boot..

Time to wait and see if I experience a crash over the next few days.. 

I'll be sure to post my results!

Thanks again!

---

### Post by MorrisseyJ on 2011-05-15
Great, thanks. Glad to hear its going well for the minute. 

When you get back to this, could you give me some idea of your hardware, it would be good to get a sense of how much of a trick its going to be to get things up and running.

Thanks.

---

### Post by jimfixx on 2011-05-16
Hey!

Well I'm somewhat sad to report that I had another crash yesterday. However, I'm hinging some hope that perhaps it was caused by not having completed the e2fsck command that is run on startup if your drives have exceeded a certain number of mounts..

It's been back up and running for 12 hours now without another crash.. I'll keep you posted.


As for my current hardware:


Ubuntu 11.04 Natty 
Kernel Ver: 2.6.38-8

Intel Core 2 Duo 2.33 ghz
4 gb ram
40 gb ssd hdd (OCX)
Nvidia Geforce 9400 - 512mb - dual display 

There is also a 7.5 TB raid (level 5) array using mdadm (6 x 1.5TB Seagate Barracuda SATA II)

It's mostly used as a file server.

I run XBMC, FFmpeg (AirVideo Server2.2.5), and Sabnzbd primarily - I don't have much else installed.


Hope that helps!


EDIT**** - Still up and running without a crash - It's been about 36 hours!

Cheers,

---

### Post by MorrisseyJ on 2011-05-26
jimfixx glad its working.

I can also report that i am on Natty and no crashes. 

The only problem appears to the be this bug [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/778490](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/778490)

---

### Post by MorrisseyJ on 2011-08-09
Being logged out appears to have stopped and otherwise everything is running fine under natty. 

Will mark as solved.

---

