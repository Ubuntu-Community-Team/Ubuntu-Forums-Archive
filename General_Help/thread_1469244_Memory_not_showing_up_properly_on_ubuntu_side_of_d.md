---
title: "Memory not showing up properly on ubuntu side of dual boot."
date: 2010-05-02
forum: General Help
---

### Post by Chiatroll on 2010-05-02
I just changed this computer to dual boot. Windows properly sees 8 gigs of ram. I put them in myself. I know they are good.

When I was checking the system monitor in ubuntu I noticed it only sees 3.2 gigs of ram. That is less then half.

I am on Lucid Lynx 10.04. It's setup for dual boot vista and ubuntu.

What information is needed to assist me?

---

### Post by lavinog on 2010-05-02
Is this a 64bit install or a 32bit install?

If you are using 32bit, you need to use the 32bit server kernel which should have PAE enabled.

---

### Post by WorMzy on 2010-05-02
I think you must have installed x86 Ubuntu, since my copy of x64 Ubuntu sees my 8GB of RAM fine. (Well, it sees it as 7.8GB, but close enough)

---

### Post by 3rdalbum on 2010-05-02
Windows 'sees' that amount of memory, but it can't use it unless it's a 64-bit version of Windows.

You can install the PAE (server) kernel on Linux, or 64-bit Ubuntu.

---

### Post by Chiatroll on 2010-05-02
> **3rdalbum said:**
> Windows 'sees' that amount of memory, but it can't use it unless it's a 64-bit version of Windows.

You can install the PAE (server) kernel on Linux, or 64-bit Ubuntu.

I know the windows version is 64 bit. How can I check my ubuntu version. Annoying if I put the wrong one on.

edit. nevermind I checked. I installed he 32 bit version. That feels a bit dumb. I may reinstall since I did just put it on.. but I always have to go threw so many hoops to get my WUSB600N linksys working when I first install.

---

### Post by dino99 on 2010-05-02
i've installed the "pae" kernel on my 32 bits system and all the ram is seen and used properly

---

### Post by lavinog on 2010-05-02
you should be able to install linux-generic-pae without having to do a reinstall.
But reinstalling with 64bit might be a better way to go anyway.

---

### Post by Chiatroll on 2010-05-02
> **lavinog said:**
> you should be able to install linux-generic-pae without having to do a reinstall.
But reinstalling with 64bit might be a better way to go anyway.

That was my logic. 64 bit will just be a better way to go overall even with all the pest.

---

### Post by lavinog on 2010-05-02
> **Chiatroll said:**
> That was my logic. 64 bit will just be a better way to go overall even with all the pest.

I think one thing that is still an issue with 64bit is Flash.  Adobe has a 64bit flash, but because it is in alpha status, it isn't in the repositories.  In the past the 32bit flash gets installed on a 64bit system, and has been very unreliable...the 64bit flash is much better.
There are many how to's on the forum on how to install it though.

I haven't updated my 64bit systems yet, so I could be wrong, and the alpha might be in the repositories now.

---

