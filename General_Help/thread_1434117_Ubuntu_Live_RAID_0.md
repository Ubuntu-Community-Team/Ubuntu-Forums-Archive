---
title: "Ubuntu Live RAID 0"
date: 2010-03-19
forum: General Help
---

### Post by Benster900 on 2010-03-19
I have a RAID 0 setup with Windows XP installed. Windows is not working so I popped in the Ubuntu live cd. I can't view the Raid 0 drives on the cd. I want to remove files and back them up to an External hdd. I have an Alienware M7700 with two 60Gb drives in RAID 0. I want to view these drives in ubuntu live cd. I would like a GUI app.

---

### Post by lyall on 2010-03-20
try looking at **InstallationSoftwareRAID** from the Community 
Documentation
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

it is a place to start

good luck and have fun learning

---

### Post by jrssystemsnet on 2010-03-20
> **Benster900 said:**
> I have a RAID 0 setup with Windows XP installed.

Need more information - Windows software RAID, or motherboard RAID?

If it's motherboard RAID - aka "fakeraid" - then try **sudo apt-get install dmraid** and **sudo dmraid -s**.  If dmraid finds an array, then **ls /dev/mapper/** and look for a random string of text name in there - something along the lines of **/dev/mapper/efdbdfbsg** or the like.  If you can find the dmraid array in /dev/mapper, then you can mount it with **sudo mount /dev/mapper/whatever /mnt** and access it that way.

I don't know WHAT to tell you if you used Windows software RAID0; I have no idea of Linux can read those or not. :)

---

### Post by Benster900 on 2010-03-21
The RAID is on the motherboard. Is there anyway with ubuntu live or any other linux distro.

---

