---
title: "VirtualBox question"
date: 2009-07-16
forum: General Help
---

### Post by OMRebel on 2009-07-16
I bought an iPhone recently, and want to get it working with XP running in a VM.  I have a VM of XP already using VirtualBox OSE, but OSE doesn't support USB devices.  So, I am going to remove that and install the closed source edition of VirtualBox - that way I can use my iPhone with iTunes.

My question is this - will the image I have created already of XP under the OSE version work with the close source version, or will I have to reinstall everything?

---

### Post by chriskin on 2009-07-16
mine worked on both, you will just have it so see it again
i mean create a new Xp virtual machine using the already used virtual disk

but doesn't OSE support usb as well?

---

### Post by GoldenSun on 2009-07-16
I just did same thing, ose -> closed.  Mine auto recognized the old vm.  It still booted and had no problems.

---

### Post by OMRebel on 2009-07-16
> **chriskin said:**
> mine worked on both, you will just have it so see it again
i mean create a new Xp virtual machine using the already used virtual disk

but doesn't OSE support usb as well?

From everything I've read, you can't use OSE for USB devices.  I could very well be mistaken, but it doesn't recognize any USB devices when I have tried using it.

---

### Post by tacantara on 2009-07-16
I had to uninstall VB the other day when the 3.0.2 update caused problems.  After I reinstalled 3.0, my virtual OSes (XP and Karmic Koala) were still there, and all settings were intact.  Although I can't say for certain, you should find the same result when un-installing OSE to upgrade.

When you download VB from the website (or via Synaptic, whichever you decide to do) make sure that you're getting 3.0, only because I haven't heard anything about 3.0.2 being debugged.

---

### Post by tacantara on 2009-07-16
> **OMRebel said:**
> From everything I've read, you can't use OSE for USB devices.  I could very well be mistaken, but it doesn't recognize any USB devices when I have tried using it.

You're right, OMRebel.  The USB support is not available in the OSE version.  Not only that, but with the "standard" version you get "Guest Additions" which allow you to run in seamless mode, and do a bunch of other things that will make the virtual user experience much more manageable.

---

