---
title: "Ubuntu - hangs at boot screen, able to use virtual terminals"
date: 2011-03-05
forum: General Help
---

### Post by corrrnbread on 2011-03-05
I am aware there are many other similar topics, but I haven't found a working solution yet for me in any of them. Please help :oops:

About a month ago I did a clean install of Ubuntu 10.10 I was using Gnome at first with no problem, but (in a moment of insanity) I decided I wanted to use KDE. I installed the KDE packages side by side with my existing Gnome files. I thought it would probably cause some kind of conflict, but it seemed to be working fine so I just forgot about it lol. It would boot into a mutated version of KDE, but soon realized it was too buggy and I hated it. So instead of removing KDE I just forced it to start up into a GDM session... A terrible idea having both installed at once. Next time I booted, it went past Grub & got stuck at the Ubuntu loading screen. I rebooted and the same thing happened. A quick search refreshed my mind about virtual consoles so I have been using them ever since ](*,)

Next phase of my "mess": I have some free time so I've been trying many possible solutions, but still haven't had any success. Update manager told me that a new Alpha release of Natty was available so I upgraded, thinking that it would just fix some corrupted file or I don't know what. Still stuck at the same Ubuntu loading screen and I receive the "input not supported" message every time I reboot. Luckily, I can log into the virtual console without seeing the screen and am still able to start GDM for a desktop gui. 

I am using 64-bit 11.04 Natty with an AMD Phenom X4 9750, 3GB RAM, Kernel 2.6.38-5 (updated a few times within time span of this problem). I have since removed all remnants of KDE that I could find, but it has had no impact.

Anyone willing to help me sort this out? Thanks in advance! :)




[COLOR="Red"]Edit-Solved (kinda): It turned out that my PCIe graphics card was conflicting with my onboard graphics card. Then I removed the PCIe card so that I could boot with a proper display and I uninstalled/purged all of the nvidia* items. Reinstalled the latest nvidia driver. Then I disabled the onboard card in the bios, I did before awhile ago, but it must have changed itself back somehow? Then I popped the card back in & at least I can see stuff now. It still says input not supported during grub, but it goes away once Gnome starts. Probably could have been done without all of those steps, but I was trying to isolate the problem rather than do a bunch more crap all at once & make it worse.[/COLOR]

---

