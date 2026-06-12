---
title: "How do I make Deluge share 'STATE' folder across Ubuntu and Windows"
date: 2011-02-20
forum: General Help
---

### Post by tenspeedfury on 2011-02-20
[LEFT]I'm dual booting windows 7 and ubuntu 10.10.  I use  Deluge on both boots.  Both instances of Deluge share a default download  location on the Windows partition.  I would like both instances of  Deluge to share it's 'State' folder, which is where Deluge stores the  .torrent files it is currently using and the information about their  progress and such. 

On the windows side this location is 
%APPDATA%\deluge\state

and on Ubuntu

~/.config/deluge/state

I found them, they look good.  I can read/write to the windows side from  Ubuntu, the windows partition is automounted, yada yada.  I can even  autoadd the .torrents from the Windows location when I run the Linux  Deluge.

But what I want is for the Windows side to function normally while altering the Ubunutu instance of Deluge to use the 
%APPDATA%\deluge\state directory on the windows partition instead of it's default ~/.config/deluge/state

Such that when I add torrents in Ubuntu (primary OS) and switch to  Windows, Deluge will be productively downloading/seeding while I'm  wasting my life with Starcraft.

Possible? Much thanks.  First post after a year of using lurking this forum and finding more help than I could ever hope for.

[/LEFT]

---

### Post by jerenept on 2011-02-20
> **tenspeedfury said:**
> [LEFT]I'm dual booting windows 7 and ubuntu 10.10.  I use  Deluge on both boots.  Both instances of Deluge share a default download  location on the Windows partition.  I would like both instances of  Deluge to share it's 'State' folder, which is where Deluge stores the  .torrent files it is currently using and the information about their  progress and such. 

On the windows side this location is 
%APPDATA%\deluge\state

and on Ubuntu

~/.config/deluge/state

I found them, they look good.  I can read/write to the windows side from  Ubuntu, the windows partition is automounted, yada yada.  I can even  autoadd the .torrents from the Windows location when I run the Linux  Deluge.

But what I want is for the Windows side to function normally while altering the Ubunutu instance of Deluge to use the 
%APPDATA%\deluge\state directory on the windows partition instead of it's default ~/.config/deluge/state

Such that when I add torrents in Ubuntu (primary OS) and switch to  Windows, Deluge will be productively downloading/seeding while I'm  wasting my life with Starcraft.

Possible? Much thanks.  First post after a year of using lurking this forum and finding more help than I could ever hope for.

[/LEFT]
It is possible to use a symlink, I think. Right-click on the /state folder in the Win partition, and select "make link". Now move this link to "/.config/deluge", erase the current folder, and rename it to "state.

P.S. Starcraft works okay in WINE, I think....[Starcraft @ Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=149") [SCII @AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882")

---

### Post by tenspeedfury on 2011-02-20
> **jerenept said:**
> It is possible to use a symlink, I think. Right-click on the /state folder in the Win partition, and select "make link". Now move this link to "/.config/deluge", erase the current folder, and rename it to "state.

P.S. Starcraft works okay in WINE, I think....[Starcraft @ Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=149") [SCII @AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882")

This is good, almost.  I set up the symlink, all is well.  I've never used symlinks before, and they are exactly what I imagined to exist and be the solution.  

The problem is Ubuntu writes the Save Path as /media/sda2/.../Downloads.  When I open Deluge in Windows it has no idea that /media/sda2/Users/Flint/Downloads is equivalent to C:\Users\Flint\Downloads.

Interestingly enough I'm watching Deluge (windows) (attempt to) download to /media/sda2/Users/Flint/Downloads and it is showing file progress!?  But (obviously) when I right click on 'open folder location' nothing happens  or if I try to point Windows Explorer to /media/sda2/.../Downloads it doesn't work.

No surprise, but this is progressing into a Windows support thread.  Any ideas?

Thanks

---

### Post by jerenept on 2011-02-20
umm... i don't think it will work that way in Windows....

This is more what I had in mind: 
[CENTER]Windows||Ubuntu
Deluge||Deluge
Deluge folder<-||-symlink to folder[/CENTER]

Windows doesn't understand Symlinks AFAIK.

---

### Post by tenspeedfury on 2011-02-20
Yes, that's how I have it set up, per your directions.  The problem is that when Ubuntu Deluge writes to the Windows 'State' folder it saves the 'Save Path' info as /media/sda2/.../Downloads.  Then, when Windows Deluge starts and reads the 'Save Path' Windows doesn't know what the /media/sda2/.../Downloads directory is.

The work around I'm coming up with to set up Deluge Preferences identically in Windows and Ubuntu as:

Download to: Windows Partition 'Downloads' Folder
Autoadd .torrents from: Windows Partition 'Torrents' Folder
Copy of .torrents to: Windows Partition 'Torrents' Folder
Delete copy of .torrent file on remove

This is somewhat less than ideal as the downside is that Deluge will constantly be 'rechecking' the files when switching between OSes and I'll be having a redundant 'Torrent Files' directory.  But boo-freaking-hoo huh?

---

### Post by jerenept on 2011-02-20
> **tenspeedfury said:**
> Yes, that's how I have it set up, per your directions.  The problem is that when Ubuntu Deluge writes to the Windows 'State' folder it saves the 'Save Path' info as /media/sda2/.../Downloads.  Then, when Windows Deluge starts and reads the 'Save Path' Windows doesn't know what the /media/sda2/.../Downloads directory is.

The work around I'm coming up with to set up Deluge Preferences identically in Windows and Ubuntu as:

Download to: Windows Partition 'Downloads' Folder
Autoadd .torrents from: Windows Partition 'Torrents' Folder
Copy of .torrents to: Windows Partition 'Torrents' Folder
Delete copy of .torrent file on remove

hmmm... i dunno.... 
does the symlink reside in the Ubuntu partition, and point to the Windows partition, or the other way around?.... cause I'm stumped :confused:

---

### Post by tenspeedfury on 2011-02-20
> **jerenept said:**
> hmmm... i dunno.... 
does the symlink reside in the Ubuntu partition, and point to the Windows partition, or the other way around?.... cause I'm stumped :confused:

It does, correct.  Reside in Ubuntu, point to Windows partition.

My ideal solution might just be unreachable due to the fundamental difference of Ubuntu writing to the mount point /media/sda1 and Windows only writing to C:\ without being capable of understanding their equivalence.

Thanks for your help, either way I learned about symlinks!

---

