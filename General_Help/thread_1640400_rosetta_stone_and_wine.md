---
title: "rosetta stone and wine"
date: 2010-12-07
forum: General Help
---

### Post by sunnydawn on 2010-12-07
I would really like help trying to install rosetta stone with wine....it said it is a non executable file?

---

### Post by 3rdalbum on 2010-12-07
Go into a terminal, type "wine " with a space at the end, and drag your EXE file to the terminal.

---

### Post by sunnydawn on 2010-12-07
So I opened the terminal and left a space and dragged the exe file there....the Archive manager ran for a while then i got this message.....


Archive:  /media/RS_TOTALe/setup.exe
[/media/RS_TOTALe/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/RS_TOTALe/setup.exe or
          /media/RS_TOTALe/setup.exe.zip, and cannot find /media/RS_TOTALe/setup.exe.ZIP, period.


Now not sure.  Help

---

### Post by sunnydawn on 2010-12-07
and if i try to open it with wine it says this......

The file '/media/RS_TOTALe/setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by razorbuzz on 2010-12-11
Right-click the .exe.
Select 'Properties' from the drop-down.
Choose the "Permissions" tab.
Check "Allow executing file as program".
Click "Close".

Double-click the exe, or right-click and "Open with Wine Windows Program Loader".

-RB

---

