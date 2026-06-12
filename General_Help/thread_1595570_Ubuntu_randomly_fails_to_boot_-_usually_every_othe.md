---
title: "Ubuntu randomly fails to boot - usually every other time."
date: 2010-10-13
forum: General Help
---

### Post by bergqvistjl on 2010-10-13
Hi I have a very weird problem (which has also been happening since 10.04 as well, although I've done a complete re-format and re-install to 10.10 and its still happening)

Basically, roughly every other time (or sometimes it does it two times in a row) Ubuntu fails to boot. What happens is it hangs on the boot screen, if I press escape before-hand to view the text info, the last indication I get is that the fsck has run sucessfully on the drive. Any ideas? When i say hang i mean, no HDD activity, keyboard doesnt work, so i have to press the reboot button on the PC, and if i'm lucky the next time the PC usually boots fine as though nothing had gone wrong. My PC is:

Mobo: Biostar t-power i45
CPU Intel Core 2 Duo E8400
Graphics: XFX Nvidia GTX 275
Hard drive and DVD Drive connected using SATA with AHCI mode on. 
RAM 4GB DDR2. 

I have run all the checks I could do, installation media (installation went fine), Memory Checks, fsck-ing the drive manually and i'm not getting any errors. Any ideas?

---

### Post by Rubi1200 on 2010-10-13
Try disabling AHCI (turning off) in BIOS and see if there is a difference.

---

### Post by bergqvistjl on 2010-10-17
> **Rubi1200 said:**
> Try disabling AHCI (turning off) in BIOS and see if there is a difference.

I'll try that, although i'm using another OS, which needs that to boot. Are there issues with ubuntu and AHCI then?

---

### Post by bergqvistjl on 2010-11-02
OK that made no difference, any other ideas?

---

### Post by Don544 on 2010-11-03
I have the same problem,almost every boot i have to start a restore  then run fix broken packages, then reboot.
System is dual bot with win7 ,boot menu offers win7 and Ubuntu.
Boot cycle runs  then comes up with gave up waiting script at bottom of screen  and nothing else.
Reboot ,choose restore option from Ubuntu menu ,choose repair  and repair broken packages run repair then reboot and it works

---

### Post by michaelzap on 2010-11-03
@bergqvistjl: I have this issue also, and I think it's related to Compiz. You might try turning that off and seeing if it resolves the issue. What happens in my case sounds like the same thing as in yours: Ubuntu gets as far as the login screen, but then either fails to show the login dialog at all or occasionally does so at a reduced resolution (in which case I can login, but I always need to restart in order to restore full functionality). I notice that when this happens the boot process hangs at mounting my encrypted swap partition, and that seems to cause the Compiz hiccup. I like Compiz and I don't reboot often, so I've just been swearing under my breath and rebooting when this happens. It started for me with 10.04 also (and Grub 2/GDM 2).

@Don544: That sounds like a different issue (also rearing its head at boot) to me - at least it's different from what I'm experiencing.

---

