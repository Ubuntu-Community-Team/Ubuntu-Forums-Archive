---
title: "Install from a USB stick?"
date: 2010-03-29
forum: General Help
---

### Post by Cityscape on 2010-03-29
I have a Ubuntu Live CD. I want to install Ubuntu on a PC with no CD drive. Is it possible to copy the contents of my Ubuntu CD to a USB stick and install from that? Will it work that way?

---

### Post by nemilar on 2010-03-29
You can't directly copy the ISO to the USB stick, but you might consider trying UNetBootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Good luck!

---

### Post by readycarpenter on 2010-03-29
yes if you download the iso and burn it to a cd, you can create a bootable usb from windows with the cd, or you could mount the iso with d-tools and not have to burn it.

or if you have a running ubuntu box you can create a usb directly from the iso via >system>admin>USB startup disk creator 

cheers

---

### Post by Cityscape on 2010-03-29
> **readycarpenter said:**
> yes if you download the iso and burn it to a cd, you can create a bootable usb from windows with the cd, or you could mount the iso with d-tools and not have to burn it.

or if you have a running ubuntu box you can create a usb directly from the iso via >system>admin>USB startup disk creator 

cheers
So how would I go about doing it? I don't want a recovery usb, I want to install from USB.

---

### Post by Cityscape on 2010-03-29
If I use UNetBootin, will i be able to install Ubuntu from it?

---

### Post by wilee-nilee on 2010-03-30
> **Cityscape said:**
> If I use UNetBootin, will i be able to install Ubuntu from it?

Yes, unetbootin can download and install altogether, if you look at the gui you will see this. You can also download the iso of a live cd or alternative both will install and load the thumb with unetbootin.

So do you want to do a dual boot or install in windows with wubi?

Unetbootin has no persistent, but the Ubuntu disc creator does.

---

### Post by Cityscape on 2010-03-30
> **wilee-nilee said:**
> Yes, unetbootin can download and install altogether, if you look at the gui you will see this. You can also download the iso of a live cd or alternative both will install and load the thumb with unetbootin.

So do you want to do a dual boot or install in windows with wubi?

Unetbootin has no persistent, but the Ubuntu disc creator does.

I don't really understand. ???
I want a flash drive that does the samething as a live cd (which is run and install Ubuntu). Can unetbootin do this?

---

### Post by wilee-nilee on 2010-03-30
> **Cityscape said:**
> I don't really understand. ???
I want a flash drive that does the samething as a live cd (which is run and install Ubuntu). Can unetbootin do this?

Yes unetbootin just copies the cd (ISO) in a bootable format to the thumb. 

Persistent means that the thumb would have a memory partition called casper-rw that would retain updates and additions. This persistent thumb would only install the ISO though. The interesting thing though is that you can remove the disc creators 4 gig limit of persistent and make your own partition much larger if needed.

Do you have a problem with downloading a new ISO so this will work, or are you still trying to use the CD?

---

### Post by sgosnell on 2010-03-30
Yes, unetbootin will do that, make a LiveCD version on a USB drive.  That's what it was designed to do.  It runs under Windows, but there is also a Linux version, FWIW.  If you have access to a computer running Ubuntu, you can create the USB version directly, but if not Unetbootin is a good way to go.

---

### Post by Cityscape on 2010-03-30
Thanks guys :) Unetbootin worked great.

---

