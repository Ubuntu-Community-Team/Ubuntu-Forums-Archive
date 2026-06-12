---
title: "Restore disk on restart"
date: 2009-08-11
forum: General Help
---

### Post by adam35413 on 2009-08-11
I am going to be creating a computer lab, and I was curious if there are any open source solutions for restoring a computer to a disk image after rebooting/logging off?  The technological knowledge of the people who will be using this lab will not be the best, and I am concerned with malware.

---

### Post by running_rabbit07 on 2009-08-11
Do you mean you want to set it up to where people basically take turns installing the system?

Or do you want to just give a demo on installing then return the system back to an MS system?

If you do an install you will have to be able to repair the MBR after removing Ubuntu in order for Windows to work.

---

### Post by dcstar on 2009-08-11
> **adam35413 said:**
> I am going to be creating a computer lab, and I was curious if there are any open source solutions for restoring a computer to a disk image after rebooting/logging off?  The technological knowledge of the people who will be using this lab will not be the best, and I am concerned with malware.

You can have the PCs with no OS on them and each time they reboot they get the OS loaded off the network via BOOTP from a server - it is slower than booting up from an installed OS but it guarantees an OS that is "fresh".

If you are going to run an insecure OS (like Windows) then you just set up the user accounts with as few privileges as possible and then configure the machines to wipe out all user accounts on next reboot - but that has nothing to do with Open Source.

---

### Post by adam35413 on 2009-08-11
> You can have the PCs with no OS on them and each time they reboot they get the OS loaded off the network via BOOTP from a server - it is slower than booting up from an installed OS but it guarantees an OS that is "fresh".

If you are going to run an insecure OS (like Windows) then you just set up the user accounts with as few privileges as possible and then configure the machines to wipe out all user accounts on next reboot - but that has nothing to do with Open Source.

This is the type of thing I am thinking of.  I want to guarantee that the users can't destroy the computers inadvertently, so I might try one or the other of the above.  Any guesses on the boot time differences?

---

### Post by fluffman86 on 2009-08-11
It's not free, but I would recommend Deep Freeze.  It's available for Windows, Mac, and Linux, and it looks like they have a free trial.  [http://www.faronics.com/html/dflinux.asp](http://www.faronics.com/html/dflinux.asp)

Personally, though, if you're using Ubuntu, it's pretty simple to have the full OS on each system, and then pull user profiles off of the network.  Then if a user destroys their profile it's their own fault, but a regular user has no access to the rest of the system.

---

### Post by dcstar on 2009-08-11
> **adam35413 said:**
> This is the type of thing I am thinking of.  I want to guarantee that the users can't destroy the computers inadvertently, so I might try one or the other of the above.  Any guesses on the boot time differences?

No, but you should be able to search out the experiences of others using this sort of thing.

---

