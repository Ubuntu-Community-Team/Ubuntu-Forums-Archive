---
title: "Natty has stopped booting"
date: 2011-06-21
forum: General Help
---

### Post by stopsatgreen on 2011-06-21
I've been using Natty since the week it launched and all was fine until recently when it began to stop booting about one time out of every ten. Now it's stopped booting entirely.

When I power on the machine I pass Grub ok, then the screen goes purple. At this point it used to then go black, then show the login screen, but now it just hangs on the purple screen and won't go further.

Sorry if I can't be more specific, I don't really know what's happening at this stage! Any help gratefully received.

---

### Post by keptang on 2011-06-22
Same issue here this morning, after Grub (which didn't have to see before), it just stops on a black screen with a cursor.

So some update must have broken the possibility to boot. :(

Booting in recovery mode, the result is the same.

---

### Post by Mark Phelps on 2011-06-22
Used to have a similar problem in 10.10 -- so much so, that I pretty much stopped using it.  PC would boot, GRUB menu would come up (because I have multiple OS's), I would choose 10.10, screen would go Purple, hard drive light would go out -- and the PC would sit there indefinitely with nothing apparent going on.

Was able to fix this by:
1) Going into the GRUB menu and selecting recovery mode -- which booted in text mode
2) Choosing the option to repair broken packages
3) Typing "startx" to launch the desktop
4) Doing a clean shutdown
5) Rebooting.

If you can't even get a text mode from selecting recovery mode, don't know what to tell you, sorry.

---

### Post by stopsatgreen on 2011-06-22
I've just managed to get in by booting in recovery mode and typing 'sudo gdm'. I took a look in Synaptic to see if there were any broken packages, but none were reported.

Any idea why GDM wouldn't start without my command?

---

### Post by varunendra on 2011-06-23
As keptang pointed out, he didn't use to see the grub screen before but now he does.

Have you guys had a kernel update that triggered this problem? Normally, the grub screen only shows up when there are multiple OS or kernels available to choose from. If so, try booting into the older kernel.

---

### Post by stopsatgreen on 2011-06-23
As I mentioned, my problem is *after* GRUB; I use GRUB as I have a Windows partition also. But I get through GRUB, then the screen goes purple, then stops. It may be related to GDM.

---

### Post by wildmanne39 on 2011-06-23
> **stopsatgreen said:**
> I've been using Natty since the week it launched and all was fine until recently when it began to stop booting about one time out of every ten. Now it's stopped booting entirely.

When I power on the machine I pass Grub ok, then the screen goes purple. At this point it used to then go black, then show the login screen, but now it just hangs on the purple screen and won't go further.

Sorry if I can't be more specific, I don't really know what's happening at this stage! Any help gratefully received.Hi, it is probably an update, mostly likely for your video card driver. I am going to give you a link on how to boot up so you can fix your problem.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by varunendra on 2011-06-23
> **stopsatgreen said:**
> As I mentioned, my problem is *after* GRUB; I use GRUB as I have a Windows partition also. But I get through GRUB, then the screen goes purple, then stops. It may be related to GDM.

Yes, I understand that. The kernel starts loading *after* the grub screen.

So "if" a newer kernel is causing the problem, then choosing the older one from the grub screen should work as before. Obviously it is not a fix, just a possible workaround till a permanent fix is released.

But of-course if there is no kernel update issue, then you don't need to bother with that suggestion :). Besides, a 'driver update' can also cause this trouble. In that case, try what wildmanne39 suggested.

---

### Post by aig787 on 2011-08-22
this happened to me and gdm was the problem. switching to kdm fixed it for me

---

