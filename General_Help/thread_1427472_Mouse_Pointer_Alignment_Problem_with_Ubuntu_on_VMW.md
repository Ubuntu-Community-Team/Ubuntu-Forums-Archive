---
title: "Mouse Pointer Alignment Problem with Ubuntu on VMWare"
date: 2010-03-11
forum: General Help
---

### Post by krisdotca on 2010-03-11
Hi All,

This is my first post to the Ubuntu formus so I hope I'm putting this in the right place. I have a problem with a Ubuntu 9.10 Desktop instance that I created on VMWare Workstation 7.0.0b203739. The problem is that the mouse is not aligned properly - I have to have the mouse pointer a couple of inches below and to the right of where I want to click. And odder still is that this problem did not exist when I first set up the VM - it only appread between reboots of the VM.

Any assistnace anyone can offer would be greatly appreciated. 


Thanks,
Kris

---

### Post by cjhabs on 2010-03-11
> **krisdotca said:**
> Hi All,

This is my first post to the Ubuntu formus so I hope I'm putting this in the right place. I have a problem with a Ubuntu 9.10 Desktop instance that I created on VMWare Workstation 7.0.0b203739. The problem is that the mouse is not aligned properly - I have to have the mouse pointer a couple of inches below and to the right of where I want to click. And odder still is that this problem did not exist when I first set up the VM - it only appread between reboots of the VM.

Any assistnace anyone can offer would be greatly appreciated. 


Thanks,
Kris

Make sure that you are running the latest version of VMWare tools in the VM - this has drivers for various components including the mouse. I have seen many a quirk disappear once VMWare Tools are updated.

---

### Post by krisdotca on 2010-03-11
Thank you for the quick reply cjhabs. I just set up the VM yesterday so I assume that the VMWare tools is the latest version. Is there a way that I can check?

---

### Post by cjhabs on 2010-03-12
I certainly wouldn't assume that it is up to date - I have had to update it for every vm I have built.
How you tell is different depending upon the vm product you are using.
I believe that the drop down tab at the top of the screen has options to update your Vmtools. This must be done with the VM running.
Just update it and it will let you know if you are already running the latest version.

---

### Post by krisdotca on 2010-03-12
Ok, I uninstalled and reinstalled VMWare Tools with the same result. The mouse pointer is still off alignment. Is there anything I can do to reset the alignment?

---

### Post by bergonom on 2011-11-15
I'm having the same issue. Did you ever figure it out?

---

### Post by bergonom on 2011-11-15
I had this problem but I guess I just figured it out.

I went to "VMWare Fusion|Preferences" then under the
"General" tab I selected "Always optimize mouse for games"
under the "Gaming:" pull down menu.

Hopefully this helps someone.

---

### Post by Tetz95 on 2013-05-05
> **bergonom said:**
> I had this problem but I guess I just figured it out.

I went to "VMWare Fusion|Preferences" then under the
"General" tab I selected "Always optimize mouse for games"
under the "Gaming:" pull down menu.

Hopefully this helps someone.

For whoever is still looking to solve this problem.  This worked for me.  :)

---

### Post by oldos2er on 2013-05-06
Old thread closed, please don't bump old threads.

---

