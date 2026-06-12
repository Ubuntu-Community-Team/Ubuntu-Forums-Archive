---
title: "Installing Windows 95"
date: 2010-07-13
forum: General Help
---

### Post by Daniel Chaput on 2010-07-13
I have an industrial printer that can only be run from Windows 95 - the driver is only compatible with that, and the manufacturer went out of business before they updated it. I have a computer running Karmic Koala that I'm trying to downgrade to 95. (Sinful of me). I have a valid CD with 95 on it, but I can't figure out how to install it over Ubuntu. Help? 

Thanks

---

### Post by CowzRule on 2010-07-13
I would like to suggest you try to install Windows 95 into a virtual machine like VirtualBox and see if you can use the printer that way.

---

### Post by Rubi1200 on 2010-07-13
Alternatively,

why not consider dual-booting? 

Seems a shame to get rid of Ubuntu just because of a printer don't you think?

[https://help.ubuntu.com/community/DualBoot/Windows#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/DualBoot/Windows#Installing%20Windows%20After%20Ubuntu)

---

### Post by Daniel Chaput on 2010-07-13
Makes sense.  I'm trying to keep everything on that box as simple as possible; I won't be the one running it and I was hoping to keep the new one as close to the old one as possible. But if I can't get 95 installed, I'll go with that.
Thanks!

---

### Post by Jan Dahl on 2010-07-13
> **Daniel Chaput said:**
> I have an industrial printer that can only be run from Windows 95 - the driver is only compatible with that, and the manufacturer went out of business before they updated it. I have a computer running Karmic Koala that I'm trying to downgrade to 95. (Sinful of me). I have a valid CD with 95 on it, but I can't figure out how to install it over Ubuntu. Help? 

Thanks

Is it because Windows 95 does not know how to handle the disk partitioning? 

**DANGER WILL ROBINSON! THE BELOW WILL KILL THE DATA ON YOUR SYSTEM**

*In that case*, try booting from an Ubuntu Live CD, then start up in "I WANNA TRY" mode. Go to 'System' - 'Administration' - 'Disk Utility'.

Mark the drive in the 'Storage devices' list on the left, then click 'Format drive' - 'MBR/Master Boot Record'. After that, **** around with the partitioning you want (probably one big bucket by the sound of it).

Remember that you might want to fetch drivers for all devices and copying them onto a CD *before* you format the computer. Note that Windows 95 is not USB-friendly (but given the computer, that might not even be relevant :) )

Hope that helps :)

---

### Post by Jan Dahl on 2010-07-13
Ooh! Forgot to add the special sauce bit:

Format the partition(s) in FAT16 or FAT32. That's the whole point of the above excercise.

---

### Post by Jazzy_Jeff on 2010-07-13
There also might be problems with whatever processor you are using as well. They did not have multi core processors back then. Not sure if that would be an issue. Also the motherboard may not be able to handle 95 either. A lot of things might have issues. I know Windows 95 did not run most things without a driver disk for the whole system. Good luck to you.

---

### Post by Rubi1200 on 2010-07-13
> **Jan Dahl said:**
> Is it because Windows 95 does not know how to handle the disk partitioning? 

**DANGER WILL ROBINSON! THE BELOW WILL KILL THE DATA ON YOUR SYSTEM**

*In that case*, try booting from an Ubuntu Live CD, then start up in "I WANNA TRY" mode. Go to 'System' - 'Administration' - 'Disk Utility'.

Mark the drive in the 'Storage devices' list on the left, then click 'Format drive' - 'MBR/Master Boot Record'. After that, **** around with the partitioning you want (probably one big bucket by the sound of it).

Remember that you might want to fetch drivers for all devices and copying them onto a CD *before* you format the computer. Note that Windows 95 is not USB-friendly (but given the computer, that might not even be relevant :) )

Hope that helps :)

I think that using GParted is the better way to go when it comes to partitioning etc.

I also think there is no reason for the OP not to consider the dual-boot option.

---

### Post by Jan Dahl on 2010-07-13
> **Jazzy_Jeff said:**
> There also might be problems with whatever processor you are using as well. They did not have multi core processors back then. Not sure if that would be an issue. Also the motherboard may not be able to handle 95 either. A lot of things might have issues. I know Windows 95 did not run most things without a driver disk for the whole system. Good luck to you.

Very good points and you are probably right that Windows 95 would not run directly on modern hardware.

---

### Post by mlentink on 2010-07-13
> **CowzRule said:**
> I would like to suggest you try to install Windows 95 into a virtual machine like VirtualBox and see if you can use the printer that way.

+1

It would be a waste of hardware to install W95 on a machine. I remember running 95 on 486's or Pentium MMX's, so it should fly in a virtual machine with about 128 MB of memory.Especially to print...
And you'd have the rest of the machine to do useful things for you

---

### Post by robert shearer on 2010-07-13
I am curious now for I was under the impression that  most virtualisation environments would only run XP or later ??

If you do get 95 running this way please post how it went.
If anyone has links to getting 95 or 98 running in a virtual environment I would appreciate them.

---

### Post by Dustin2128 on 2010-07-13
> **robert shearer said:**
> i am curious now for i was under the impression that  most virtualisation environments would only run xp or later ??

If you do get 95 running this way please post how it went.
If anyone has links to getting 95 or 98 running in a virtual environment i would appreciate them.

:p

---

### Post by Jazzy_Jeff on 2010-07-13
Virtualization may be the only way to get it to work.

---

### Post by belkinsa on 2010-07-13
But you need to make a ISO image of your Windows 95 disk in order to install it on VB.

---

### Post by Dustin2128 on 2010-07-13
> **Mechafish said:**
> But you need to make a ISO image of your Windows 95 disk in order to install it on VB.
Hm, I've managed to install windows OSes to vbox without converting the disc image to an iso. Still, there are tools to do that easily on linux, shouldn't be too dificult. In fact, I think I've got a 95 disc lying around somewhere, I'll get back to you if I find it.

---

### Post by proggy on 2010-07-13
> **Jazzy_Jeff said:**
> There also might be problems with whatever processor you are using as well. They did not have multi core processors back then. Not sure if that would be an issue. Also the motherboard may not be able to handle 95 either. A lot of things might have issues. I know Windows 95 did not run most things without a driver disk for the whole system. Good luck to you.
true story , i tried it went crazy with all that ram and processing power , it booted then when it got to the desktop.......blue screen

---

### Post by robert shearer on 2010-07-14
> **Dustin2128 said:**
>  post   #12 :p

Yes looks do-able,  only from their site...
[http://www.virtualbox.org/wiki/Guest_OSes](http://www.virtualbox.org/wiki/Guest_OSes)

---

