---
title: "Cannot enable Desktop Effects"
date: 2009-09-21
forum: General Help
---

### Post by Dan09 on 2009-09-21
Hi everyone! First off, sorry I didn't post this "in the correct forum, but everytime I try to start a thread in "Desktop Effects and Customization" it says I dont have permission...?  Oh well!

So I just recently installed a fresh build of ubuntu onto my new laptop which has an ATI Radeon HD 3870 card, and I'm having some troble getting desktop effects running.

The GUI method simply says "cannot enable desktop effects" and running compiz via the terminal gives the following mess : ```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
```

Does anyone have any suggestions on what I should do?  Any help is greatly appreciated!  Thanks!

---

### Post by MegaLoler on 2009-09-21
I had this problem yesterday.  I installed the newest kernel and it fixed it.

---

### Post by Dan09 on 2009-09-21
> **MegaLoler said:**
> I had this problem yesterday.  I installed the newest kernel and it fixed it.

Forgive the newbish-ness, but how would I go about doing this?

Simply a "sudo apt-get uprgade" or something?

Or maybe [http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html](http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html) <---- this?

---

### Post by MegaLoler on 2009-09-21
I don't think that would work.  I'm trying to find the link to the page that showed me how to do it, I'm just having a little trouble, but I'll keep looking for it.

Edit: :\ I can't find it.  Hopefully someone else will be able to help you.  If I find it I will let you know.

---

### Post by Dan09 on 2009-09-27
Oh no worries!  Thanks for the attempt though! :]

---

