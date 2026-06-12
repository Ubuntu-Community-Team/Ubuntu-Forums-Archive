---
title: "install Window's 7"
date: 2012-09-10
forum: General Help
---

### Post by Yayoushiko on 2012-09-10
So i want to install Window's 7 again.And after i install Window's 7 i want to duel boot with Ubuntu.
But in order to windows 7 it say's i need to format my hdd to ntfs.I  have tryed using Gparted,but it does not allow me to click on  anything.Please someone help,this is so frustrating.Over tv maybe.

---

### Post by overdrank on 2012-09-10
Are you using the live cd with gparted, as you have to unmount the partition to make changes to it.
_[RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")_

---

### Post by jerome1232 on 2012-09-10
> **Yayoushiko said:**
> So i want to install Window's 7 again.And after i install Window's 7 i want to duel boot with Ubuntu.
But in order to windows 7 it say's i need to format my hdd to ntfs.I  have tryed using Gparted,but it does not allow me to click on  anything.Please someone help,this is so frustrating.Over tv maybe.

First, backup any data you have, it will be lost if you reformat.

Anytime I've installed windows there was an option to write a new partition table (might say write new MBR), can't remember what the exact option is but it will wipe the hard drive of all partitions (and data) and the Windows installer will carry on it's merry way.

Poke around the installer for it.

---

### Post by apochry on 2012-09-10
Hello,

Provide some more information about the partitioning of your disk. Maybe even a screenshot of gparted, if you aren't sure what's going on there.
It is always easier to install Ubuntu after  Windows, this way the installation wizard takes care of everything. Not saying that you have to do that, but the best for new user.

Generally you'll need to do:

[LIST]
[*] Create ntfs partition
[*] Install Windows in there
[*] Repair grub --> [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[/LIST]
 - Christo

EDIT: Sorry for the duplicates, you guys are replying too fast! :-)

---

### Post by Yayoushiko on 2012-09-10
> **overdrank said:**
> Are you using the live cd with gparted, as you have to unmount the partition to make changes to it.
_[RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")_

No i just download the iso for Gparted,now i am going to burn it to a disc.
Also i already have Ubuntu installed.I was wanting to change back to window's 7.
After i change back then i was going to duel boot.Atm i want to uninstall Ubuntu.

---

### Post by jerome1232 on 2012-09-10
You don't have to use gparted or any of that, just pop in the Win7 install disc, goto the advanced drive options and delete/create partitions as needed.

It looks something like the below image.

---

