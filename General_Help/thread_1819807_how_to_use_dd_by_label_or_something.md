---
title: "how to use dd by label or something?"
date: 2011-08-06
forum: General Help
---

### Post by fbs777 on 2011-08-06
Hi.
i need a way to recovery a hd image using an automate script.

what i have:
- 1 hd with linux + the hd.img file
- 1 hd empty to receive the backup from the hd.img

the problem: sometimes, depending how/where the hds are conected in the mainboard they are named as sda/sdb/sdc/etc, so if i make a script to execute the command "dd if=/opt/hd.img of=/dev/sdb" is possible to restore the image to the same hd where the image is...

the hd with linux is named with the label "backup", so i was thinking on something to check which hd is empty or not labeled "backup", get the /dev/sdX of this hd and then use the dd with this variable.

Someone know how to make this script?

thanks

---

### Post by jerrrys on 2011-08-06
you could just use "clonezilla".  it backs up hdd to hdd nicely no matter what slot is being used.

---

### Post by fbs777 on 2011-08-06
> **jerrrys said:**
> you could just use "clonezilla".  it backs up hdd to hdd nicely no matter what slot is being used.

Unfortunately, this must be used by very newbie people, so the system must boot and auto execute a script to the recovery starts and when finish, the system is shutdown, with no interaction.

---

### Post by dcstar on 2011-08-06
> **fbs777 said:**
> Hi.
i need a way to recovery a hd image using an automate script.

what i have:
- 1 hd with linux + the hd.img file
- 1 hd empty to receive the backup from the hd.img

the problem: sometimes, depending how/where the hds are conected in the mainboard they are named as sda/sdb/sdc/etc, so if i make a script to execute the command "dd if=/opt/hd.img of=/dev/sdb" is possible to restore the image to the same hd where the image is...

the hd with linux is named with the label "backup", so i was thinking on something to check which hd is empty or not labeled "backup", get the /dev/sdX of this hd and then use the dd with this variable.

Someone know how to make this script?

thanks
This will show you what drives are detected on your system and how many partitions are detected:
```
sudo partprobe -s
```
You should be able to incorporate the output into a script to select the device with no partitions as the dd destination.

---

### Post by fbs777 on 2011-08-07
> **dcstar said:**
> This will show you what drives are detected on your system and how many partitions are detected:
```
sudo partprobe -s
```
You should be able to incorporate the output into a script to select the device with no partitions as the dd destination.

thank you, this will solve the problem!

---

