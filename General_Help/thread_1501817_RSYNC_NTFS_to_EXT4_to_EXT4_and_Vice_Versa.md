---
title: "RSYNC NTFS to EXT4 to EXT4 and Vice Versa"
date: 2010-06-04
forum: General Help
---

### Post by lvleph on 2010-06-04
I am trying to sync a folder across three different computers. There is a central server which is the hub and has ext4 file system. The spokes however have two different file systems; ext4 and ntfs. How the heck do I sync a folder when the file systems change like this. It would have been easy if it were always ntf -> ext4 -> ntfs, but things are complicated when I try ntfs -> ext4 -> ext4 nothing transfers because of permissions.

---

### Post by dcstar on 2010-06-05
> **lvleph said:**
> I am trying to sync a folder across three different computers. There is a central server which is the hub and has ext4 file system. The spokes however have two different file systems; ext4 and ntfs. How the heck do I sync a folder when the file systems change like this. It would have been easy if it were always ntf -> ext4 -> ntfs, but things are complicated when I try ntfs -> ext4 -> ext4 nothing transfers because of permissions.

NTFS is **not** a Linux filesystem, NTFS **cannot** support all required Linux attributes. NTFS chokes on legal Linux file/folder names that start with ".".

Do not fool yourself that you can replicate data across foreign filesystems.

---

### Post by lvleph on 2010-06-05
I realize that NTFS is not a Linux file system. You absolutely can duplicate, to some extent, an ntfs file system to an ext4 file system. You just can't preserve permissions. 

The problem I am having is with permissions. Obviously, because NTFS is crap. The folder that I am trying to sync is a folder with photos and there are no files with "." at the beginning. Although, that is also not an issue, since I have had "." at the beginning of files in an NTFS file system before. Like I said earlier there is no issue if I am only syncing between the NTFS and the hub. The problem occurs when I sync to a third computer.

---

### Post by carolinason on 2011-10-21
a little late here-- remember to back up your data - oh yeah we are backing up data. use at your own discretion. to practice make some folders and files maybe.

file systems should not matter over the network that would be handled by the network protocol, i would use samba! you only need read permission to copy from and write permission to copy to... again handled by samba. rsync using the mount points you create for each machine.

"rsyncing" locally, the file system credentials again should not be an issue, ntfs-3g should handle this. i am using rsync as root. you might want to sudo, but i am a bit wacky like that 

just a local example -- i can use rsync on my machine with an ntfs partition and an ext4 partition without any permission issues. i use the -a switch for archive.

to **copy** from ntfs-3g -> ext4
> rsync -va /path/to/ntfs-3g_partition-mounted-directory/ /path/to/ext4_partition-mounted-directory/
just reverse that for ext4 -> ntfs-3g

to **sync** to the target or destination i use --delete, to remove files from the target no longer on the source
from ext4 -> ntfs
> rsync -va --delete /path/to/ext4_partition-mounted-directory/ /path/to/ntfs-3g_partition-mounted-directory/

for archives that have tons of data i **sync** the directories using the --progress switch, so i can watch the activity, again from ext4 -> ntfs
> rsync -va --delete --progress /path/to/ext4_partition-mounted-directory/ /path/to/ntfs-3g_partition-mounted-directoryy/

---

### Post by oldos2er on 2011-10-21
Closed. Please don't bump old threads.

---

