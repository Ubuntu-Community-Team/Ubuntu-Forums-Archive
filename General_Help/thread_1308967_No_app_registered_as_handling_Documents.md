---
title: "No app registered as handling Documents"
date: 2009-11-01
forum: General Help
---

### Post by camionbleu on 2009-11-01
I have just installed the 9.10 Netbook Remix on my Toshiba NB205. Everything was initially working fine, but now whenever I go to Files and Folders and click on any of the items (Documents, Music, Pictures, Videos, Downloads, Desktop, Local Disk), I get an error that says "Unable to open Documents (or 'Music, Pictures, etc)" and "No application is registered as handling this file".

The only change that I have made to the new installation is to install Thunderbird email (but I did not remove or in any way mess with Evolution).

This was a clean install, not an upgrade from a previous version of Ubuntu. At first, I wondered whether I had somehow lost Nautilus, but I can run it from the Alt-F2 window. I tried running sudo apt-get install nautilus, but apt-get simply reported that I already have the latest version of Nautilus installed.

I'm somewhat new to Ubuntu (have been running 9.04 for 2-3 months now) and this is the first time that I have installed the Netbook Remix. So this is probably just naive user error.

Can someone point me in the right direction, please? As this is an almost fresh installation could just reinstall Ubuntu. But I'd rather learn what I broke and how to fix it.

---

### Post by camionbleu on 2009-11-02
I found the solution to this, though I still have no idea how I broke it in the first place. I opened Nautilus (using Alt-F2), then navigated to my home directory and right-clicked on one of the folders that was causing a problem when I tried clicking on it in Files & Folders. In the context menu that popped up when I right-clicked, I chose "Open with Other Application...". In the Open With dialog, I clicked "Use a custom command", and entered the command: nautilus.

Doing this once for one of the folders fixed it for all of them. Now I can click on any of them in Files & Folders and they open OK.

I hope this is useful for someone else who might run into this problem.

---

