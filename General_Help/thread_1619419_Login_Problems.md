---
title: "Login Problems"
date: 2010-11-11
forum: General Help
---

### Post by Hadesminion13 on 2010-11-11
I said "problems" because I can't really describe my problem with one word. It's not a straight-up freeze or crash, just... weird. First of all, I used Wubi to install Ubuntu, so now I'm running a dual boot (Vista 64-bit and Ubuntu 64-bit), and I have been for about a week now. I'm working towards becoming a PSP C Programmer, so I installed the PSPToolchain, OSLib, Toolchain Libraries, etc... That didn't give me any problems.

Scite, Armagetron, WINE, Ubuntu Tweak, Chromium Web Browser, and many other applications and packages installed without error (minus the fact that any game I boot via WINE and Armagetron are really laggy and/or lack graphic effects that are supposed to be there). When I went into Synaptics Package Manager I went to the Update All or whatever it's called. (It's an icon at the top.) After it downloaded and installed a few packages I closed out of it. I had closed Chromium earlier because I thought I saw it as an update.

Now, when I tried to re-open Chromium, it showed a tab that read "Starting Chromium Web Browser" or something similar. After a little delay, it disappeared/crashed out on me. I never saw the window. I tried to open up a few other applications, all the same. I clicked the power button on the top right because I was going to restart. Where restart normally is, it said Restart Required, so I clicked it and my computer shut down.

After I booted up my computer, I went to Ubuntu, chose the mode/version I wanted to boot it in, and it booted up like normal. When it finally displayed the fullscreen Ubuntu image (the purple-ish space-looking picture that's set as your background at default (I think)) and then played the bongo sound, I thought I'd be ready to go. To my surprise, the Logon as... box never popped up. I could still move my mouse, so my overall computer wasn't frozen. When I held the power button after waiting a bit to see if it'd end up popping up, a black screen with some text output flashed then disappeared, and it re-played the bongo sound, then re-loaded the Ubuntu fullscreen image...

I tried it again, same thing, except this time I continued to hold the power button. The second time it popped up it shortly disappeared and my computer was shut down. I tried re-booting Ubuntu and even tried the Recovery Menu. I used DKPG to fix the packages, tried cleaning space out, nothing.

Any Ideas? :confused:

---

### Post by coffee412 on 2010-11-11
Instead of installing thru windoze, do this - 

1. Boot windows and shrink its partition - leaving free space. 
2. Boot from the Ubuntu cd you downloaded and burned and install Ubuntu. 

Now you can dual boot. I just dont trust windows at all. Maybe its just me. But since its a new install I would do it this way. 

Just start over.

---

### Post by Hadesminion13 on 2010-11-11
I don't have any black CDs and can't really afford any right now :(
I've tried GEdit, but it kind of made be nervous, plus I can't run it from a CD, like I said, so it wouldn't let me resize my windows partition and it didn't look like my Linux partition was listed. Either way, Windows worked the first time I installed Ubuntu, I just wanted to make Ubuntu bigger without resizing partitions, so I uninstalled Ubunto and re-ran Wubi. I also heard that if you resize your Windows partition manually you have to do a ton of extra stuff just to get Windows back.

---

### Post by coffee412 on 2010-11-11
> **Hadesminion13 said:**
> I don't have any black CDs and can't really afford any right now :(
I've tried GEdit, but it kind of made be nervous, plus I can't run it from a CD, like I said, so it wouldn't let me resize my windows partition and it didn't look like my Linux partition was listed. Either way, Windows worked the first time I installed Ubuntu, I just wanted to make Ubuntu bigger without resizing partitions, so I uninstalled Ubunto and re-ran Wubi. I also heard that if you resize your Windows partition manually you have to do a ton of extra stuff just to get Windows back.

If you go into the administration area of windoze you can work right with the partition and shrink it. That will give you more free space. But then you get to do a bunch of moving of partitions and running grub-install again to get things done. 

You know, If you have a mem stick you can download and put Ubuntu on it and then install from there if you computer supports booting from it. Most new ones do.

---

### Post by Hadesminion13 on 2010-11-11
Well, I tried resizing the partition your way, then with "diskpart.exe" (a windows partition/volume manager). For some reason when I use the command "list disk" it says I have 0 B free. When I go to Start > Computer The size of my C: drive is 176 GB, and I have 40.9 GB free. Why when I try to shrink my main Windows partition does it say I don't have anything free?

---

