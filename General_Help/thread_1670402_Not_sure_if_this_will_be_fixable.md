---
title: "Not sure if this will be fixable"
date: 2011-01-18
forum: General Help
---

### Post by rbailey83 on 2011-01-18
i want to re install windows vista, here's the problem: my dvd drive is not working, i only have 1 memory stick, when i go to re install vista at the partitions menu i cannot delete i am told that partition needs to be NTFS, is there any way to change the partition or add a new NTFS partition from ubuntu desktop so that i don't have to delete vista install on memory stick, install gparted, then delete gparted and put vista back on? if so can anyone give me step by step?

---

### Post by ksprasad on 2011-01-18
HI,
 
 Yes. Go to system->Administration->Disk Utility.
 There you can create a new NTFS partition.
 
Regards,
ksprasad

---

### Post by ksprasad on 2011-01-18
-

---

### Post by Quackers on 2011-01-18
You can install gparted via synaptic package manager, use that to create/change partitions.

---

### Post by rbailey83 on 2011-01-18
> **Quackers said:**
> You can install gparted via synaptic package manager, use that to create/change partitions.

i tried that, followed the instructions but there was no unallocated slot, could not unmount, did the partition table, unallocated slot showed, put to NTFS but would not do it

---

### Post by Quackers on 2011-01-18
How are you trying to re-install Vista? Installation disc, recovery dvd? And what exactly do you want to do with your partitions?

---

### Post by rbailey83 on 2011-01-18
> **Quackers said:**
> How are you trying to re-install Vista? Installation disc, recovery dvd? And what exactly do you want to do with your partitions?

re-installing using vista install on usb. I want to remove ubuntu and switch back to vista but the format needs to be NTFS, i tried gparted and disk utility but cannot create a new partition or change current.

---

### Post by Quackers on 2011-01-18
I have never used an installation usb before, but it seems to me that the installer part should be able to use the whole disc, formatting and creating the necessary partitions as it goes. That's what a dvd installer does iirc.

Alternately, you should be able to run gparted from the live cd/usb desktop. If you turn swap off you should be able to do what you want.

---

### Post by rbailey83 on 2011-01-18
cannot use install disc dvd drive is not working

---

### Post by rbailey83 on 2011-01-18
cannot use install disc dvd drive is not working

---

### Post by Quackers on 2011-01-18
No Ubuntu live usb?

I edited the post above.

---

### Post by rbailey83 on 2011-01-19
no only have the 1 usb and it has the vista install on it right now

---

### Post by slooksterpsv on 2011-01-19
Have you created the usb stick correctly? The reason I ask is cause if it's truly booting from the USB drive, you should have the option to modify the hard drive. If not, then either:

A) You're not booting from the USB
B) The installation is trying to run from within Ubuntu, in which case you can't modify the hard drive (very doubtful on this one)
C) You're not modifying the partitions correctly during the install - e.g. you have to click on Advanced, then click on the drive, click delete (deleting the partitions you want to remove), then choosing next and installing.
D) The installation thinks your trying to install to the USB not the actual hard drive, in which case the USB can't be modified as it's running all the programs.
E) Something else I haven't though of...

---

