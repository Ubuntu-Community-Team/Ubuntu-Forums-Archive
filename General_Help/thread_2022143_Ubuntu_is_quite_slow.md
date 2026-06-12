---
title: "Ubuntu is quite slow"
date: 2012-07-10
forum: General Help
---

### Post by PrideRage on 2012-07-10
Hello Ubuntu Users.
I am new to the world of Ubuntu, but I'm getting used to it pretty fast.
Anyway, here's my issue:
Ubuntu seems to be slow. Dragging or resizing windows takes a few milliseconds (it's no more realtime). Also, when changing a Tab in Firefox it takes some time for Firefox to actually display the new tab, and I can't watch 1080p movies smoothly :(
Firefox was just an example, in almost every window this noticable delay is there.

Thanks in advance!

***Edit***: I have fixed this very annoying problem. However, the reason for the lag was very funny: Since Tune-up Utilities detected VMware Player as resource demanding, I chose to deactivate it. Now, every time I start the VMware Player, Tune-up has to reactivate it. Therefore it ran slow as hell. 
Anyway I want to thank everyone who has read and/or replied to this topic :)

---

### Post by lukeiamyourfather on 2012-07-10
> **PrideRage said:**
> 
I am running Ubuntu (32 Bit) in a Virtual Machine.


It doesn't have anything to do with Ubuntu, it has to do with the virtualization software. If you haven't yet enable hardware virtualization acceleration in the BIOS if your processor supports it and in the configuration for the virtual machine software. Someone more familiar with VMware products might have more in depth suggestions.

---

