---
title: "Live USB - Can you disable 'format' option?"
date: 2010-05-23
forum: General Help
---

### Post by Alexander D. Gray on 2010-05-23
Hello everyone,

I have a Live install of ubuntu 10.04 on a USB drive which is really handy. I've changed some things around so it's just how I like it.

However, if for example I'm using a computer running windows, and I plug this USB stick in, a popup appears asking me if I want to reformat the drive. I'd much rather not have this appear because an accidental misclick would make me have to do all the work of reinstalling/customizing my USB.

I know how to turn of the popup for a particular machine, but I was wondering if it's possible to deny permissions to format the USB if it's plugged into any computer. Best case scenario would be if you were to plug the usb into any computer and click 'format' you would get a message prompting for a password first (not the one for the computer, one relative to the USB) or something like that.

Anyone have any thoughts on whether this can be done?

Cheers.

---

### Post by garvinrick4 on 2010-05-23
In Windows does it pop up because it reads the USB drive as ext4 when it is mounting to a Windows envirment and cannot read it? If it is a fat format in a startupdisk creator then I
would find the setting in Windows and turn off USB mounting on install. It has been a while
so I do not remember all the Windows settings and where they are. But it is a GUI setting for sure.

---

### Post by JustinR on 2010-05-23
This might not be so efficient.

But you could resize your ubuntu partition and create a small FAT partition so windows recognizes the flash drive on startup, like maybe a small 1MB partition.

---

### Post by garvinrick4 on 2010-05-23
You know any which way around it, if it is a Live USB it is only to be booted of off.
If it has been installed as a /boot a / and a swap in ext4 it would be in the mbr and not need
to be inserted while in Windows. The more I thought about it the more something was not
correct here.

---

### Post by Alexander D. Gray on 2010-05-25
Hi all,

Thanks for the responses. You're right in that it's a boot USB drive, so no it shouldn't be inserted into a machine already running windows or something. 

The reason I wanted to turn this off is because I live in a house where multiple OSes are being used so often times someone will plug a mac formatted thing into a windows machine to have it not work, and vice versa, etc.

I wanted to avoid the accidental occurrence, say, of my mother seeing this USB stick, thinking it's nothing in particular, and then plugging it in and clicking 'okay' to the popup she neither takes a lot of time to read, or really understand.

So, short of writing 'do not reformat!' or something on it, I was wondering if there's a more tech savy way to pull it off. The idea of having a partition readable by anything is actually a really good idea, for if someone were to plug the drive in, all they'd see is a tiny partition instead of a format prompt. If this were to be done, is it possible to password protect the other partition, or something like that, from reformatting?

Thanks for the feedback.

Cheers.

---

### Post by garvinrick4 on 2010-05-26
> **Alexander D. Gray said:**
> Hi all,

Thanks for the responses. You're right in that it's a boot USB drive, so no it shouldn't be inserted into a machine already running windows or something. 

The reason I wanted to turn this off is because I live in a house where multiple OSes are being used so often times someone will plug a mac formatted thing into a windows machine to have it not work, and vice versa, etc.

I wanted to avoid the accidental occurrence, say, of my mother seeing this USB stick, thinking it's nothing in particular, and then plugging it in and clicking 'okay' to the popup she neither takes a lot of time to read, or really understand.

So, short of writing 'do not reformat!' or something on it, I was wondering if there's a more tech savy way to pull it off. The idea of having a partition readable by anything is actually a really good idea, for if someone were to plug the drive in, all they'd see is a tiny partition instead of a format prompt. If this were to be done, is it possible to password protect the other partition, or something like that, from reformatting?

Thanks for the feedback.

Cheers. I get it better now. Maybe a box with a note on it saying " Ma this is my stuff, do not touch." Just kidding do not do that it will make Ma have to look at it and you might get a smack for being a wise guy.  Hope you figure something out.

---

