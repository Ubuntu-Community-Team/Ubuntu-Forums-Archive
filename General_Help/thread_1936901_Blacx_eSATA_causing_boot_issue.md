---
title: "Blacx eSATA causing boot issue"
date: 2012-03-06
forum: General Help
---

### Post by jeliot86 on 2012-03-06
Hello linux newbie here):P

I'm trying to get my blacx eSATA hardrive enclosure to work but 11.10 is not playing nice.  I did a fresh install booted up (bios see's drive) into ubuntu.  Plugged in eSATA and fired up the enclosure and got nothing.  Ubuntu won't recognize it.  So I restarted right as Ubuntu starts to load it fails and hangs.  I only know it happens right away because the HD indicator stops almost immediately. I have not looked into watching the post or boot loader or whatever linux calls it, Im sure there is a command for that!;)  i unplug eSATA reboot and BAM.... im back in.  replug in duet and BAM ubuntu fail to boot  

Blacx Duet
ASUS M2V 1.01g
64bit Ubuntu 11.10
AMDx64 dual core

Any help would be greatly appreciated, I would really like NOT to go back to USB on this enclosure 

P.S I did try the enlosure in both slots and also turned "Show Always" in the compizconfig

---

### Post by dcstar on 2012-03-08
> **jeliot86 said:**
> Hello linux newbie here):P

I'm trying to get my blacx eSATA hardrive enclosure to work but 11.10 is not playing nice.  I did a fresh install booted up (bios see's drive) into ubuntu.  Plugged in eSATA and fired up the enclosure and got nothing.  Ubuntu won't recognize it.  So I restarted right as Ubuntu starts to load it fails and hangs.  I only know it happens right away because the HD indicator stops almost immediately. I have not looked into watching the post or boot loader or whatever linux calls it, Im sure there is a command for that!;)  i unplug eSATA reboot and BAM.... im back in.  replug in duet and BAM ubuntu fail to boot  

Blacx Duet
ASUS M2V 1.01g
64bit Ubuntu 11.10
AMDx64 dual core

Any help would be greatly appreciated, I would really like NOT to go back to USB on this enclosure 

P.S I did try the enlosure in both slots and also turned "Show Always" in the compizconfig

Hotplugging SATA drives requires AHCI enabled in your BIOS, try that.

---

### Post by jeliot86 on 2012-03-12
Thank for the tip:

I ended up trying to run the hardrive from the 3rd SATA internal port on my mother board and that didn't work either.  I later found out that there was an issue the Marvell controller on my MB and Ubuntu.  Ironically this Marvell chip also controls the eSATA port, but the other 2 SATA ports are controlled by the VIA chipset.  Weird but I ended up having to modify some config files in Ubuntu to get the Marvell controller working and I'm up and running.  Once this brutal recovery project finishes I plan to try the eSATA and re post

thnx

---

### Post by ptoye on 2012-03-24
Please tell us what the fix was. I've got what sounds like the same (or similar) problem with a Marvell controller on an Asus mobo.

---

