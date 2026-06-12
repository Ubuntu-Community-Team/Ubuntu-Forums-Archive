---
title: "How do I edit dmraid boot parameters?"
date: 2011-11-06
forum: General Help
---

### Post by vlix on 2011-11-06
Hi there,

I would like to ask a question about dmraid.

I've recently installed Ubuntu 11.10 on my computer, alongside Windows 7 in a standard dual boot configuration.

My system contains a firmware RAID/FakeRAID RAID1 array, using the Intel ICH10R controller on my motherboard. On the array is a single NTFS partition. I don't use the array as a boot drive.

I have noticed that at some point during boot, Ubuntu starts dmraid in order to activate the RAID set, after which it tries to mount any partitions on it. However, it does not succeed in mounting anything. I think I know why:

When I run ```
dmraid -ay
``` to manually activate the raid set, I get this output:

```
vlix@Wolfcastlex:/etc$ sudo dmraid -ay
/dev/sdb: "isw" and "ddf1" formats discovered (using ddf1)!
/dev/sda: "isw" and "ddf1" formats discovered (using ddf1)!
RAID set "ddf1_Array1" already active
vlix@Wolfcastlex:/etc$
```Dmraid erroneously chooses to use the "ddf1" format, while it should be using "isw" for Intel software RAID. When I run ```
dmraid -ay -f isw
``` to force the right format, the RAID set is activated properly, and I can proceed to mount the partition. I am guessing that this exact same problem occurs at boot time as well.

Now finally, my question :):

Which of all the various startup scripts and whatnot contains the command to run dmraid at boot? I'd like to edit it to force it to use the right format.

---

### Post by raja.genupula on 2011-11-06
hi man go with this 
[http://www.linuxquestions.org/linux/answers/Hardware/How_to_boot_from_RAID_using_dmraid](http://www.linuxquestions.org/linux/answers/Hardware/How_to_boot_from_RAID_using_dmraid)

---

### Post by vlix on 2011-11-07
Hi Raja,

Thanks very much for your reply! But I think your link is not quite what I'm looking for. I'm not trying to create a new script to make dmraid activate my RAID set during boot. Ubuntu is already automatically doing that out of the box, but with the wrong settings. I would like to modify those existing settings, not create new ones, if possible. Thanks for your help though!

---

