---
title: "Problems downloaded games"
date: 2011-01-25
forum: General Help
---

### Post by devinsoles on 2011-01-25
I am trying to download an online mmorpg but an error keeps occuring with archive manager. 

It reads as follows
Archive:  /home/jeff/Downloads/shaiya_us_downloader.exe
[/home/jeff/Downloads/shaiya_us_downloader.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/jeff/Downloads/shaiya_us_downloader.exe or
          /home/jeff/Downloads/shaiya_us_downloader.exe.zip, and cannot find /home/jeff/Downloads/shaiya_us_downloader.exe.ZIP, period.

What should I do?

---

### Post by Bucky Ball on 2011-01-25
downloader.exe is a Windows file. Unless you are using Wine, Ubuntu won't open or deal with this file type. It is an execute file, unused in Linux. ;)

---

### Post by devinsoles on 2011-01-25
So to fix this problem download wine?

---

### Post by Bucky Ball on 2011-01-25
> **devinsoles said:**
> So to fix this problem download wine?

If you wish to use Windows programs. If you want to use a LOT of Windows programs I suggest dual-booting as some can be hit-and-miss with Wine. They don't all work faultlessly and some not at all. ;)

It can be found in the repositories: System>Administration>Synaptics Package Manager. Search for 'wine' and install.

---

### Post by blueridgedog on 2011-01-25
Based on the wine site, this appears to run under wine (it requires a windows OS):

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10214](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10214)

I suggest you install wine from synaptic and then run the install "exe" from wine.  You should be able to right click the "exe" file and select "open with wine".

---

### Post by devinsoles on 2011-01-25
I am only wanting to run this one program so hopefully I don't have to resort to dual booting. Thanks.

---

### Post by FahadMKS on 2011-01-25
Before going ahead with the DUal Boot, I would suggest you to install the Wine software from the Ubuntu Software Center and then try to install the software that you need.

If you get an error when double clicking the software setup(The Game), then right click the setup of the game and then select Properties and on the new window select the tab as "Permissions" and then check the box to allow Executing as a program and then retry to install the Game.

If you face with the issue after this, please do reply us back.

---

### Post by Bucky Ball on 2011-01-25
FahadMKS:

> **devinsoles said:**
> I am only wanting to run this one program so hopefully I don't have to resort to dual booting. Thanks.

Please read previous posts before posting. ;)

---

