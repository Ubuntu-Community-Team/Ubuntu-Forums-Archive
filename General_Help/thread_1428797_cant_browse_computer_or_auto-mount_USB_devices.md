---
title: "cant browse computer:/// or auto-mount USB devices"
date: 2010-03-13
forum: General Help
---

### Post by kaligus on 2010-03-13
I do not know these two are related but noticing them goes hand in hand so I will lump them together.

I normally have a windows USB drive hooked up to my machine day in and day out and periodically turn it on, reboot (for purely historical reasons) then make a back up from my local file system and 2 flash-SD drives and 1 flash-CF drive onto the windows drive.

The usual process is while the machine is off plug in flash#1 and turn the Windows drive on, boot, p)laces S)D drive ... then P)laces C)omputer U)SB drive copy files ... eject SD-1 and insert SD-2 automount pops up ... copy files repeat until done.

Recently (I noticed it last week but did not have the time to dig any) I need to hand mount all of the USB devices whether flash or hard drive... and I can not browse "computer:///" or "network:///"

Nautilus gives me an error 'Nautilus cannot handle "computer" locations' (or "network")

This possibly was broken when I updated my Nvidia drivers from the launchpad ppa to 195.x but I carefully went through the files uninstalled so that nvidia could be upgraded and reinstalled them.

I have since downgraded back to 190.x and disabled the PPA in my repository list as it caused other problems.

No other updates list anything *I* can imagine having an effect of nautilus.

I have also been trying without joy to compile a couple of things and have added a stack of libraries recently (as in since last time my backup worked "correctly").

What information can I provide to hepl figure out why my automounts have died and taken my network:/// and computer:/// with them?

---

