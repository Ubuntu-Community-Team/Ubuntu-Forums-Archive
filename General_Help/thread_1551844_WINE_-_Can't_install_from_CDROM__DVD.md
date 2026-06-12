---
title: "WINE - Can't install from CDROM / DVD"
date: 2010-08-12
forum: General Help
---

### Post by cosmolee on 2010-08-12
Wine 1.1.42  Ubuntu 10.04

I'm having trouble installing a program from the CDROM / DVD drive. I've checked to see that the mapping of the d: drive is correctly pointing to the right place - it is: 

~/.wine/dosdevices$ ls -l 
total 0 
lrwxrwxrwx 1 cosmo cosmo 10 2009-10-04 18:46 c: -> ../drive_c 
lrwxrwxrwx 1 cosmo cosmo 13 2010-08-12 20:19 d: -> /media/cdrom0 
lrwxrwxrwx 1 cosmo cosmo 8 2010-07-25 19:12 d:: -> /dev/sr0 


I run the install program, it runs from the DVD as expected: 

~/.wine/dosdevices$ wine start d:\Komplete\ 6\ Setup\ PC.exe 



However, after answering the setup questions (storage directories, etc - I don't change anything, I just accept the defaults), once it gets to the point of actually installing the software, a pop-up alert says "Disk Not Found", "Please insert Komplete 6". The disk it is asking for is the same one I've run the installation program from, so I don't understand why it can't see those files. It's obviously seeing the DVD since it's running the installation program from it... 

Any ideas?? 

Thanks much for any help...Cosmo

---

