---
title: "Help the noob."
date: 2009-10-07
forum: General Help
---

### Post by Niko P on 2009-10-07
How do I get to the boot menu? When my XP crashed, I installed Ubuntu, and boot menu worked normally. But  when I installed a couple of weeks ago that XP back, the boot menu disappeared. So, do I need grup repair or something to get that boot menu back? If I need, so how I do it?

Yeah, i know... I have **very** bad English. ](*,) But I hope at least someone understands what I mean.

---

### Post by J V on 2009-10-07
Windows doesn't like other operating systems... you will need to reinstall grub, I'm not sure how exactly you have to do this, but their website will have more info...

Always install ubuntu *after* your windows if you are dual booting...

---

### Post by tom.swartz07 on 2009-10-07
I understood you perfectly fine! haha.

Try this guide here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you have any questions after following the guide, post back. If everything works out, let us know here and mark the thread as solved! 

Thanks! Hope it helps!

---

### Post by tom.swartz07 on 2009-10-07
This Thread might be a little easier to follow:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mechro on 2009-10-07
You can repair Grub using the Ubuntu Live CD. Instructions here...

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tom.swartz07 on 2009-10-07
> **J V said:**
> 
Always install ubuntu *after* your windows if you are dual booting...

Not particularly - You simply have to restore GRUB, the bootloader.
Windows simply takes over the boot order when it installs.

---

### Post by Niko P on 2009-10-07
> **J V said:**
> Always install ubuntu *after* your windows if you are dual booting...Yeah, I know.  But this is a "mini-laptop", so there does not have disk drive in it. So I had to get external disk drive from somewhere. And when XP was crashed it crashed the boot menu too. And a lot of other stuff. It showed only a blue screen, and complained that something important file doesn't exist / or it is deleted. So I installed Ubuntu to examine why XP crashed at all. And surely that can almost guess that was a virus which did it. Now I've learned, don't download everything from the Internet. :D

---

### Post by Niko P on 2009-10-07
Umm, I don't have that live Ubuntu CD. #-o

---

### Post by mechro on 2009-10-07
> **Niko P said:**
> Umm, I don't have that live Ubuntu CD. #-o

How did you install Ubuntu? If it was from a CD, what edition of Ubuntu is it?

---

### Post by Niko P on 2009-10-07
> **mechro said:**
> How did you install Ubuntu? If it was from a CD, what edition of Ubuntu is it?
USB-memory stick. Forget that what i said.

[http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)
Could this help me?

---

### Post by mechro on 2009-10-07
> **Niko P said:**
> USB-memory stick. Forget that what i said.

[http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)
Could this help me?

USB-memory stick... You'll have to help me here. Does the stick only install Ubuntu or can it run a "Live" version of Ubuntu?

---

### Post by mechro on 2009-10-07
Wait a minute. If it's a mini-laptop with a flash drive, how many operating systems are you going to put on it? I would have thought it's only capable of one OS at a time.

If it's only one OS you only need one bootloader, Windows or Grub.

Install Windows, you'll get Windows bootloader.

Install Ubuntu, you'll get Grub.

---

### Post by mechro on 2009-10-07
... unless of course Ubuntu runs off the USB stick...

I'll get me coat. :-k

---

### Post by Niko P on 2009-10-18
> **mechro said:**
> How many operating systems are you going to put on it?
To my laptop? Two.

---

### Post by dan1973 on 2009-10-18
Am quite new to Linux and Ubuntu and consequently I have been doing a lot of experimenting with 2 operating systems sometimes 3, installing and uninstalling.

I can safely agree that the simplest way to do things is to:

1) Get hold of an Ubuntu live cd image
2) Run Ubuntu from th cd without installing it.
3) Run the partition editor
4) Use the partition editor to divide up your hard disk ready for your 2 os
5) Install whatever Windows you want into one of these
6) Install Ubuntu into the other.

The Ubuntu install will automatically detect Windows and give you a choice on startup which one you want to boot into.

All you need to do is get hold of the disks and external drive - good luck!

---

