---
title: "Partition becomes unusable after setting swap area"
date: 2012-06-20
forum: General Help
---

### Post by meetdilip on 2012-06-20
[COLOR=#444444][FONT=arial]Tried to install Ubuntu 12.04 LTS on desktop with 2 GB RAM. Used the last option called " Something else ". But when I add partition as swap area (which is in ntfs), balance space is becoming unusable. What to do ? I tried setting swap area at beginning and end.
[/FONT][/COLOR]

---

### Post by kanikilu on 2012-06-20
> **meetdilip said:**
> But when I add partition as swap area (which is in ntfs) That doesn't really make sense - the swap area should be it's own partition, not "in ntfs".

Have you actually installed Ubuntu at this point, or are you getting stuck during the installation? Also, are you trying to dual boot with Windows, or are you letting Ubuntu use the entire disk?

---

### Post by oldfred on 2012-06-20
Do not confuse swap with a shared NTFS data partition.

Swap is for use when RAM memory is full. It is unformated space and will erase any data in a NTFS partition if set as swap.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by meetdilip on 2012-06-21
Let me clarify, SWAP is not in ntfs instead I used a currently ntfs drive to create swap partition. Once I create Swap out of ntfs, the rest becomes unusable. I am trying to dual boot xp and Ubuntu but failed due  to this issue.

---

### Post by oldfred on 2012-06-21
Often NTFS partitions need a chkdsk after a resize, depending on how you did it. Tne NTFS partition boot sector or PBR has to have a NTFS boot signature that includes the start and size of the NTFS partition. Usually chkdsk fixes that, sometimes or if bootable it may also need fixBoot. chkdsk & fixBoot can only be run from Windows or a Windows repair disk.

---

### Post by meetdilip on 2012-06-21
Sorry,  didn't follow. Can you please explain what I should do to install Ubuntu.

---

### Post by oldfred on 2012-06-21
Is the issue that the unallocated cannot be used?

Then you probably have used all 4 primary partitions. Most Windows systems now use all 4 primary partitions, in my opinion just to make it more difficult to modify system. 

Post this from liveCD. Does system work ok from liveCD?

sudo fdisk -lu

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

