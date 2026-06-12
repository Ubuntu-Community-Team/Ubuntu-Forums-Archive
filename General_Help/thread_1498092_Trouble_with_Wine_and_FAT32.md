---
title: "Trouble with Wine and FAT32"
date: 2010-05-31
forum: General Help
---

### Post by X-Windows on 2010-05-31
I'm sure many of you are running wine, so I'll ask here. I am dual-booting Ubuntu and Windows and would like to run my Windows apps through wine. I have a ntfs partition for windows, a ext4 partition for Ubuntu and the rest of my HD is fat32 for storage. I have been trying to install all my windows apps to this fat32 partition so I can run them on either OS. Things are working fine on the windows end, but every time I install to the fat32 partition Wine is unable to run the app. I have tried installing a working app on wine's C: drive and it works perfectly, but if I put it on the fat32 partition it throws a generic "report this as bug" error. Does anyone know a way to install apps so they can work on either OS without forcing them to be installed to the operating system's partition? I tried moving wine's C drive to the fat32 to no avail.

---

### Post by X-Windows on 2010-05-31
Update:

I copied the drive_c file from /home/.wine to a new ext4 partition, renamed the origional, and created a link to the new partition's drive_c folder. As far as I can tell this should get things working, wine sees the link, writes to it like it always does, but all the data goes to the new partition's drive_c folder. Works in theory. However when I run a Setup.exe program it displays the splash screen fine, but when I click on an Install button, I get an error  "The program IKernel.exe has encountered a  serious problem and needs to close". Any idea why this is happening or what can be done to fix it? From what I can tell everything *should* be working perfectly. :confused:

---

