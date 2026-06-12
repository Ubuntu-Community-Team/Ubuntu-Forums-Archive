---
title: "can i delete from the /root directory?"
date: 2009-11-18
forum: General Help
---

### Post by mtgmutton on 2009-11-18
the title may sound stupid, but i just removed VirtualBox (got a windows laptop), and i found that in the /root directory, there is a subdirectory called .VirtualBox that's taking up 51GB of space... is it safe to delete it? 51GB is a lot and it feels wasteful to keep it. :???:

if it makes a difference, i'm running linux mint, not ubuntu.

---

### Post by ibuclaw on 2009-11-18
If you are never going to use VirtualBox again, remove it, as it is most likely old Virtual Hard Disk Images from your VBox setup.

Not sure how they ended up in there, though...
Maybe Linux Mint runs VBox as root?

---

### Post by Cheesemill on 2009-11-18
The .VirtualBox directory contains the settings and hard drives for your virtual machines.

If you don't need them anymore then go for it.

---

### Post by drs305 on 2009-11-18
And if you are deleting via a root nautilus GUI use SHIFT-DEL or "permanently delete" to prevent the folder ending up in /root/.local/share/Trash, where it would continue to take up space.

---

### Post by mtgmutton on 2009-11-18
thanks for the replies!

i never plan on using VirtualBox again.

i am deleting via CLI, so no worries about it being in the trash.

as to it being in the /root folder, i did always have to run it as root... never figured out why. oh well :)


P.S. trying to find the "thanks" button... where is it?

---

### Post by dcstar on 2009-11-19
> **mtgmutton said:**
> 
........
P.S. trying to find the "thanks" button... where is it?

Got removed years ago.

---

