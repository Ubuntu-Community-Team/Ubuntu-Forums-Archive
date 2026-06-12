---
title: "SOLVED: 2.5 GB System Partition - What Went Wrong?"
date: 2009-07-22
forum: General Help
---

### Post by drs305 on 2009-07-22
This post is for Jaunty/Karmic users who elected to install Ubuntu alongside Windows and ended up with an unusably small (2.5GB) Ubuntu partition. It is an extension of another post about how to expand an Ubuntu system partition: [_Expanding an Ubuntu System Partition_]("http://ubuntuforums.org/showthread.php?t=1219270"). It is *not* applicable to Wubi installations within Windows.

UPDATE: This bug is being actively worked on. It will definitely be fixed in Karmic. The default once a fix is introduced will be to take (available space - 2.5GB) and use the midpoint. Until the bug is fixed, users must continue to manually select a larger default as explained below.

[SIZE="3"]**[COLOR="Navy"]How Did I End Up with a 2.5 GB Ubuntu Partition?[/COLOR]**[/SIZE]
The graphics in Step 4 in the Jaunty partitioning changed from earlier releases. When the user elects to share Windows and Ubuntu, you should click on the partition bar graphic at the bottom of the page. This action will activate a slider which the user must move left or right to select the Ubuntu partition size. ***[COLOR="DarkRed"]If the user does not move the slider, the default size will be 2.3 to 2.5 GB (shown), which is not large enough to support a normal installation.[/COLOR]*** The user should move the slider left to increase the size. The *absolute minimum* size should be at least 5GB; the *minimum recommended* size is at least 8 GB.

[SIZE="3"]**[COLOR="DarkRed"]Here is a snapshot of Step 4 of the installation, with the user electing to "*Install them side-by-side*":[/COLOR]**
_[ATTACH]121997[/ATTACH]_[/SIZE]

**[SIZE="3"][COLOR="Navy"]Related Links:[/COLOR][/SIZE]**
[_Installation/SystemRequirements_]("https://help.ubuntu.com/community/Installation/SystemRequirements")
[Jaunty Guide]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")
[_Expanding an Ubuntu System Partition_]("http://ubuntuforums.org/showthread.php?t=1219270")
[_HowtoPartition_]("https://help.ubuntu.com/community/HowtoPartition")
[_Partitioning Basics_]("http://ubuntuforums.org/showthread.php?t=282018")
Troubleshooting:
[_RecoverLostDiskSpace_]("https://help.ubuntu.com/community/RecoverLostDiskSpace")
[_Disk Full - Check Your Trash_]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by computerkid2000 on 2009-08-08
> **drs305 said:**
> This post is for Jaunty users who elected to install Ubuntu alongside Windows and ended up with an unusably small (2.5GB) Ubuntu partition. It is an extension of another post about how to expand an Ubuntu system partition: [_Expanding an Ubuntu System Partition_]("http://ubuntuforums.org/showthread.php?t=1219270"). It is *not* applicable to Wubi installations within Windows.

[SIZE=3]**[COLOR=Navy]How Did I End Up with a 2.5 GB Ubuntu Partition?[/COLOR]**[/SIZE]
The graphics in Step 4 in the Jaunty partitioning changed from earlier releases. When the user elects to share Windows and Ubuntu, you should click on the partition bar graphic at the bottom of the page. This action will activate a slider which the user must move left or right to select the Ubuntu partition size. ***[COLOR=DarkRed]If the user does not move the slider, the default size will be 2.5 GB (shown), which is not large enough to support a normal installation.[/COLOR]*** The user should move the slider left to increase the size. The *absolute minimum* size should be at least 5GB; the *minimum recommended* size is at least 8 GB.

Here is a snapshot of Step 4 of the installation, with the user electing to "*Install them side-by-side*":
_[ATTACH]121997[/ATTACH]_

**[SIZE=3][COLOR=Navy]Related Links:[/COLOR][/SIZE]**
[_Installation/SystemRequirements_]("https://help.ubuntu.com/community/Installation/SystemRequirements")
[Jaunty Guide]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")
[_Expanding an Ubuntu System Partition_]("http://ubuntuforums.org/showthread.php?t=1219270")
[_HowtoPartition_]("https://help.ubuntu.com/community/HowtoPartition")
[_Partitioning Basics_]("http://ubuntuforums.org/showthread.php?t=282018")
Troubleshooting:
[_RecoverLostDiskSpace_]("https://help.ubuntu.com/community/RecoverLostDiskSpace")
[_Disk Full - Check Your Trash_]("http://ubuntuforums.org/showthread.php?t=898573")


WELL THE NEXT VERSION BETTER FIX THAT !!! sorry for shift!

---

### Post by michy99 on 2009-08-08
Somehow i missed this when it was posted. Well that solves the question of why so many people are ending up with tiny partitions. The slider needs to be below the option to install side-by-side. As it is, it looks like it belongs to the last option, to partition manually. I wonder if the development team has been notified of this?

---

### Post by drs305 on 2009-08-08
> **michy99 said:**
> Somehow i missed this when it was posted. Well that solves the question of why so many people are ending up with tiny partitions. The slider needs to be below the option to install side-by-side. As it is, it looks like it belongs to the last option, to partition manually. I wonder if the development team has been notified of this?

I filed a bug report about it, anecdotally since it didn't happen to me. I told them what was happening and gave them a link to the thread.

---

