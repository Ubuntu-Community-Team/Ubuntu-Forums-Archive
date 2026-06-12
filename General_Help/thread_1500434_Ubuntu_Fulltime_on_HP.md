---
title: "Ubuntu Fulltime on HP"
date: 2010-06-03
forum: General Help
---

### Post by JLYap on 2010-06-03
Hi everyone. I'm not sure if I'm posting this in the right forum, so apologies if this thread is misplaced. 

I currently have an HP mini netbook. As some of you may know, Ubuntu comes 
pre-installed alongside Windows 7. What I would like to do is to run Ubuntu on this netbook fulltime and uninstall Windows 7. Can someone please advise me on how I may go about doing so or perhaps point me to some resources that may tell me how to do so? Thanks!

---

### Post by derekeverett on 2010-06-03
> **JLYap said:**
> Hi everyone. I'm not sure if I'm posting this in the right forum, so apologies if this thread is misplaced. 

I currently have an HP mini netbook. As some of you may know, Ubuntu comes 
pre-installed alongside Windows 7. What I would like to do is to run Ubuntu on this netbook fulltime and uninstall Windows 7. Can someone please advise me on how I may go about doing so or perhaps point me to some resources that may tell me how to do so? Thanks!

I apologize as this isn't a direct answer to your question..

But are you sure you want to do that? Windows comes in handy from time to time. I hope you have your recovery disk at least.

---

### Post by wojox on 2010-06-03
I would download a [LiveCD]("http://releases.ubuntu.com/9.10/") and burn it to a disk.

Then boot from the CD and use G-Parted to delete the windows partition and expand your ubuntu partition.

---

### Post by JLYap on 2010-06-03
Thank you for your responses. 

> **derekeverett said:**
> I apologize as this isn't a direct answer to your question..

But are you sure you want to do that? Windows comes in handy from time to time. I hope you have your recovery disk at least.

Yes I'm quite sure. I'm curious though, in what ways may Windows come in handy? Also, what do you mean that I have my recovery disk at least? Sorry for the noob question, I'm incredibly (and somewhat embarrassingly) new to this.

---

### Post by derekeverett on 2010-06-03
> **JLYap said:**
> 
Yes I'm quite sure. I'm curious though, in what ways may Windows come in handy? Also, what do you mean that I have my recovery disk at least? Sorry for the noob question, I'm incredibly (and somewhat embarrassingly) new to this.

Did your computer come with a DVD that will allow you to put Windows back on the machine? You may decide you need/want Windows at a later time.

There are many reasons to keep it around if you already have it. There are some web-sites that require IE. Sad but true. Also flash works way better in windows. Not to mention that you might come across some piece of software one day that you would like to run and it may be Windows only.

Myself, I can tell you that the sound card in my HP machine requires Windows if I want to use the input jack. It won't work with Ubuntu for audio recording.

I don't see an advantage to getting rid of Windows if you already have it. You can even mount your Windows volume inside of Ubuntu to have access to Windows files. That's what I've done and it works great.

---

### Post by tankjer on 2010-06-03
> **JLYap said:**
> Yes I'm quite sure. I'm curious though, in what ways may Windows come in handy? Also, what do you mean that I have my recovery disk at least?
I think that by recovery disk he meant Windows 7 install disk. Also some programs are available for Windows only, and though there's Wine under Linux to run them, there are no guarantees that they will work with 100% performance and stability as in Windows.

---

### Post by John Bean on 2010-06-03
> **JLYap said:**
> I'm curious though, in what ways may Windows come in handy?

Windows is better supported by hardware manufacturers, so for example some devices that work fine in Ubuntu once installed can only be setup initially using software that only runs on Windows or Mac. Been there, I recently had to use XP to install a cheap NAS whose (Linux!) OS had to be loaded using a Windows-only installer. Frustrating experience :-(

Plus of course the fact that unless you are prescient there's no way you can know you'll *never* need Windows and curse yourself for having thrown it away after paying for it when you bought the netbook...

I strongly recommend you keep it, "just in case".

---

### Post by aeiah on 2010-06-03
the boot loader may be on the windows partition, so if you do decide to remove the partition, make sure you get yourself a copy of the super grub disk (or super grub 2 disk, if you use grub2). you'll also want a copy of the gparted live usb (or livecd if you have an external cd drive) for removing the windows partition and resizing your ubuntu one.

if you want to play it safe, you could do a bit-for-bit copy of the whole drive (or at least of the windows partition) and then if things get borked you can restore it back to how it was before you removed windows. you'd need an external hard drive for that of course, and a liveusb like gparted, slitaz, crunchbang, ubuntu etc. the command you'd be using is dd. there are plenty examples on it's wikipedia page for copying partitions and hard drives.

---

### Post by JLYap on 2010-06-03
Thanks guys! Responses have been helpful. I may just keep windows for that matter but a few questions:

1. Does the presence of windows 'slow down' my use of Ubuntu? For me, it seems using linux on this netbook is pretty slow, and is the main reason that I want to delete windows (may not seem like a valid reason i know). The only thing I will be doing with this netbook is using software from Open Office and email. 

2. Also, forgive my ignorance,  I can't seem to 'save' anything on Ubuntu. I tried downloading Firefox and it just told me to insert a USB... any solutions to this?

Thanks! This community is amazing!

---

### Post by derekeverett on 2010-06-03
How is your Ubuntu installed? Do you have a dual boot configuration? 

I can't see anyway Windows can be slowing your Ubuntu down. If your computer has limited resources than I could see that slowing things down, but Windows would be affected by this more than Ubuntu would.

Are you running Ubuntu itself from a USB stick or a live CD? With a live CD you will be unable to save anything. I don't know much about booting from a USB stick. I know it can be done but I've never done it.

---

### Post by aeiah on 2010-06-03
im not sure what they did with your ubuntu install.. im guessing you not being able to save anything and it being slow are related. perhaps ubuntu is a 'livecd' sitting on an SDHC card or read-only partition somewhere? 

having windows on there won't particularly slow ubuntu down.

perhaps you can post the results of the terminal command
```

df -h

```

this may tell us whether you're using a live system or not. a live system would create a filesystem in ram which would make things slow and read-only.

stuff like tmpfs, /dev/loop0, aufs would suggest your ubuntu install is just a live system they've put on a partition or SDHC card

---

### Post by wojox on 2010-06-03
> **JLYap said:**
> Thanks guys! Responses have been helpful. I may just keep windows for that matter but a few questions:

1. Does the presence of windows 'slow down' my use of Ubuntu? For me, it seems using linux on this netbook is pretty slow, and is the main reason that I want to delete windows (may not seem like a valid reason i know). The only thing I will be doing with this netbook is using software from Open Office and email. 

2. Also, forgive my ignorance,  I can't seem to 'save' anything on Ubuntu. I tried downloading Firefox and it just told me to insert a USB... any solutions to this?

Thanks! This community is amazing!

1. Only if your using wubi

2. Firefox should already be installed. Do you have Admin privileges?

---

### Post by JLYap on 2010-06-03
Righto, feel a bit stupid. Didn't really have a pre-installed linux, just a “Mobile Internet Experience” version of Linux as I found out on this site: [http://the-gadgeteer.com/2009/03/17/hp-mini-1000-netbook-running-linux/](http://the-gadgeteer.com/2009/03/17/hp-mini-1000-netbook-running-linux/)

 Will be installing Ubuntu Netbook remix now through USB. In any case, thank you everyone for your help.

---

