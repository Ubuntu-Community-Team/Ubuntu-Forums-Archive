---
title: "Xsane permissions, run as root"
date: 2010-09-01
forum: General Help
---

### Post by BrockStrongo on 2010-09-01
Hi Everybody

    How would I change the permissions for a specific program(xsane)? For some reason Xsane only works now if I run as root. It was working fine before the latest kernel update, now I get "cannot start scanner: invalid argument" unless I run the program as root. Also images that are scanned are nor accessible unless I am root
   Any help would be greatly appreciated

Epson Stylus NX215
Ubuntu 10.04 64 bit
The printing feature works fine still.
Iscan is installed from avasys.jp
Rolled back to old kernel and problem still exists

---

### Post by arrange on 2010-09-01
I really don't know, but if nobody comes up with a better idea, you can try running *xsane* like this (from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)):```
strace xsane 2>&1 | grep EACCES | sort -u
```We might be able to see what is holding *xsane* back :D

---

### Post by BrockStrongo on 2010-09-01
It looks as though /dev/bus/usb is not allowing me to use the scanner.
I remember seeing a post that used chmod a+w or something like that to change permissions, but, I can't seem to find it again.
What do you think? 
open("/dev/bus/usb/001/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/001/002", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/001/003", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/002/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/003/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/004/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/005/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/006/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/002", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/003", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/004", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/007/005", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/bus/usb/008/001", O_RDWR)    = -1 EACCES (Permission denied)
open("/dev/port", O_RDWR|O_NOCTTY)      = -1 EACCES (Permission denied)
open("/dev/sg0", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg2", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg3", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
open("/dev/sg4", O_RDWR|O_NONBLOCK)     = -1 EACCES (Permission denied)
mike@mike-laptop:~$

---

### Post by BrockStrongo on 2010-09-01
Thanks for all your help,
I've tried changing the permissions on each folder /dev, /bus/ and /usb I've tried changing the read and write permissions, I've tried changing the owner, but I must be missing something. The funny thing is the program worked fine the last time I used it , (about a month ago) so I don't really know what has changed since then

---

### Post by BrockStrongo on 2010-09-01
Well, I found a solution to my problem :) My problem being Xsane would give me the error "failed to start scanner : invalid argument"
1. sudo gedit /etc/sane.d/dll.conf 
         remove the # from the line that reads #epson
2. sane-find-scanner
        make a not of the line "found USB scanner (vendor=0x04b8, product=0x084f) at libusb:002:003" the vendor and product id's were what I needed
3. sudo gedit /etc/sane.d/epson.conf
       replace the line that reads "usb" with "usb 0x04b8 0x084f"
        the product and vendor id's will vary depending on what scanner you have
4.   sudo /etc/init.d/saned restart
Now when Xsane starts I'm presented with a screen asking me to select the scanner I want. I select Epson PID and VOILA scanner works.

I don't know if this is the right way to do it, but, don't look a gift horse in the mouth.

These directions are almost the same as the ones I found in [http://maxolasersquad.blogspot.com/2009/11/scanning-problems-in-ubuntu-karmic-910.html](http://maxolasersquad.blogspot.com/2009/11/scanning-problems-in-ubuntu-karmic-910.html) the only difference being the location of the dll.conf and epson.conf files. So many thanks to MAXO
TALLAHASSEE, FL, UNITED STATES

---

### Post by trukker on 2010-10-19
Had same problem when upgrading to Maverick... seems an upgrade problem...

Solved as above! :popcorn:

---

### Post by mcrimea on 2010-11-18
> **BrockStrongo said:**
> Well, I found a solution to my problem :) My problem being Xsane would give me the error "failed to start scanner : invalid argument"
1. sudo gedit /etc/sane.d/dll.conf 
         remove the # from the line that reads #epson
2. sane-find-scanner
        make a not of the line "found USB scanner (vendor=0x04b8, product=0x084f) at libusb:002:003" the vendor and product id's were what I needed
3. sudo gedit /etc/sane.d/epson.conf
       replace the line that reads "usb" with "usb 0x04b8 0x084f"
        the product and vendor id's will vary depending on what scanner you have
4.   sudo /etc/init.d/saned restart
Now when Xsane starts I'm presented with a screen asking me to select the scanner I want. I select Epson PID and VOILA scanner works.

I don't know if this is the right way to do it, but, don't look a gift horse in the mouth.

These directions are almost the same as the ones I found in [http://maxolasersquad.blogspot.com/2009/11/scanning-problems-in-ubuntu-karmic-910.html](http://maxolasersquad.blogspot.com/2009/11/scanning-problems-in-ubuntu-karmic-910.html) the only difference being the location of the dll.conf and epson.conf files. So many thanks to MAXO
TALLAHASSEE, FL, UNITED STATES

My ACER ASPIRE ONE with LUCID LYNX for netbook cannot detect my EPSON Perfection 4490 Photo scanner. The above did not work. Neither does running xsane as root. 

sane-find-scanner does detect alright.  (04b8 0119)

Avasys Image Scan! for 4490 scanners also does not detect the scanner. 

From my desktop (not the ACER netbook) LUCID LYNX works with the scanner just fine.

So the bottom line for me is that ACER and LUCID LYNX and EPSON 4490 don't work together.

---

### Post by BoBeau on 2010-12-08
I tried the above, but Xsane still does not recognize my scanner.  I have an all-in-one Epson 415.  The printer works fine.  I have tried everything I can possibly find to get the scanner working but nothing works.  I have to reboot under Windows every time I need to scan something.

I am a serious Newbie, and I need help!

---

### Post by drrob1 on 2011-11-20
I don't know if this is too late, but I ran 
 ```
lsusb
```

and found that my Brother MFC 7420 is at bus 007 device 002.  Then
  ```
chmod a+w /dev/bus/usb/007/002
```

and now xsane works as a normal user.  I don't have to be root.

Hope this helps

---

### Post by drrob1 on 2011-11-20
Oddly I get an error when I exit xsane that the output files were not created because of a permission problem.

But the files **_are_** created.  So I'm ignoring the error.

---

### Post by joham34 on 2012-05-01
> **drrob1 said:**
> I don't know if this is too late, but I ran 
 ```
lsusb
```

and found that my Brother MFC 7420 is at bus 007 device 002.  Then
  ```
chmod a+w /dev/bus/usb/007/002
```

and now xsane works as a normal user.  I don't have to be root.

Hope this helps

Your solution was straightforward. Many thanks !

---

### Post by goulo on 2012-12-21
Following advice from [http://www.sane-project.org/README.linux](http://www.sane-project.org/README.linux)

I solved this apparently more "correctly" by adding the desired users to the "scanner" group, e.g. to let user "goulo" scan,

**sudo usermod -a -G scanner goulo**

(and then the user needs to login again for it to take effect).

---

