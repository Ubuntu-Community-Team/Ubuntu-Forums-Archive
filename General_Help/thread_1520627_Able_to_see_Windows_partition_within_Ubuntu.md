---
title: "Able to see Windows partition within Ubuntu?"
date: 2010-06-29
forum: General Help
---

### Post by VinoFuriaRoja on 2010-06-29
Hey guys,  I have a question.  I am going to be installing Ubuntu 10.04 on to my girlfriend's computer (she played around with my computer and loved Ubuntu!) as a dual boot coming up in a few days.  She wants to be able to access her Windows partition from the HD within Ubuntu whenever she wants.  

So my question is if this is possible?  Is it a matter of just mounting the partition within gparted?  Within my Ubuntu on my computer, I can see my Windows partition as "13GB Filesystem" in PLACES, and then in gparted, I see it as a NTFS partition and mounted as "/media/etc.."  Take a look at the screenshot I added.  When I open up the 13GB Filesystem from within Ubuntu, I can see all the files that are Windows.  So again, how can I go about doing to this to make sure that it happens when I install Ubuntu (using the Wubi installer)?  Or should I use the LIVE CD and dual boot that way?  Let me know what you guys think.  

Mark

---

### Post by bcbc on 2010-06-29
I don't see a screen shot, but if you install with wubi then you can see the windows files under the /host directory.

If you do a normal dual boot, then you can either click on the drive under Places as you do, entering your password the first time to mount it, or set it up in /etc/fstab to mount automatically.

---

### Post by VinoFuriaRoja on 2010-06-29
I forgot to attach the screenshot.  Sorry.  I've attached it now.

---

### Post by techunit on 2010-06-29
> **VinoFuriaRoja said:**
> Hey guys,  I have a question.  I am going to be installing Ubuntu 10.04 on to my girlfriend's computer (she played around with my computer and loved Ubuntu!) as a dual boot coming up in a few days.  She wants to be able to access her Windows partition from the HD within Ubuntu whenever she wants.  

So my question is if this is possible?  Is it a matter of just mounting the partition within gparted?  Within my Ubuntu on my computer, I can see my Windows partition as "13GB Filesystem" in PLACES, and then in gparted, I see it as a NTFS partition and mounted as "/media/etc.."  Take a look at the screenshot I added.  When I open up the 13GB Filesystem from within Ubuntu, I can see all the files that are Windows.  So again, how can I go about doing to this to make sure that it happens when I install Ubuntu (using the Wubi installer)?  Or should I use the LIVE CD and dual boot that way?  Let me know what you guys think.  

Mark
Well if you want to access the windows partition from ubuntu go with a standard dual boot, but make sure that you don't use gparted or the installer to partition windows vista or windows 7 because it will cause errors that won't let windows boot untill you fix them

---

