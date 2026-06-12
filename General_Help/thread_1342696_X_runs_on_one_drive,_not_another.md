---
title: "X runs on one drive, not another"
date: 2009-12-01
forum: General Help
---

### Post by Baka no Kami on 2009-12-01
I installed 9.10 server on an old laptop to use as a digital picture frame, but I'm having an odd problem.  The only packages I installed past the base system were xorg, samba, ssh, and feh to display images.  I use xinit to start feh when the system starts up.

I replaced the harddrive with a ide2cf adapter and installed the whole system on a 4gig compactflash drive.  The problem is that X doesn't run.  It loads up, the screen blanks as the resolution changes, then it crashes back to the terminal.  The wierd part is that the exact same setting works with no problems when the system is installed on a 4gig USB thumbdrive.

So, everything else being the same, X runs when I'm using a USB drive, crashes when I'm using an IDE drive.

Has anyone seen something like that before?

---

### Post by blueridgedog on 2009-12-01
When attempting to start x from a terminal, are there any error messages? Are there any error messages in /var/log/Xorg.0.log?

---

### Post by Baka no Kami on 2009-12-05
> **blueridgedog said:**
> When attempting to start x from a terminal, are there any error messages? Are there any error messages in /var/log/Xorg.0.log?

Thanks, I wasn't even sure where to look for the logs, but I got it fixed.  I tried plugging the CF card into a USB reader and booting off that.  It started up but with the same problem that X would crash.  So I reinstalled Ubuntu with the CF card still hooked to the USB.  I reset everything the way it was before and everything worked.  I don't know why.  Then I moved the CF card from the USB reader, back to the IDE adapter.  Everything still worked.  I don't understand it, but have decided not to question it.

---

