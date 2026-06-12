---
title: "Ubuntu Server Edition"
date: 2011-11-08
forum: General Help
---

### Post by glennbates on 2011-11-08
I have been told that I should have installed the server edition of Ubuntu.  Can I "upgrade" to this without installing and/or reinstalling it?  What can I do?

---

### Post by lechien73 on 2011-11-08
As far as I know, the main differences between the desktop and server editions are that the GUI isn't installed by default, and server edition has a server-optimised kernel.

In terms of upgrading, I believe if you're running 64-bit edition, you can just upgrade the kernel to the server-optimised version by typing:

```
sudo apt-get install linux-image-3.0.0-12-server linux-headers-3.0.0-12-server
```

Grub should also update itself, but if not, then run:

```
sudo update-grub

```

Hope this helps - I'm presuming that you're running 11.10 :)

---

### Post by glennbates on 2011-11-08
> **lechien73 said:**
>  I'm presuming that you're running 11.10 :)
How do I know?  Was downloaded about a month ago and installed 4 days ago.

---

### Post by Slim Odds on 2011-11-08
> **glennbates said:**
> How do I know?  Was downloaded about a month ago and installed 4 days ago.

```
cat /etc/lsb-release
``` from a terminal window

Sounds like you're running 11.04

---

### Post by glennbates on 2011-11-08
> **Slim Odds said:**
> ```
cat /etc/lsb-release
``` from a terminal window

Sounds like you're running 11.04
Yes.  11.04

Thanks!

---

### Post by lechien73 on 2011-11-08
Ok, so if you're running 11.04, then try a different kernel:

```
sudo apt-get install linux-image-2.6.38-12-server linux-headers-2.6.38-12-server
```

Please could you post the output of:

```
uname -m
```

If it says x86_64, then you're running the 64-bit edition.

---

### Post by glennbates on 2011-11-08
> **lechien73 said:**
> Please could you post the output of:

```
uname -m
```If it says x86_64, then you're running the 64-bit edition.
i686

---

### Post by glennbates on 2011-11-08
I'm still trying to get these copied.  What do I need to do?

---

### Post by lechien73 on 2011-11-08
Ok, so you have the 32-bit edition of Ubuntu installed. As far as I'm aware, the server-optimised kernel only works with the 64-bit edition. If you want the 64-bit edition, then you're better off downloading it and re-installing from scratch.

To check if your CPU supports the 64-bit edition, you could post the output of:

```
cat /proc/cpuinfo
```

---

### Post by glennbates on 2011-11-08
It has

clflush size : 64
cash_alignment :64

---

### Post by lechien73 on 2011-11-08
Thanks, but what I was really looking for was the "flags" - it has all the obscure codes, like fpu, acpi, mmx, fxsr etc.

---

### Post by glennbates on 2011-11-08
> **lechien73 said:**
> Thanks, but what I was really looking for was the "flags" - it has all the obscure codes, like fpu, acpi, mmx, fxsr etc.
flags : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constan_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave lahf_lm arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid


I hope after all that typing, that is what you wanted.:confused:

---

### Post by lechien73 on 2011-11-08
It certainly is. The "lm" flag indicates that your processor would support the 64-bit edition of Ubuntu.

If you wanted to install 64-bit server edition, then I'd recommend downloading the server edition from [here]("http://mirror.sov.uk.goscomb.net/ubuntu-releases/11.10/ubuntu-11.10-server-amd64.iso"), and then completely reinstalling.

If you were already running 64-bit desktop, then you'd have been able to upgrade easily, but since you're running 32-bit then this is the best way.

---

### Post by glennbates on 2011-11-09
> **lechien73 said:**
> Ok, so you have the 32-bit edition of Ubuntu installed. As far as I'm aware, the server-optimised kernel only works with the 64-bit edition. If you want the 64-bit edition, then you're better off downloading it and re-installing from scratch.
 
To check if your CPU supports the 64-bit edition, you could post the output of:
 
```
cat /proc/cpuinfo
```
Where do I find the server edition?

---

### Post by glennbates on 2011-11-10
I am downloading this now.  Do I need to unstall it before I reinstall it?  I have my hd partitioned for dual boot.

---

### Post by 1clue on 2011-11-10
Just reinstall onto the same partition.  I personally would also erase the partition during that segment of the install, but it's not strictly necessary.

---

### Post by glennbates on 2011-11-10
Thanks

---

### Post by 1clue on 2011-11-10
Just a word of advice since you seem relatively new at this.

Learn what is really important to you.  For me, for example, it's my email addresses, my web browser bookmarks and my email content in that order that I Really Don't Want to Lose.  There's a bunch of files that are good to keep too, but those generally are expendable.

Put EVERYTHING you need in one place.  By default that's $HOME.  Don't fight that.  If you suddenly can't boot anymore, focus on grabbing your stuff and getting it out of there.  There may come a point when you decide not to do that.  I don't do it that way anymore, but I have very limited places where I put "my" files.  Mostly I have an XFS partition that I use for ISO images, VMware and such.

Anything that constitutes software can be reinstalled, and generally it's easier to reinstall it than it is to try and recover it.

Don't be afraid of a reinstall.  Think of it as an opportunity to try doing things a different way, a fresh start.  I prefer a clean start over an upgrade or downgrade.

Get a removable drive.  My current system has a drive slot where I can stick in a bare SATA drive as though it were a tape cartridge.  Every so often I plug it in and drag my critical files onto it, then unplug it.

I've gone through all sorts of money and time on backups.  I used a tape drive way back in the day, religiously made backups for years and then at one unfortunate point I discovered that my tape drive couldn't read the tapes it wrote.  None of them.  I've sworn off any archival system other than a bare copy onto a removable drive now.  That's insanely easy and really reliable too.

---

### Post by glennbates on 2011-11-11
Trying to delete this message.  Can't find the delete option when I go into edit.

---

### Post by glennbates on 2011-11-11
> **1clue said:**
> Just a word of advice since you seem relatively new at this.
 
Learn what is really important to you. For me, for example, it's my email addresses, my web browser bookmarks and my email content in that order that I Really Don't Want to Lose. There's a bunch of files that are good to keep too, but those generally are expendable.
 
Put EVERYTHING you need in one place. By default that's $HOME. Don't fight that. If you suddenly can't boot anymore, focus on grabbing your stuff and getting it out of there. There may come a point when you decide not to do that. I don't do it that way anymore, but I have very limited places where I put "my" files. Mostly I have an XFS partition that I use for ISO images, VMware and such.
 
Anything that constitutes software can be reinstalled, and generally it's easier to reinstall it than it is to try and recover it.
 
Don't be afraid of a reinstall. Think of it as an opportunity to try doing things a different way, a fresh start. I prefer a clean start over an upgrade or downgrade.
 
Get a removable drive. My current system has a drive slot where I can stick in a bare SATA drive as though it were a tape cartridge. Every so often I plug it in and drag my critical files onto it, then unplug it.
 
I've gone through all sorts of money and time on backups. I used a tape drive way back in the day, religiously made backups for years and then at one unfortunate point I discovered that my tape drive couldn't read the tapes it wrote. None of them. I've sworn off any archival system other than a bare copy onto a removable drive now. That's insanely easy and really reliable too.
 Thanks for the advice.  This is a brand new computer and has nothing saved on it that cant' be reinstalled.

---

### Post by glennbates on 2011-11-11
I have tried twice to reinstall but it keeps booting the old one. How do I uninstall. Keep in mind, I have a dual boot.

---

### Post by 1clue on 2011-11-11
I'm sorry I won't be much help on that one.  I haven't dual booted for almost 10 years.

---

### Post by Slim Odds on 2011-11-11
> **glennbates said:**
> I have tried twice to reinstall but it keeps booting the old one. How do I uninstall. Keep in mind, I have a dual boot.

If this is a "new computer", why don't you install by wiping out the entire hard drive?

---

### Post by glennbates on 2011-11-11
> **Slim Odds said:**
> If this is a "new computer", why don't you install by wiping out the entire hard drive?
For now, I want to keep Windows on it.

---

### Post by 1clue on 2011-11-11
How accessible does Windows need to be?

For my girlfriend's laptop, I bought a second hard drive (make sure it's SATA) and swapped drives for the Linux install.  I also got a USB3 enclosure for the old drive.  That way I could do absolutely anything to the drive that was inside the laptop, and had a guaranteed rollback mechanism just by switching drives again.

---

### Post by Slim Odds on 2011-11-11
> **glennbates said:**
> For now, I want to keep Windows on it.

Then just install the new Ubuntu where the old Ubuntu was. Make sure that you select the **correct partitions** and format them during the install.

---

### Post by glennbates on 2011-11-11
> **Slim Odds said:**
> Then just install the new Ubuntu where the old Ubuntu was. Make sure that you select the **correct partitions** and format them during the install.
 I've tried but I can't seem to get it to overwrite the old one.

---

### Post by Slim Odds on 2011-11-11
> **glennbates said:**
> I've tried but I can't seem to get it to overwrite the old one.

We're going to need a lot more details.....

---

### Post by glennbates on 2011-11-11
> **Slim Odds said:**
> We're going to need a lot more details.....
 I installed 11.04 then updated to 11.10.  I didn't like it and I wanted to install the server edition.  I keep trying to install over the old one but the old one keeps booting up after a seemingly successful install.

---

### Post by 1clue on 2011-11-11
Can you still boot to the windows partition?

I can think of 2 things it might be:

First, you highlighted the partition but didn't actually select it somehow.  This is a tough one for me because I generally leave the installer at this point and do my own thing with the command line.

Second, somehow your boot loader is not configured properly.

If you want, boot off the CD and right after you choose your language and keyboard, type control+alt+F1.  You'll get a root terminal.  Then type fdisk /dev/sda, you should get your hard drive.  Type 'p' and you should get your partition list.  Then type 'd' and select the partition number which contains your Ubuntu session, and finally 'w' to save the changes.

After that, hunt through the screens using control+alt+F# until you find the GUI session again.

---

### Post by glennbates on 2011-11-12
> **1clue said:**
> Can you still boot to the windows partition?Yes
 
 
> I can think of 2 things it might be:
 
First, you highlighted the partition but didn't actually select it somehow. This is a tough one for me because I generally leave the installer at this point and do my own thing with the command line.I dont' think it gave me an option. I just had to enter the size of the partition.
 
 
> Second, somehow your boot loader is not configured properly.
 
If you want, boot off the CD and right after you choose your language and keyboard, type control+alt+F1. You'll get a root terminal. Then type fdisk /dev/sda, you should get your hard drive. Type 'p' and you should get your partition list. Then type 'd' and select the partition number which contains your Ubuntu session, and finally 'w' to save the changes.
 
After that, hunt through the screens using control+alt+F# until you find the GUI session again.
I'll give it a try.

---

### Post by glennbates on 2011-11-13
I figured out what the problem is.  I had an external hard drive hooked up to my computer and I was formatting a partition of it.  Now I need to go back and try again without the external being pluged in.

---

### Post by glennbates on 2011-11-13
This gets worse every time I try.

---

