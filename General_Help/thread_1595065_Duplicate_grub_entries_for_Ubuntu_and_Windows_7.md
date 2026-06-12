---
title: "Duplicate grub entries for Ubuntu and Windows 7"
date: 2010-10-12
forum: General Help
---

### Post by tshudyb on 2010-10-12
To start by saying that I am brand new to anything linux.

I just installed Ubuntu 10.10 32-bit to dual boot on my Windows 7 32-bit PC.  This last time that I booted my pc the grub looked like this:

Ubuntu, Linux 2.6.32-25-generic
Ubuntu, Linux 2.6.32-25-generic (recovery mode)
Ubuntu, Linux 2.6.32-24-generic
Ubuntu, Linux 2.6.32-24-generic (recovery mode)
Windows 7 (loader) (on/dev/sda1)
Windows 7 (loader) (on/dev/sda2)

From what I understand the duplicate for Ubuntu is just an updated Kernal, hence the -24 to -25.  What I didn't understand is why there is a duplicate for Windows 7 and what the sda1 and sda2 is?  Someone please explain.  When I first installed Ubuntu, there was only one listing for Ubuntu and one for Windows 7.

Also, I was wondering what you do to keep up with new kernals and remove old one's.  How do you keep the Kernals from piling up? I assume that when another Kernal becomes available, there will then be 3 Ubuntu listings in the grub. 


One last thing is I would like some suggestions for the best way of going about learning linux. (i.e. terminal commands)

---

### Post by Quackers on 2010-10-12
The 2 kernels is normal and it is recommended to have 2 in the menu for trouble-shooting purposes. You will get a new entry for every new kernel installed (and its recovery option as well).
The 2 options for Windows (sda1 and sda2) are probably your windows recovery partition and your actual windows partition. I would try booting with each one as sometimes they can be listed the wrong way round by grub. Then you will know which is which.
The extra kernels can be deleted by using ubuntu-tweak.

---

### Post by tshudyb on 2010-10-12
> **Quackers said:**
> The 2 kernels is normal and it is recommended to have 2 in the menu for trouble-shooting purposes. You will get a new entry for every new kernel installed (and its recovery option as well).
The 2 options for Windows (sda1 and sda2) are probably your windows recovery partition and your actual windows partition. I would try booting with each one as sometimes they can be listed the wrong way round by grub. Then you will know which is which.
The extra kernels can be deleted by using ubuntu-tweak.

What is ubuntu-tweak?

---

### Post by VMC on 2010-10-12
> **tshudyb said:**
> To start by saying that I am brand new to anything linux.

I just installed Ubuntu 10.10 32-bit to dual boot on my Windows 7 32-bit PC.  This last time that I booted my pc the grub looked like this:

Ubuntu, Linux 2.6.32-25-generic
Ubuntu, Linux 2.6.32-25-generic (recovery mode)
Ubuntu, Linux 2.6.32-24-generic
Ubuntu, Linux 2.6.32-24-generic (recovery mode)
Windows 7 (loader) (on/dev/sda1)
Windows 7 (loader) (on/dev/sda2)

From what I understand the duplicate for Ubuntu is just an updated Kernal, hence the -24 to -25.  What I didn't understand is why there is a duplicate for Windows 7 and what the sda1 and sda2 is?  Someone please explain.  When I first installed Ubuntu, there was only one listing for Ubuntu and one for Windows 7.

Also, I was wondering what you do to keep up with new kernals and remove old one's.  How do you keep the Kernals from piling up? I assume that when another Kernal becomes available, there will then be 3 Ubuntu listings in the grub. 


One last thing is I would like some suggestions for the best way of going about learning linux. (i.e. terminal commands)

Here is a [link]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/") that shows some linux terminal commands that will do what your asking. There are several ways to go about removing old kernels.

Usually its advisable to keep an extra old copy in case you have issues with the newest kernel.

The first several commands on the link is just displaying info only, so that part is harmless.

There use to be a GUI around that allowed you to remove old kernels. someone will magically appear to show you that one.

Regarding how to learn the CLI commands. Funny you should ask. I just read of a new book that is free to download. That info is found [here]("http://linuxcommand.org/tlcl.php").

---

### Post by Quackers on 2010-10-12
It is a useful program for tweaking all these things. It is available in System > Admin > Synaptic Package Manager (search for ubuntu-tweak, with the - in the middle)

---

### Post by Foxcow on 2010-10-27
I have the same problem with the dual Win7 entries.  This has never happened before any previous version of Grub or Ubuntu.

Anyone know how to remove the second entry?  I tried to boot from it and it doesn't work.

I also tried sudo grub-mkconfig and update-grub.


[IMG]http://i208.photobucket.com/albums/bb252/Foxcow/2-2.png[/IMG]

---

### Post by drs305 on 2010-10-27
> **Foxcow said:**
> I have the same problem with the dual Win7 entries.  This has never happened before any previous version of Grub or Ubuntu.

Anyone know how to remove the second entry?  I tried to boot from it and it doesn't work.

It's a bit geeky, but you can edit the /etc/grub.d/30_os-prober script to change or hide these entries (Section 4):
[ Grub 2 Title Tweaks Thread]("http://ubuntuforums.org/showthread.php?t=1287602")

The other option if you don't have additional OS's would be to create a 40_custom menu with your Windows entry and disable /etc/grub.d/30_os-prober entirely so it won't include the Windows entry as it currently displays.

Since this isn't your thread, if you have any questions about the instructions please post in that thread.

---

### Post by Foxcow on 2010-10-27
> **drs305 said:**
> It's a bit geeky, but you can edit the /etc/grub.d/30_os-prober script to change or hide these entries (Section 4):
[ Grub 2 Title Tweaks Thread]("http://ubuntuforums.org/showthread.php?t=1287602")

The other option if you don't have additional OS's would be to create a 40_custom menu with your Windows entry and disable /etc/grub.d/30_os-prober entirely so it won't include the Windows entry as it currently displays.

Since this isn't your thread, if you have any questions about the instructions please post in that thread.



Thank you.  I figured it was ok to ask since the original poster had the same question.

---

