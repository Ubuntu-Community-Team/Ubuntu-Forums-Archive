---
title: "Question about Modules ,loading and Alsa"
date: 2009-09-11
forum: General Help
---

### Post by jhardydj on 2009-09-11
I have finished an install of Ubuntu (9.04) and have been playing around with Alsa trying to get my USB sound device working.  Looking at a couple of different Alsa guides , I ended up confusing my self .  So , I have a couple questions about modules and loading.  

I understand the difference between insmod , rmmod , modprob and depmod.  What I don't get is how to find the modules that are built and ready to use that may not be loaded, modules that are loaded already (lsmod perhaps?)?  

Basically (as hinted above) I am trying to get sound working and I am having a tough time with Alsa.  Some docs say to load Alsa as a driver and not as a module option within the kernel and others say to have Alsa built as a module within the kernel. Your thoughts?

/proc/asound/cards, and modules both show my US122L (hw 1) .  Running strace on anything to do with alsa looks to be a mess.   mostly /dev/snd/<something here> is missing.  etc.. 

Any ideas?

Sorry, that was alot of questions!  Hopefully someone can shed some light.

Thanks in advance.

---

### Post by cariboo on 2009-09-11
This might not be any help, but all the modules are located in /lib/modules/<kernel version>.

Usb sound works for me using pulse audio, that is installed by default in 9.04.

---

### Post by jhardydj on 2009-09-11
What audio interface do you have?  Should i remove Alsa and try pulse instead?

---

