---
title: "Programs freezing, clicks don't register"
date: 2009-08-31
forum: General Help
---

### Post by earthwanderer on 2009-08-31
I installed Ubuntu 9.04 two months ago, and things were great until Thursday.  I was playing with the flash plug-ins, trying to make some content work on a website.  The website began working, but within an hour I had serious trouble with the computer.  

Programs freeze...sort of.  The mouse still moves, but most clicks don't register (wireless and touchpad, although the touchpad takes longer to stop working). I can click within a website, for example in a text box I can reposition the cursor, but I can't click on links.  I can usually navigate with the keyboard.  This occurs in my regular session and in the GNOME failsafe session (although it takes longer to occur there). Eventually nothing seems to work and I have to restart.

I reversed the changes I made to flash (removed adobe-flashplugin and flashplugin-nonfree-extrasound and reinstalled swfdec-mozilla) but the problem is still occuring.

I ran a memory test that didn't show any problems.

I use virtualbox to run XP for some programs I need for work.  I'm tempted to just try a fresh install of Ubuntu, but I'm not sure I can use my XP disc to install on virtualbox again. Any help or insight would be greatly appreciated.

---

### Post by _sluimers_ on 2009-08-31
Remove swfdec-mozilla and put back in adobe-flashplugin, unless you have a good reason not to.
swfdec is still in it's developmental stage, so adobe-flashplugin currently works better.

I doubt reinstalling Ubuntu as a whole would work unless you have upgraded, from one distro to another. That always seems to go wrong. Then a fresh install should help.

I suggest saving everything from /home/<your username>/.VirtualBox to a USB stick or external harddrive when you decide to do a fresh install. Put everything back after you've reinstalled Ubuntu and Virtualbox.

Hope this helps.

---

### Post by earthwanderer on 2009-08-31
Thank you for the information!  I went back to the adobe instead of swfdec-mozilla and things are slightly better.

Now, I can use the touchpad and the buttons work as long as I don't have the USB plugged in for the keyboard and mouse (I have a Microsoft 7000 desktop set).  When I do plug in the USB the keyboard continues to work, but the USB mouse stops clicking in Linux after a few minutes, and never clicks in virtual box (mounted or unmounted). Same with the trackpad, but it resumes normal function as soon as I remove the USB.

The USB mouse isn't really that big of a deal but I need the ergonomic keyboard and they are bundled together...

---

