---
title: "Install windows from Lubuntu"
date: 2011-12-31
forum: General Help
---

### Post by mrbambocha on 2011-12-31
Hi.
Im totally new to linux. My HDD messed up so I had to install linux to be able to format my HDD. And its actually really good so far. Think Im gonna stick to it when I dont work. But when I do work, I need windows. So I wonder how do I partition/prepare the HDD right in lubuntu?  


**Also some basic questions:**
[LIST]
[*]Whats the best way to learn Linux? Is it to install ubuntu instead and download the free manual and start from there (if so, how can I run ubuntu side by side with Lubuntu?)? 

[*]How come there arent any viruses for Linux? Dont I need an firewall either? How about malwares from internet/cookies etc?


[/LIST]

---

### Post by Paqman on 2011-12-31
> **mrbambocha said:**
> So I wonder how do I partition/prepare the HDD right in lubuntu? 


You'll need to make a large free space on the drive. You can do that by booting into your LiveCD or USB (the one you installed from), launching the Partition Editor (Gparted), right click on your swap and "swapoff", then shrink your Ubuntu partition so that it leaves a large enough free space for Windows and format it NTFS. Then boot up into your Windows install disk, install it into that NTFS partition.

You'll then need to [restore the Grub bootloader]("https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu"), because Windows is rude and nukes it.

> 
[*]Whats the best way to learn Linux? Is it to install ubuntu instead and download the free manual and start from there (if so, how can I run ubuntu side by side with Lubuntu?)? 


Lubuntu is Ubuntu, it's just got a different desktop environment. Using Lubuntu will teach you anything about Linux that using regular Ubuntu will.

> 
[*]How come there arent any viruses for Linux?


Linux is mostly used on servers, for which viruses aren't the main threat. A lot of effort has been put into Linux security. Additionally, most distros use a very rapid and comprehensive system for patching vulnerabilities. This all adds up to Linux being a very small, hard to hit target for desktop malware.

> 
Dont I need an firewall either?


You already have a firewall built-in, it's just not turned on because the default setting on Ubuntu has no ports open, so there's nothing for a firewall to protect. If you install any servers you would want to enable the firewall and set it up.

If you're behind a router that will also be acting as a firewall.

> 
How about malwares from internet/cookies etc?


You're still 100% vulnerable to a range of attackes, such as social engineering and phishing. You'll need to be just as vigilant of those as you would on Windows or OS X.

---

### Post by Paddy Landau on 2011-12-31
In addition to what Paqman said, Lubuntu is the "light" version of Ubuntu; it runs well on old and low-spec computers. If you have a modern computer with at least 2Gb, you may prefer Ubuntu.

Also, because of what Windows does, you may find that it is easier to install Windows first (let it overwrite your Linux installation); then install Ubuntu (or Lubuntu), because the installation will give you the option of running it side-by-side with Windows.

You also have the option of installing WUBI, which is Ubuntu *inside* Windows (instead of side-by-side), but I don't recommend that long-term as WUBI can be unstable.

Linux, originally based on Unix, was designed from the bottom-up for high security and multiple users (it's actually possible for two users to sign into the same Linux box at the same time). That is why viruses and other malware have not gained ground in Linux -- you have to manually install malware for it to work! As you get used to Ubuntu more and more, you will come to understand and appreciate the security policies built in. If you follow the default security policies, you'll only get malware if you are careless.

---

### Post by mrbambocha on 2011-12-31
Thanks for the answers. I like the security that comes with linux.

> You'll then need to restore the Grub bootloader, because Windows is rude and nukes it. Will have to look into this. 


> Also, because of what Windows does, you may find that it is easier to install Windows first (let it overwrite your Linux installation); then install Ubuntu (or Lubuntu), because the installation will give you the option of running it side-by-side with Windows. Thats why my computer crashed. Did it and after that I couldnt boot or partion/format/repair my HDD from the CD either. What could have gone wrong? 


> In addition to what Paqman said, Lubuntu is the "light" version of Ubuntu; it runs well on old and low-spec computers. If you have a modern computer with at least 2Gb, you may prefer Ubuntu. Ive read a little bit about it, my computer isnt slow, (dual core and 4GB RAM), but I just wanted the fastest/lightest/userfriendly distr. I always run lightweight distr of windows aswell. Heard that GNOME and KDE isnt as fast as LXDE, and there where fever apps installed for Lubuntu. Would you still recomend me to go with Ubuntu? Open for any ideas since I would like to learn to use Linux.

Is this the best way to start learning ubuntu?: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)


Btw, I only need windows when I use holdem manager. If I could solve that in ubuntu I woudlnt even need Windows. Is that possible to solve trough wine (needs postgres sql)?

---

### Post by Paqman on 2011-12-31
> **mrbambocha said:**
> 
Would you still recomend me to go with Ubuntu?


You can install the regular Ubuntu desktop into Lubuntu by installing the package [ubuntu-desktop]("apt:ubuntu-desktop"). The log out, click the wee cog by your user name to switch between the LXDE or Unity desktop environments.

Linux is very modular, you can chop and change some quite big components very easily.

> 
Btw, I only need windows when I use holdem manager. If I could solve that in ubuntu I woudlnt even need Windows. Is that possible to solve trough wine (needs postgres sql)?

According to the Wine App DB it doesn't look good, but those are old results, so you never know. Another option would be a very stripped down Windows install in a VM. That would save having to reboot for just one app, and you've got more than enough grunt for virtualisation.

---

### Post by Paddy Landau on 2011-12-31
> **mrbambocha said:**
> Thats why my computer crashed. Did it and after that I couldnt boot or partion/format/repair my HDD from the CD either. What could have gone wrong?
Windows, I guess ;)
If you cannot reinstall from your Windows CD without Ubuntu, then you wouldn't be able to do so with Ubuntu.

> **mrbambocha said:**
> ... (dual core and 4GB RAM), but I just wanted the fastest/lightest/userfriendly distr.
4Gb is more than enough for Ubuntu. Compared to Windows, Ubuntu is already light; Lubuntu is made for computers with just 256Kb of RAM. In your case, I really would suggest Ubuntu. The latest version uses Unity, which is very user-friendly (despite some loud complaints on the forum), and most newbies love it. See my signature for Unity tutorials.

> **mrbambocha said:**
> Is this the best way to start learning ubuntu?: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
Well, the section that shows you how to install would be useful, but at 158 pages, it is probably too much to read. Linux is very easy; Apple's OS is based on Unix (as is Linux), and Ubuntu is also GUI. If you are used to Windows XP or 7, you won't have any problem using Linux.

As I say, see the Unity tutorials, which will take you perhaps 15 minutes, and you will be set to go.

Oh, and one thing that ex-Windows users often fall down on: installing, deinstalling and updating programs is way easier than in Windows. Perhaps read the section on installing programs in the manual.

> **mrbambocha said:**
> Btw, I only need windows when I use holdem manager. If I could solve that in ubuntu I woudlnt even need Windows. Is that possible to solve trough wine (needs postgres sql)?
Recommendation: Don't use Wine; use [PlayOnLinux]("apt:playonlinux") (it's in the repository). Wine is complicated to use, but PlayOnLinux is a front-end to Wine -- it hides the complexity for you. (I don't know how to use Wine, but I use it anyway by using PlayOnLinux.)

To find out if a package works with Wine (or PlayOnLinux), the first step is to go to the [Wine website]("http://www.winehq.org/"), click on its [App DB]("http://appdb.winehq.org/"), and search for the package. Holdem is not listed, which means that it hasn't been tested; therefore, the only way to find out whether or not it works is to try. Install it using PlayOnLinux and try.

Wine is imperfect, partly because Microsoft keeps part of its workings secret. You can either dual-boot Windows, or load Windows in a [virtual machine]("https://www.virtualbox.org/") within Ubuntu.

Loading Windows in a virtual machine will, of course, slow down your machine, but not by much if you have several cores and I would think at least 6Gb RAM. Virtual Box allows you to [run Windows programs seamlessly]("https://www.virtualbox.org/manual/ch04.html#seamlesswindows") within Ubuntu, should you choose; it's an option to consider.

---

### Post by mrbambocha on 2012-01-01
> "Loading Windows in a virtual machine will, of course, slow down your machine"
 Is there a guide on how to load  windows in a virtual machine?

---

### Post by grahammechanical on 2012-01-01
[https://www.virtualbox.org/wiki/Documentation]("https://www.virtualbox.org/wiki/Documentation")

Regards.

---

### Post by Paddy Landau on 2012-01-01
> **mrbambocha said:**
> Is there a guide on how to load  windows in a virtual machine?
See the manual that grahammechanical indicated.

First: it is helpful to use the latest version of Virtual Box, which (I believe) is not the one on the default repository. Go to the [VB download page for Linux]("https://www.virtualbox.org/wiki/Linux_Downloads"); scroll down to "Debian-based Linux distributions"; follow the instructions. Then, go to the [main download page]("https://www.virtualbox.org/wiki/Downloads"), download the "VirtualBox 4.1.8 Oracle VM VirtualBox Extension Pack", and follow the instructions.

Once it is installed correctly, VB will be automatically updated as required when you run your Update Manager, and VB will prompt you to automatically update the extension pack as required.

---

