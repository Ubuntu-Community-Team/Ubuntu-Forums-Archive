---
title: "problems opening synaptic package manager"
date: 2012-09-28
forum: General Help
---

### Post by gizzacroggy on 2012-09-28
Hi,

I have a problem with both ubuntu software centre - no install butons - and with synaptic package manager - when i open it says 

E: The package linux-image-2.6.32-42-generic needs to be reinstalled, but I can't find an archive for it.

i tried to install 
[I]claire@claire-laptop:~$ sudo apt-get install linux-headers-2.6.32-42-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.32-42-generic needs to be reinstalled, but I can't find an archive for it.
[/I]
I tried to remove and it said the same thing.

any suggestions? i am quite a terminal novice so would be really helpful if you can be clear with instructions.

thanks 

claire

---

### Post by Bucky Ball on 2012-09-28
Try these commands one after the other, with no Synaptics or Software Centre open:
```

sudo apt-get install update
sudo apt-get install upgrade 
```The latter will upgrade software, not the release ...

What errors did that throw? Is this a recent install and what version?

---

### Post by gizzacroggy on 2012-10-21
Hi,

sorry delay, the email alert that you had replied got hidden as spam.

I just tried what you suggested...

claire@claire-laptop:~$ sudo apt-get install update
[sudo] password for claire: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.32-42-generic needs to be reinstalled, but I can't find an archive for it.
claire@claire-laptop:~$ sudo apt-get install upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.32-42-generic needs to be reinstalled, but I can't find an archive for it.
claire@claire-laptop:~$

---

### Post by CaptainMark on 2012-10-21
try```
sudo apt-get install -f
```been known to get me out of a few apt-get hell holes

---

### Post by Bucky Ball on 2012-10-21
I'm presuming you're using 10.04? If you're using 12.04 the kernel you're having problems with is not installed and not required. This may have occurred as a result of an auto-upgrade (through Synaptics or SCentre) from 10.04 (or 11.10) to 12.04.

Please confirm which release you are using. ;)

---

### Post by Starcruiser322 on 2012-10-21
You can also try 
sudo apt-get remove linux-image-2.6.32-42-generic
sudo apt-get install linux-image-2.6.32-42-generic

If that doesn't work, try changing "remove" to "purge" to do a total removal.
NOTE: If it gives you a huge list of software to be removed along with the header, proceed at your own risk. Ensure you have backups!

---

### Post by gizzacroggy on 2012-10-22
Yes, i am using 10.04.

---

### Post by gizzacroggy on 2012-10-22
hi, thanks fro suggestion but neither remove or purge work.....

claire@claire-laptop:~$ sudo apt-get purge linux-image-2.6.32-42-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-image-2.6.32-42-generic needs to be reinstalled, but I can't find an archive for it.

---

### Post by Bucky Ball on 2012-10-22
Open Synaptics and search for:

2.6.32-42-generic

You will find it is uninstalled or need an upgrade/partial upgrade. Install and see if that works. You don't want to get rid of that as it is a 10.04 kernel. It may not be the current one but the current one may rely on that being installed before it can be installed.

---

### Post by gizzacroggy on 2012-10-23
It is not possible to open synaptic.

when i do, it tells me the problem package needs reinstalling and there has been an internal error opening cache.

---

### Post by Bucky Ball on 2012-10-23
Try booting from the recovery kernel, when you get to the options choose to drop to a shell with network, and try Starcruiser's tips, if you haven't already:

> **Starcruiser322 said:**
> You can also try 
sudo apt-get remove linux-image-2.6.32-42-generic
sudo apt-get install linux-image-2.6.32-42-generic

If that doesn't work, try changing "remove" to "purge" to do a total removal.
NOTE: If it gives you a huge list of software to be removed along with the header, proceed at your own risk. Ensure you have backups!

The recovery should be the second on the list when you boot. You could also try the previous kernel, which would be the third on the list, then try the 'sudu apt-get update' in a terminal.

---

### Post by buckyaustin on 2012-10-23
Try this in terminal. For Kubuntu kdesudo for Ubuntu gksudo. So it's "gksudo synaptic". Should work.

---

### Post by gizzacroggy on 2012-10-23
it brings up the same error message as when i try open synaptic through system - administation

---

### Post by gizzacroggy on 2012-10-23
trying that but not clear how to open recovery kernal. when it boots i press f12 to enter boot options - i get boot from hard drive or cd. or f2 for set up which takes me in to BIOS.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) - shift or escape don't work for me - how can i enter grub menu?

thanks

---

### Post by gizzacroggy on 2012-10-23
i managed to change my grub settings with gedit and accessed grub options. entered recovery for version -generic rather than generic-pae. 

same error message about linux-image 2.6.32-42-generic need reinstalling but can't find archive for it.

---

### Post by gizzacroggy on 2012-10-29
hi, does anyone else have any ideas?

thanks

---

### Post by flint5 on 2012-10-29
Have you some older versions of kernels?? You can see them when the GRUB starts.
If you have, than select some older kernel to start Ubuntu.
When Ubuntu loads, try to open software manager and synaptic.
If this works, update and upgrade, maybe will this fix linux-image 2.6.32-42-generic,
if not you can always use some older kernel that works.

---

### Post by gizzacroggy on 2012-10-30
Hi, none of the older kernals made any difference - same issue.

However,... i tried to solve another problem, which may have been connected to causing this problem.

This all began when i tried to use a second hand ipod with ubuntu. banshee no longer works and while rhythmbox sees tunes of ipod, and i can delete songs, they still appear on ipod. 

i followed these instructions for syncing ipod to ubuntu and now problem has gone away. i can open synamptic and install new software. strange.,

[http://syncing-ipod-ubuntu.articles.r-tt.com/](http://syncing-ipod-ubuntu.articles.r-tt.com/)

sudo add-apt-repository ppa:pmcenery/ppa

Next, type:

sudo apt-get update

And then:

sudo apt-get dist-upgrade

so that solved - so now to get banshee working again and ipod working without causing another problem :)

thanks for your efforts.

---

