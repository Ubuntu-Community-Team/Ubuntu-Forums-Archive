---
title: "running slow"
date: 2010-04-03
forum: General Help
---

### Post by Andreei on 2010-04-03
I now have the beta 10.04 installed. I had 9.10 an 8.10, but from 8.10 the all the versions have been running a lot slower on my computer.I am referring to normal usage.For example viewing webpages in mozilla and listening to music on rythmbox did not run smoothly the music kept stopping every 10-15 sec etc. usually because the processor kept peeking at 100% freezing everything. I set the graphics details at none but no major improvement.Any advice ? I have a amd athlon64 1800+ // 512 ram // 256 mb ati radeon video card.

---

### Post by chessnerd on 2010-04-03
Cut features, cut processes, cut software, cut wages. Well, maybe not the last one, but you get the idea.

First, under System>Preferences>Startup Applications cut out anything that you don't need (like Bluetooth support), the same goes for Services. Then, go into Synaptic and start digging around. For instance, I doubt your machine has Bluetooth, so you can cut out bluez and gnome-bluetooth. If you don't use Evolution, you can try to cut that out and save some system resources. Same goes for Empathy.

If you don't want to use Synaptic, you can do the same thing in the Ubuntu Software Center, but you won't have as much direct control over what you are getting rid of.

I always enjoy a good software gutting. I see it as a refreshing type of spring cleaning for your Linux install, but your experience may vary. ;)

If, however, this does not work, or you don't feel like digging around in your system that much, you can also consider moving to Xubuntu or Lubuntu. They both use lighter desktop environments and so should run better on your hardware. Xubuntu is similar to Ubuntu in terms of appearance and Lubuntu is the most lightweight of the three.

---

### Post by nem75 on 2010-04-03
Andreei, you might want to find out what exactly goes wrong first. Use System Monitor and related tools to see which processes eat CPU time when it's at 100%. Monitor the memory and swap space usage to find out what slows your system down and which processes are responsible. From looking at your specs I wouldn't say that you don't have enough RAM, but 512 MB sure is not much these days. Even Ubuntu won't scale to an unchanged hardware base forever.

Bottom line: find out what's really going on. :)

---

### Post by Andreei on 2010-04-03
grrr..i can't now, not blaming *chessnerd but the uninstalling tip is not for nabs like me. i managed to f up ubuntu and now it won't start up (which is weird because i did a normal restart after uninstalling) it stops at the loading screen and the terminal shows in the corner but it doesn't do anything.

---

### Post by chessnerd on 2010-04-03
> **Andreei said:**
> grrr..i can't now, not blaming *chessnerd but the uninstalling tip is not for nabs like me. i managed to f up ubuntu and now it won't start up (which is weird because i did a normal restart after uninstalling) it stops at the loading screen and the terminal shows in the corner but it doesn't do anything.

Hmmm... Okay, well try installing the "ubuntu-desktop" package. That should put all the default software back on your system. So, from a terminal, do ```
sudo apt-get install ubuntu-desktop
``` and see if that fixes your problem.

Sorry about that. I should probably have advised more caution in my previous post. Cutting stuff out can sometimes have adverse effects if you don't know what everything is.

---

