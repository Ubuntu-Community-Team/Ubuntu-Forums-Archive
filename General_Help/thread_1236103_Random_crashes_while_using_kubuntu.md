---
title: "Random crashes while using kubuntu"
date: 2009-08-09
forum: General Help
---

### Post by Xomm on 2009-08-09
I'm switching to Kubuntu from Windows XP due to lack of reliable customer service from Microsoft.

So, I decided to put Kubuntu through it's paces, like, listening to music, composing text documents, web browsing, video watching, installing from update manager, the list goes on and on. 

(I am fully recounting my problems to provide as much info as possible.)

During the course of my testing, Kubuntu started crashing erratically. Sometimes it would crash while loading Pidgin. Sometimes while downloading software packages, listening to a song on Amarok, other times while innocently reading a wikipedia article on Konquerer. 

After powering off using the power button on the computer itself, because nothing would respond, Kubuntu would do the expected disk check.

After that, sometimes it would tell me to manually run fsck, sometimes not. 

The 'lifespan' of Kubuntu dwindled with each reboot, sometimes only lasting a minute before crashing once more.

I reinstalled Kubuntu, and it seemed to work fine, up until installing the package for a chess game, where the screen seemed off-color with a total freeze.  After rebooting, the screen was still off color, even to the point where the K menu's background was distorted.


I'm really stuck. I don't want to go back to Windows XP for everyday use, just for programs that aren't supported. But Kubuntu seems, to me, like the best Linux distro i've found. 

(I'm running Jaunty Jackalope.)

---

### Post by w00ly on 2009-08-22
I have the same issue as you here: [http://ubuntuforums.org/showthread.php?t=1246742](http://ubuntuforums.org/showthread.php?t=1246742)
What video card are you running? You said that it crashed while on wikipedia but were you downloading anything or were there any file transfers going? What about desktop effects?

---

### Post by Xomm on 2009-08-22
I've figured it out, but forgot to close the thread. 

It was probably because I'm using the ATi Radeon X1300 graphics card. (Which, as many of is know, along with it's driver, is very buggy when used with Jaunty)

Since then I've switched to Ubuntu/Gnome, I've had no crashes.

---

### Post by P4man on 2009-08-22
gnome and KDE share the same videodrivers and kernel (if you installed the same version). If the problem is solved, then thats good, but its sort of surprising, and it wouldn't point to a problem with the ati card.

Random freezes usually point to a kernel problem and can be hard to cure. Often its an acpi incompatibility or something with the apic and/or clocksource that requires some obscure kernel parameter to work. Should it happen again, report back and I can try to give you some things to try.

---

