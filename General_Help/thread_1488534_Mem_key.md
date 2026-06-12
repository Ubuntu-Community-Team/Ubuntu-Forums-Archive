---
title: "Mem key"
date: 2010-05-20
forum: General Help
---

### Post by Sarraband on 2010-05-20
I'm using 10.04 and it doesn't want to recognize my Movin key memup 4gb stick. It only sees it when I plug it in to a usb hub, but then won't let me write to it or store anything on it? Any ideas appreciated because it said Linux compatible on the packaging?

---

### Post by ubunterooster on 2010-05-20
open the drive and right-click in it. Select properties and go to the "permissions" tab. Whaat does it say?

---

### Post by Sarraband on 2010-05-21
Hi, it says,"the permissions of movin key could not be determined".

---

### Post by ubunterooster on 2010-05-21
go to system>administartion> Disk Utility. format the drive. This should take care of all permissions but all data on the drive will be lost.

---

### Post by Sarraband on 2010-05-22
Ok, I did that after transfering all my needed stuff to my external hard drive, but I keep getting the same thing here's some more info
If I go in to the user manual it tells me to do this :       Linux Kernel 2.4 install mode
Go to the system's root directory. To install USB flash drive type: "mount/dev/sda1/mnt". For unloading USB flash drive
type: "umount / mnt". When I do this from the terminal it just says command not found
My computer will not recognize the drive on its own, but only with a usb attachment whereupon it comes up with the Movin Key icon as well as a Public Icon If I open the movin key icon, all it gives me is manuals and a memory bar. exe file which gives me this when I try to open it: rchive:  /media/Movin key/Memorybar.exe
[/media/Movin key/Memorybar.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/Movin key/Memorybar.exe or
          /media/Movin key/Memorybar.exe.zip, and cannot find /media/Movin key/Memorybar.exe.ZIP, period.

If I try the autorun inf file I get this, which does nothing in a terminal : [Autorun]      

icon=Movin key.ico

label=Movin key

My computer is a quad core Acer Aspire if that's of any importance
Getting really hacked off now because my MP3 player refuses to be written to now, whereas it worked fine before, also because i haven't permissions and I don't have permissions to read "apt"?

Um, it all seems like a permissions/read write problem, no?
Cheers for any help.

---

### Post by ubunterooster on 2010-05-22
run ```
gksu nautilus
```

This will start nautilus as root, allowing you unrestricted access to files and folders. You should also be able to change permissions easily when running nautilus as root.

---

### Post by Sarraband on 2010-05-25
> **ubunterooster said:**
> run ```
gksu nautilus
```

This will start nautilus as root, allowing you unrestricted access to files and folders. You should also be able to change permissions easily when running nautilus as root.

Thanks for the help, works ok now.:)

---

