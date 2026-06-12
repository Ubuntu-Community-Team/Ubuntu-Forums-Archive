---
title: "Installing Ubuntu messed up my Windows XP display theme"
date: 2009-10-02
forum: General Help
---

### Post by keatonbell on 2009-10-02
Hello,

I just installed the newest version of Ubuntu side-by-side with Windows XP and now when I load XP I am not greeted with the passable "classic" theme but instead the default eyesore that is the bright blue and green XP appearance.  Also my desktop background is reverted back to the default blue.  Even if I change them back to my preferences, they are reset when I reboot.  Any idea how I can get my display settings to stick?

Thanks!
Keaton

---

### Post by The Cog on 2009-10-02
I can't think why that might happen, unless it's just that your windows disk is now out of space and having trouble saving settings.

---

### Post by keatonbell on 2009-10-02
No that's not it.  I have plenty of space for Windows.  Thanks for the guess though!  Keep 'em coming!

---

### Post by jlacroix on 2009-10-02
> **keatonbell said:**
> No that's not it.  I have plenty of space for Windows.  Thanks for the guess though!  Keep 'em coming!

Your Windows XP profile is corrupted. Try copying your files off, and recreating your profile. My immediate guess is that you loaded Ubuntu on the same physical hard disk as Windows, and there may be a bad sector that Windows XP was forced to use for your profile as a result of the repartitioning. Run the manufacturer's tools for your drive.

Of course, that is just a guess...

---

### Post by NightwishFan on 2009-10-02
Did you do a normal installation or use WUBI?

It is not Ubuntu that did that, unless the poster above is right. Perhaps do a system restore or try to change the system to best performance under: control panel -> system

Hope it works for you.

---

### Post by jlacroix on 2009-10-02
> **NightwishFan said:**
> Did you do a normal installation or use WUBI?

It is not Ubuntu that did that, unless the poster above is right. Perhaps do a system restore or try to change the system to best performance under: control panel -> system

Hope it works for you.

Actually, a System Restore would be a bad idea, because if it's malware, System Restore makes that worse.

What I would do is actually go into the Recovery Console (using the Windows CD) and run:

chkdsk C: /P

That should clear it up if its a hard drive problem but I'd still scan the drive with manufacturers tools just in case.

---

