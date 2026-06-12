---
title: "Can't run application in Wine"
date: 2011-01-17
forum: General Help
---

### Post by ~LoKe on 2011-01-17
I'm supposed to be starting an online course through OntarioLearn, and they provide software called "Embanet" which all the assignments are issued and turned in through.  Wine won't run the Windows XP version of the software.  There's also a Mac version but I'm not sure if it would be easier to get that working.

This is the error I get.  After which, the application doesn't start (but it runs in the background):

> wine fcc32.exe
err:dbghelp_msc:pe_load_debug_directory Got a page fault while loading symbols

I have the application set to run with Windows XP compatibility, but no luck.

I think my only option is to install Windows through VirtualBox/Qemu, but as I don't have a Windows install CD for this computer (only a 64bit CD, I need 32) I don't know if it'll be possible.

I have a 64bit processor (C2D T7250), but Ubuntu is installed as 32bit.  Will VB or Qemu accept my 64bit installation CD?

If so, what's my next step?  If not, do I have alternatives?

---

### Post by Mark Phelps on 2011-01-18
Given that MS Windows, combined with Apple OSs, comprise nearly 100% of the desktop PC community (Linux all combined is only a few percentage points), they probably feel they are doing their job in providing software that works for that nearly 100%.

And, as you have already discovered, Wine won't work (surprise!!).

Your only option at this point is the one you've already determined -- install virtualbox and then MS Windows inside it.  But, you need a legal copy of MS Windows to do that -- and if you don't have that, you won't be able to get any help in these forums.

One of the major downsides of using a Linux distro -- you're part of a very, very small minority.

---

