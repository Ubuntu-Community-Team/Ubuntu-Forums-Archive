---
title: "which?"
date: 2011-03-28
forum: General Help
---

### Post by minas1 on 2011-03-28
Hello, I'm new to ubuntu.

I want to install ubuntu inside windows. My processor is 64 bit i5. When I selected the 64bit version it says amd64 (which I think is for amd processors). Should I download this or the 32 bit version?

Thank you.

---

### Post by TBABill on 2011-03-28
AMD64 is just the designation used for 64 bit and applies to Intel or AMD.
 
Download whichever you prefer. Both will work on your processor.

---

### Post by antaios256 on 2011-03-28
the amd64 is just the naming convention it will work fine for an intell chip set  (running ubuntu 10.10 amd64 on an i7 64bit)

---

### Post by Rubi1200 on 2011-03-28
> I want to install ubuntu **inside** windows.
If you mean Wubi, see here for more information:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by minas1 on 2011-03-28
Thanks for the replies.

I have installed the 64 bit version, but it can't find the network drivers (wired/wireless) of my laptop. Is there a place where I can find them?

---

### Post by Dutch70 on 2011-03-28
I think you should try ...System > admin > additional drivers

Are you sure you need drivers?

If that doesn't work, you'll have to give some more details. You should probably read this also.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by 3Miro on 2011-03-28
> **minas1 said:**
> Thanks for the replies.

I have installed the 64 bit version, but it can't find the network drivers (wired/wireless) of my laptop. Is there a place where I can find them?

First, check to see if the wired and/or wireless is already working. The Linux kernel ships with a ton of free drivers that usually work just fine. If this fails (i.e. you have no connection), then go to System -> Admin -> Additional drivers and see what is available.

---

### Post by minas1 on 2011-03-28
Hi, neither wireless nor wired is working.

I tried going to addition drivers as you suggested.

When I select it, a message appears:
**Downloading package index failed, please check your network status. Most drivers will be available.**

I press ok, and then it displays:
**Searching for available drivers...**

After 5 seconds, the window comes up:
**No proprietary drivers are in use on this system**

---

