---
title: "Help with Ubuntu and Windows CE 5.0"
date: 2012-05-28
forum: General Help
---

### Post by wolf187 on 2012-05-28
Hello

I'm doing a project at the moment, I need to edit the registry and the boot files of a Windows CE 5.0 device, however the device in question has almost no GUI and resembles something similar to an old green LCD screen, the device has an ethernet port, and various serial ports for service,host and sensor. The problem is that I need to edit the registry via my system loaded with Ubuntu, I googled a few solutions, but none of which work, I am able to connect to the device using Minicom and using a Prolific USB-to-Serial adapter however I am not able to get very far as to even transfer a file, Visual Studio would have been a good choice to use but because of the lack of a keyboard and mouse and decent video there is no way to allow access to Visual Studio or other means to access this device, it uses a MSM586SEN chipset and uses a Compact Flash as a ROM, even by trying to use a PM-1033-RS-R20 vga card there is no way to boot up into a usual Windows CE system like most phones, if it is possible can someone show me how to either connect and alter the registry or even the boot file on the Windows CE 5.0 system ,the boot file is NK.BIN and is standard for all Windows CE 5.0 devices, however the only tool so far known to manipulate NK.BIN which is binmod.exe does not work even when tried in Windows. Thanks in advance for your help and sorry if any of the rules have been violated.

---

### Post by wolf187 on 2012-06-01
Just over 80 views and no help, I was able to find somewhat of a solution for it, I used the NKBINTools and used viewbin to check the contents of the NK.BIN and used the cvrtbin to convert the NK.BIN to NK.nb0 and used dumprom to extract all the compiled files, now I have to edit the NDIS.dll and NDISconfig but I have come across another problem, I am trying to clone the drives but with no avail, I have tried using dd, I used it as "dd if=/dev/SOURCE of=/dev/DESTINATION", when I mount the drives, the cloned drive shows all the data exactly the same as the source but when used on the device, it does not boot up at all, I even tried ddrescue and various other tools for Windows on these Compact Flash drives but I am getting nowhere, the drives might have some kind of write protection but somehow they still copy onto another drive, can anyone recommend any tools that can be used to clone these drives, the following programs I have used on Linux and Windows and have not worked : Acronis True Image, Clonezilla,dd,Winimage,Winhex,ddrescue,Gparted,Norton Ghost 7 and many more but I can't seem to remember them but any suggestions would help,thanks.

---

### Post by wolf187 on 2012-06-28
I have solved the cloning problem,there was an error with the source drive and dd worked fine and onto the input of the drivers into the run time image I have decided to use platform builder 5.0 and make a new version using certain properties from the older one but I have run into another problem, it has an encryption on the ftp server, I have one username and password but I need to decrypt the other,it is in some kind of code can anybody help with this, the text file with the FTP usernames and password is attached, HECUSER has a password of HECUSER but I cannot figure out the Chemtrols password,can anyone help,thanks.

---

### Post by drs305 on 2012-06-28
This moves the thread into possible hacking solutions, which is not allowed on the Ubuntu Forums. Even if your intentions are ok, the information provided could very well be used for illegal purposes. To prevent such dissemination on these forums:

Thread Closed.

---

