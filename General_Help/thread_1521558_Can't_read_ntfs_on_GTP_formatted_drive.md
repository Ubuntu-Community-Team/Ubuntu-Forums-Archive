---
title: "Can't read ntfs on GTP formatted drive?"
date: 2010-06-30
forum: General Help
---

### Post by beastrace91 on 2010-06-30
Howdy All,

So I currently have OSX and Windows 7 install on my hardrive - I would like to add 10.04 in the mix, however it will not let me resize my Windows partition because it does not recognize it as ntfs. It will not let me mount it via cli or gui and gparted will only offer to remove the partition - not resize.

The drive is GPT - any suggestions how I can fix this?

~Jeff

---

### Post by oldfred on 2010-07-01
GPT info 
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Download gdisk or use parted:
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
The emergency disks that include GPT fdisk are:
    * SystemRescueCd
    * PartedMagic 
sudo parted /dev/sda unit s print
gdisk -l /dev/sda
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

---

