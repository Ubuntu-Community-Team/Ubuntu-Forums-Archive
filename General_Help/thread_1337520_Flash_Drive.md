---
title: "Flash Drive"
date: 2009-11-25
forum: General Help
---

### Post by tchayden on 2009-11-25
Hello every one,
I am a new user to Ubuntu and I can't seem to get my flash drive to work. It gives me an icon on the desktop when I plug it into the USB port.  But it won't let me extract any files or load any of the software.  If anybody has any answers that would be great!

Thank you and have a great holiday!

---

### Post by wilee-nilee on 2009-11-25
Right click on icon then properties and see if it has read and write enabled. Also you can probably format it with gparted if nothing is on there, how big is the memory?

---

### Post by tchayden on 2009-11-26
it is an 8 GB SanDisk but there is only 28 megabytes stored on it.

---

### Post by tchayden on 2009-11-26
I went into properties and it says it is a read only file tried to change it and it gives me an error and says I am not allowed to do this. It is a DOS/Windows program, if that means anything. should i be using archive manager or is there something else I should be using to open this file that i don't have or should be using?

This is the error i get when i try double clicking on LaunchU3.exe:

Archive:  /media/U3 System/LaunchU3.exe
[/media/U3 System/LaunchU3.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/U3 System/LaunchU3.exe or
          /media/U3 System/LaunchU3.exe.zip, and cannot find /media/U3 System/LaunchU3.exe.ZIP, period.

---

### Post by audiomick on 2009-11-26
Hallo.
It looks like you are trying to start a windows programme ( LaunchU3.exe ) in Ubuntu. You can't because windows executables ( anything.exe ) don't run in Linux, and don't need to.

What you are seeing ins more than likely a windows driver for the flash drive. Just leave it ther, you'll need it when you plug the drive into a windows computer.

That you get this:

Archive: /media/U3 System/LaunchU3.exe
[/media/U3 System/LaunchU3.exe]

indicates that your computer has found and mounted the drive. Are you sure you can't write to it? Have you tried saving something to the drive, or just  deleting that .exe file?

---

### Post by tchayden on 2009-11-26
what i am trying to do is open it up and transfer some files from windows to Ubuntu so i can eventually get rid of windows on this computer. So what you are saying is that i will never be able to open the flash drive on a Linux based system?

Yeah when i go into properties it says read only and when i try to change it to read and write it gives me an error and doesn't allow me to. I can't save anything to it cause i can't open the flash drive to get to any thing. 

the icon goes away when i remove the flash drive from the USB port.

---

### Post by XCan on 2009-11-26
You may have to change the permissions as root, depending on the ownership when it is mounted. Try ```
 gksudo nautilus 
``` and go back into properties and uncheck the read-only flag. Note that if this mode works and you decide to transfer files in this mode, your copied files may need ownership change, but we'll cross that bridge later.

---

