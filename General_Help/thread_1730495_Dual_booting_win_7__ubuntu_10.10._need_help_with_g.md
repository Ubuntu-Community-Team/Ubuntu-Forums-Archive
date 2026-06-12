---
title: "Dual booting win 7 / ubuntu 10.10. need help with grub boot text."
date: 2011-04-16
forum: General Help
---

### Post by PandaMonix on 2011-04-16
hey guys.

I have dul booted ubuntu 10.10 and windows 7.
windows 7 came with my laptop.

i installed 10.10 with wubi.

i now get on my grub menu

-ubuntu 10.10
-ubuntu 10.10-safe mode
-ubuntu 10.10 (random numbers)
-ubuntu 10.10 (rando numbers) safe mode
-win 7
-win 7



id really like it just to say

ubuntu 10.10
ubuntu 10.10 -safe mode
windows 7



is there any way i can remove things from the grub menu, and edit the text??

thanks for listening guys, i appreciate it!

---

### Post by Rubi1200 on 2011-04-16
Probably the easiest method to clean up the menu is to use Grub Customizer:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

But, here's the rub: I don't know if this works with Wubi installs since GRUB is assumed to be installed to the MBR of the drive. In the case of Wubi installs, this is not so; it uses the Windows bootloader to do its thing.

Let me get some more information and post back when I have a more definitive answer for you.

Or, perhaps, someone will come along with other suggestions.

---

### Post by drs305 on 2011-04-16
**[COLOR="DarkRed"]Update:[/COLOR]** See next post.

**Stop the Presses!**

I originally told Rubi1200 that I thought Grub Customizer would probably work on a Wubi install. However, I just did a preliminary test by installing and making some minor changes. 

At the moment I'm having problems booting back into Wubi, so please hold off until you either get further confirmation that GC works in Wubi or I can sort out what's happening on my system. 

**Added:**

I hadn't run Wubi in a long time and updated all the packages, so I can't be sure if the problem was with GC or something else. My guess it's the Wubi update rather than GC, but let's be sure before we go messing up your system.

---

### Post by drs305 on 2011-04-16
Ok, it *was* the standard problem with Wubi updates. Once fixed using *Rubi1200's* Wubi Megathread instructions, Wubi is working properly.

Grub Customizer appears to work fine within Wubi.

---

### Post by Rubi1200 on 2011-04-16
Thanks drs305 for sharing this information with us about GC and Wubi installs. I am sure users will find this tool useful.

---

### Post by PandaMonix on 2011-04-19
Legends!

thanks for that. ill look into it in a few minutes. ill post back with my outcome.

thanks heaps. =]

---

