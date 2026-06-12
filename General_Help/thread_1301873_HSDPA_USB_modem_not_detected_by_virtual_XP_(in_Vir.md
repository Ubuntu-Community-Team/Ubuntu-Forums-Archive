---
title: "HSDPA USB modem not detected by virtual XP (in VirtualBox)"
date: 2009-10-26
forum: General Help
---

### Post by t0p on 2009-10-26
I want to unlock a Huawei E160X HSDPA USB modem.  To do so, I get a code from my mobile service provider, which I then input to a particular program.  Unfortunately, this program comes only in a Windows version.

I don't have Windows on my computers and I don't really want to install XP just for this program.  So I installed VirtualBox, then installed XP to it.  I used the closed-source version of VirtualBox as I was told only that version could use USB devices.

The virtual XP seems to have installed just fine.  It can use USB devices - I enable them by checking them under Devices > USB - for instance it detects and can use my USB flash sticks without any problems.

When I plug in the modem, an entry for it appears at Devices > USB.  I check that entry, then virtual XP says it has "found new hardware".  But the modem never actually appears.  So the modem-unlocking software can't see it, and I can't get on with unlocking it.

The modem is seen by Ubuntu just fine.  And when I have plugged it into a computer using real XP, that XP sees it too.  It's just this virtual XP that can't see it, when the virtual OS sees other USB devices okay.

Anyone know what I can do about this?  I don't want to have to install XP to my hard drive just to use this one program.  And there isn't an XP computer handy that I can use for this either.

---

### Post by t0p on 2009-10-27
bump

---

### Post by diablo75 on 2009-10-27
This problem likely has more to do with Windows than anything else.

I would start by checking (in Windows) Control Panel>System>Hardware tab>Device Manager to see if the modem is recognized correctly or if the drivers for it need to be installed/updated.

Otherwise, find a friend who has XP on their machine natively installed and give it a whirl on that.

---

### Post by dj-toonz on 2009-10-27
You'll need a proper install of windows to use that program with the modem, as Virtual-box under Linux, doesn't set up the modem in windows, It shares the connection between the host & the guest (bridges it) I.e you set up the modem in Linux using network-manager & virtualbox uses that connection, doesn't access the modem directly

---

### Post by geiroffenberg on 2011-08-31
> **dj-toonz said:**
> You'll need a proper install of windows to use that program with the modem, as Virtual-box under Linux, doesn't set up the modem in windows, It shares the connection between the host & the guest (bridges it) I.e you set up the modem in Linux using network-manager & virtualbox uses that connection, doesn't access the modem directly

oooh. it's already connected. could have spared me some time if i read this or tried IE instead of trying to get the modem to work. it already works. must say virtualbox is absolutely fantastic.

---

