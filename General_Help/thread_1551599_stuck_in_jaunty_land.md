---
title: "stuck in jaunty land"
date: 2010-08-12
forum: General Help
---

### Post by kip152 on 2010-08-12
Switched my hp 32 bit from vista to ubuntu 9.4 a long time ago. have hp disks for vista. Can't upgrade ubuntu 9.10, whenever I do, cursor won't move. can't go back to vista. disk recovery goes about halfway through, by then, pc goes to sleep. Do I have to stay in 9.4 forever? I'd like to just go back to vista if I can't upgrade ubuntu.

---

### Post by wilee-nilee on 2010-08-12
Get the OEM recovery for vista from the manufacturer. I got a XP set from Acer for 20$ US, automatic activation. Is the recovery disc you have a full install disc that came with the computer or what?

Or you could download a later version of Linux, back up what you want and either dual boot or just install what you want.

As far as your computer going to sleep during a reload of Vista call your computer manufacturer, or investigate this on the web as well, maybe there is a setting your missing.

---

### Post by Muskegman on 2010-08-12
If you changed your OS from the original Vista to ubuntu then ubuntu would have changed the file system from windows NTFS to Linux Ext 3 file format.

Windows will not see the hard drive if it is an ext3 or ext 4 format

In order to reinstall vista from your installation disks you will have to use g-parted to change your hard drive file system back to NTFS format.

This can be done by booting from your ubuntu live cd and then select g-parted in the live session. There you should see your hard drive, sda1 or sdb1 ,depending how many hard drives you have. After you select the hard drive use the drop down box and select "NTFS"

* only do this if you wish to reinstall vista, if you wish to carry on using ubuntu then do not change anything.

---

### Post by kip152 on 2010-08-12
I think you can help me, but you're going too fast for me!
You want me to put my ubuntu disk in, then restart the pc?

---

### Post by philinux on 2010-08-12
> **kip152 said:**
> I think you can help me, but you're going too fast for me!
You want me to put my ubuntu disk in, then restart the pc?

Just to be clear. You're saying there is only ubuntu on the machine?

---

### Post by kip152 on 2010-08-12
Yes. What do i do after I put the ubuntu disk in? I don't want to install it again.

---

### Post by philinux on 2010-08-12
> **kip152 said:**
> Yes. What do i do after I put the ubuntu disk in? I don't want to install it again.

Before that open terminal, Apps-Accessories. Copy and paste in the command below. Report back any errors.

sudo apt-get update && sudo apt-get upgrade

---

### Post by kip152 on 2010-08-12
Lots of hits and igns, no errors.

---

### Post by kip152 on 2010-08-12
a

---

