---
title: "external hdd"
date: 2011-04-16
forum: General Help
---

### Post by mr.farenheit on 2011-04-16
i bought a 1 tb external harddrive. i tried to format it to an ext format but when it went through the process a few second ubuntu would stop and say drive error. i tried doing exfat and got the same results and now ubuntu won't recognize the drive. i had to format it to ntfs which i wanted to avoid. any ideas?

---

### Post by corcomp84 on 2011-04-16
which program are you using to formate it, G parted or the disk utility or something else?  I know that I had a few issues with formating mine because some of the hard drives come with a special partition for backup's.. I just deleted whatever they had currently on it and then re-formated the whole drive.. I never did like using just etx though u never know when you want to use it on windows or other shares.. Also what was the hard drive make?

---

### Post by mr.farenheit on 2011-04-16
the hard drive was blank,no side partitions. i used gparted and disk utility. ended up using windows format utility on xp. and its an iomega brand hdd.

---

### Post by corcomp84 on 2011-04-16
are u using a USB hub or directly connecting it? Also were you using ETX4 or an older on? Could also be the type of partition you are trying to make, like extended or primary.. Which type did you choose? I have 4 T hard drives that I store on my home network, and they use fat 32, I tried ETX but I found it to be a pain whenever I wanted to share it with media servers and windows computer..

---

### Post by mr.farenheit on 2011-04-16
it's usb and i was trying to set it up for backing up files. i thought about fat32 but for some reason i though certain formats can only read up to a certain drive size. i can try formatting multple partitions.

---

### Post by corcomp84 on 2011-04-16
No my whole 1t drive is fat 32 or at least over 900gb worth.. pending on what you want to back up and if or how you want to share it across a network I would only worry about 1 maybe 2 different partitions.. That way you can have secure access to one partition and openly share another if you want.. Just when you formate it try to make sure the USB plug is directly plugged into the computer and not through a USB hub, It probably makes no difference but sometimes I have issues..

---

### Post by mr.farenheit on 2011-04-16
i guess i can try it again. thanks for the help :)

---

### Post by dragonfly41 on 2011-04-16
I've also had problems going through a USB hub particularly if it doesn't have its own power supply.
Try connecting your drive directly to a USB port nearest to the power plug (usually at the back of the motherboard).
I use Parted Magic on a bootable CD to partition and check disk health.

---

