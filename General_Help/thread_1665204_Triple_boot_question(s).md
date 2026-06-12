---
title: "Triple boot question(s)"
date: 2011-01-12
forum: General Help
---

### Post by Bucky Ball on 2011-01-12
Hi all,

A quick one. I have Win7 and Ubuntu 10.10 dual-booting on my Toshiba Satellite Pro L510. I'm wanting to add OpenSuse. 

Question 1: If I install OpenSuse, will grub2 automatically change to inlude all three OSs or do I need to tweak some?

Question 2: Anything in particular I should look out for? What holes have others commonly fallen into installing OpenSuse in a multi-boot?

Tnx in advance. ;)

---

### Post by wilee-nilee on 2011-01-12
I always use grub2, so I upgrade any OS to that. But I also have a quad boot that includes natty as the last install. I just put maverick back in charge of the boot, to avoid any instability in Natty the usual way from the set up I want to control=maverick.
sudo grub-install /dev/sda  
in this case my HD is sda you know this stuff though.

If open suse is grub-legacy I would either upgrade it to grub2, or just mnt the OS with grub2 and load its grub2 to the mbr, it should chainload grub-legacy.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

My set up is W7, maverick, linuxmint10, natty, the linux are all pretty identical, except the mint idles at a 150 Mib ram with a little easy tweaking.

---

### Post by garvinrick4 on 2011-01-12
When you install OpenSuse it uses the anaconda installer and grub-legacy so just choose
to not install any grub at all on install there is a checkmark to not install grub during installation process. 
Then boot into Ubuntu and sudo update-grub and will put OpenSuse
as menuentry and config file, not having grub-legacy around at all is 
just so much easier and has no use what so ever. Just my opinion on OpenSuse, Fedora installs with Ubuntu's grub2 as grub in use.
This is practical experience I have installs on my machine I am using now.

---

### Post by Bucky Ball on 2011-01-12
Tnx wilee and garvin for your input. This has helped a lot. After a long night I just got the chance to pop the OpenSuse CD in the drive and it's looking good and kinda familiar! I downloaded the Gnome deskotp version, not DVD so nothing radical!

Gonna clear some space and install, following rules of engagement you both have outlined. 

I like where you're comin' from garvin; don't install grub and then just 'sudo update-grub' in Ubuntu. That's working for me. 

Thanks again both and get back to you with my progress. ;)

---

### Post by Bucky Ball on 2011-01-15
Finally got there. Been a bit busy. I downloaded OpenSUSE Gnome desktop to try it out. I liked it so downloaded the DVD bells and whistles version and tried to install. Didn't like that so installed from the Gnome Desktop CD. Set up partitions and let it roll. No problem, except ... I fell asleep on the couch for five hours while it was installing! Consequently Garvinrick4, I completely missed the 'don't install grub' option! lol

When I woke up and checked the machine it was all good. Reboot and I'm looking at OpenSUSE's grub-legacy menu and, of course, no sign of my Ubuntu install. So, following the instructions from the link posted earlier, I rectified the situation and it was pretty simple. From this page:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

In a nutshell, it is basically three commands. I booted from a Ubuntu liveCD, opened a terminal and input the following:

```
sudo mount /dev/sda5 /mnt

```I knew my install was on sda5, obviously, but replace with your details. Then this:
```

sudo grub-install --root-directory=/mnt/ /dev/sda
```I originally had this as:

```
sudo grub-install --root-directory=/mnt/ /dev/***sda5***

```But that didn't work so I just left off the '5'. Rebooted and I'm looking at my familiar Ubuntu Grub2 list. Rockin'!

From there, one more command, easy as:

```
sudo update-grub
```Grub2 picked up the OpenSUSE install, added to the list, reboot and all my installs are there for me. Now triple booting Ubuntu 10.10, OpenSUSE 11.3, and Win7 with problem. :)

Didn't help my wireless probs any; OpenSUSE doesn't see my wireless card in Network Manager so probably need to install drivers and see how I go. I'll post in the OpenSUSE forum about that ...

Thanks for the help you two, much appreciated, and I hope my nutshell report helps others. ;)

---

### Post by Bucky Ball on 2011-01-16
Hmm. Spoke too soon. But I think I've figured what's happened.

When I tried to boot OpenSUSE I got this error:

> error: file not found.
error: you need to load the kernel first
Odd. So I just reinstalled OpenSUSE and this time I set to not load any grub. Rebooted and there is my grub2 Ubuntu list. That worked beautifully so now I have tried both suggestions so thanks again.

All working great, until ... I boot into OpenSUSE, playing around some, then get the updates of which there are many. Restart the machine, attempt to boot into OpenSUSE and, guess what:

> error: file not found.
error: you need to load the kernel firstI'm figuring the updates killed it and as the first thing I did when I installed the first time was get the updates I'm thinking that's what broke the boot in the first instance also. 

So, not sure how to fix this and not really appropriate forum so I'll try OpenSUSE forum.

Just wanted to update, thanks again.

[B]
** UPDATE to my update: [/B]No problem. After receiving the error messages after installing a second time I figured the kernel might have changed with the update so the OpenSUSE entry was pointing in the wrong direction or some-such. So I update-grub one more time in Ubuntu, reboot, boot into OpenSUSE and no problems. All good and all boot entries working. Not sure exactly why the old entry no longer worked but the new one does.

I tried both methods outlined here and the easiest it when you get to the partitioning section of the OpenSUSE install, just choose not to install a grub. Your Ubuntu grub2 will then still be in control when you reboot after the install and it's as simple as 'sudo update-grub'.

When you boot to OpenSUSE and update that, reboot into Ubuntu and 'update-grub' one more time. Easily fixed, at least in my case. 

;)

---

### Post by corrytonapple on 2011-01-17
Good to hear this!  I was going to do the same thing as you, but use KDE.  Would one have to do this every-time openSUSE updates its kernel?

---

### Post by Bucky Ball on 2011-01-17
> **corrytonapple said:**
> Good to hear this!  I was going to do the same thing as you, but use KDE.  Would one have to do this every-time openSUSE updates its kernel?

I would think so. Just make sure you don't install a grub when you are installing OpenSUSE KDE. :)

---

### Post by corrytonapple on 2011-01-17
I won't.  Don't worry, I have only messed up one Ubuntu install.  Kids, do not enter a Terminal command and then change your mind without reversing it or remembering the command that you entered. ;)

---

