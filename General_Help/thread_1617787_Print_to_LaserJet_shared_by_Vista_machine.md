---
title: "Print to LaserJet shared by Vista machine"
date: 2010-11-09
forum: General Help
---

### Post by bendilts on 2010-11-09
My LaserJet is connected to an old desktop machine that has it shared.  The configuration on that desktop is correct, since I have been printing through it from other Windows machines for a long time (and it still works now).

I recently started dual-booting Ubuntu 10.10 on my otherwise Windows laptop, and I've gotten everything basically working how I like it, except that I can't get connected to that printer.

The Vista machine is at IP address 192.168.0.103, and the printer is shared as LaserJet.  It's set up with workgroup MSHOME.

When I go to add a printer in Ubuntu, I click the Browse button under "SMB Printer," and I see the MSHOME workgroup, but when I try to expand it, there's nothing inside.

If I try to type in the address directly (smb://192.168.0.103/LaserJet), the Verify button tells me "Print Share Inaccessible, Connection timed out."  Note that I can ping 192.168.0.103 fine.  I can continue through the rest of the wizard, but I obviously can't print anything out after I finish the setup, since the connection is failing for some reason.

There is no username or password required to see the shared printer.

Any idea what could be going on here?  I'm kind of at wit's end here, and I'd love to be able to ditch Windows--with the obvious exception of Starcraft II, of course :-D

---

### Post by pricetech on 2010-11-09
Have you installed Samba ??  In Synaptic; system-config-samba

See if that helps.

---

### Post by bendilts on 2010-11-09
That had no effect.  system-config-samba seems to be what I'd use to share a printer FROM Ubuntu, not get at a Windows-shared printer.

---

### Post by bendilts on 2010-11-09
Got it!  It was a setting on the Windows server after all: [http://support.microsoft.com/default.aspx?scid=kb;en-us;177078](http://support.microsoft.com/default.aspx?scid=kb;en-us;177078)

---

