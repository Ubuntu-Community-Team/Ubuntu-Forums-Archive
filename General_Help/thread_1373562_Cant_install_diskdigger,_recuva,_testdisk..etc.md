---
title: "Cant install diskdigger, recuva, testdisk..etc"
date: 2010-01-05
forum: General Help
---

### Post by james_holiday on 2010-01-05
[FONT=Calibri][SIZE=3]Hi everyone [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Im having a real hard time installing diskdigger, recuva, testdisk..etc on my ubuntu[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Because I cant seem to get the Internet to work, I’ve downloaded them on another computer and put them on a USB stick and then into the ubuntu computer..[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Problem is whenever I try to open any of the files, it will try to open it up in Archive Manager and an error soon occurs…[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]“An error occurred while loading the archive.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Command Line Output[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Archive: /media/USB DISK/rcsetup134.exe[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/media/USB DISK/rcsetup134.exe][/SIZE][/FONT]
[FONT=Calibri][SIZE=3]End of central directory signature not found. Either this file is not a zipfile, or it constitutes one disk of a multi part archive..”[/SIZE][/FONT]

---

### Post by michy99 on 2010-01-05
Usually an .exe file is for Windows and will not work on a linux system. You need the linux version of the software.

---

### Post by james_holiday on 2010-01-05
Hey I downloaded and installed the linux version.. The Ubuntu 9.04, but its still doing the same old thing..

---

### Post by james_holiday on 2010-01-06
Does anyone have any idea what im doing wrong?
 
Its the Ubuntu Linux version and its still coming up with..
 
End-of-central-directory signature not found. Either this is not a zipfile or it constitutes one disk of a multi-part archive. In the latter case the central directory and zipfile coment will be found on the last disk(s) of this archive.
 
 
Any thoughts?

---

### Post by Matt_616 on 2010-01-11
I don't know about the others, but Recuva is a Windows only app. so far.  I'm currently trying it through Wine, and will update my post when i have more information.


EDIT:
Recuva will install VIA Wine emulator, but will give cryptic errors when trying to scan.  I assume that the file structure of Ubuntu is too different from that of Windows, and Recuva cannot find the filepaths needed through the use of Wine.

(Running Karmic, fully Updated)

---

### Post by Leppie on 2010-01-11
the testdisk .deb you can download here: [http://packages.ubuntu.com/karmic/testdisk](http://packages.ubuntu.com/karmic/testdisk)

---

