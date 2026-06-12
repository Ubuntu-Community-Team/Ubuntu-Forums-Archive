---
title: "Ubuntu live cd doesnt work or gives login screen"
date: 2010-07-25
forum: General Help
---

### Post by kurret on 2010-07-25
When I run my Ubuntu live cd (with quiet splash removed) i get the following error message.

```
[drm_fb_helper_panic] *ERROR* panic occurred, switching back to text console 
run-init: /sbin/init: I/O error
```

with quiet splash it just hangs.

So what I tried was that I checked acpi=off in options on F6 (i have no idea what i did). But then it works!! sort of..

I then get to a login screen, but I have no username or password (and the googled username and pw ubuntu and ubuntu/ubuntu doesnt work). SO im stuck at a login screen when I want to try ubuntu from CD without installing. How stupid isnt thath?

worth to mention is that Im doing this to access my old files on a windows computer that crashed sort of.

I have tried both 9.1 and 10.04

So if anyone can help me with the first error or have any working username and pw I would be very happy!

---

### Post by Rubi1200 on 2010-07-25
I think I read a similar post recently and the solution there was to download and burn the CD again. You might want to try that first.
 
As far as rescuing files from the computer, you can use any live distro for that (one of my personal favorites is Knoppix).

---

### Post by kurret on 2010-07-26
> **Rubi1200 said:**
> I think I read a similar post recently and the solution there was to download and burn the CD again. You might want to try that first.
 
As far as rescuing files from the computer, you can use any live distro for that (one of my personal favorites is Knoppix).

Thanks, but I have tried two CDs of two different version, ands its the same error on both. It hangs without acpi=off, and gives impossible login screen with acpi=off.

But i will check out Knoppix, thanks for the tip.

---

### Post by kurret on 2010-07-26
Hi again, I downloaded and tried Knoppix and it works fine! Thanks for that!

---

