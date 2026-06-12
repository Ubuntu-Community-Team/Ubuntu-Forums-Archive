---
title: "Can I delete default files on new usb drive?"
date: 2009-12-01
forum: General Help
---

### Post by linuxNewb on 2009-12-01
I just got a Toshiba Portable USB Drive, and I was thrown a bit because when I plugged in the USB cable, Ubuntu didn't do anything (mount it, or even recognize a new device). I had to (re)boot with the drive plugged in for Ubuntu to recognize it. I'm pretty sure that this is just how these portable USB drives work, and it's not an Ubuntu issue.

That being said, now I'm questioning everything that I know about external drives, and I need someone to hold my hand, and tell me that I can safely delete all of the default files on my new usb drive such as autorun, icon, and '.dmg' files without breaking it. Thanks for your patience :)

---

### Post by audiomick on 2009-12-01
Hallo.
You probably can if it is only ever going to go into a Linux computer, but I am _**geussing !**_

The other consideration is, if there is any chance you might want to plug it into a Windows computer ever, leave them there. They are probably there to install the windows drivers for the drive.

---

### Post by linuxNewb on 2009-12-01
Thanks for your quick response. Now I'm glad I asked -- I didn't even think of that.

---

### Post by audiomick on 2009-12-01
Glad to help.
Put a solved tag on the thread, wont you? In the thread tools at the top.:D

---

### Post by TheOnlyMrK on 2009-12-01
You don't need any of those files at all weather you use Ubuntu or Windows with it, by what you described the files it is software that came on the hard drive, "autorun" is the file that automatically starts the software when you plug it into a Windows computer, and ".dmg" are Mac files.
So basically if you don't use a Windows or Mac computer and/or don't care about the included software delete the files.

---

### Post by gnicko on 2009-12-01
If you intend to just use the drive for storage purposes or moving documents from one system to another you won't need them. You only really need those files if you want to run programs--kind of like a "live CD" set up--from the USB drive in Windows (and/or maybe Mac, but I suspect that the Mac folks have different sets of files.) You can delete them (or format the drive) if you want to. 

If you format the drive FAT32 (or even FAT16) you should be able to use it on Windows, Linux and Macs (I think) too.

If you do decide that you need the pre-installed files, you will have to find another source to get them back from. Last time I had to do that I found a free Windows program on the Hewlett Packard site to format the USB drive and format it for "live" use. Same principle for Linux, etc. You can do it with gPartEd [Gnome Partition Editor] if you have it installed or maybe the Start-up Disk Creator app.

Whichever actions you decide to take, you won't "wreck" the USB drive--you just might have to go thru an extra step or two if you change your mind. I format and re-format mine all the time and, except for formatting with a Linux filesystem, which Windows just won't do, they give me no problems jumping from one O/S to another.

---

