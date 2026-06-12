---
title: "cannot access camera pictures"
date: 2011-06-25
forum: General Help
---

### Post by cadogan32 on 2011-06-25
i plugged in my camera and i get this error :

Unable to mount KODAK EASYSHARE M530 Digital Camera
Error initializing camera: -60: Could not lock the device

i tried a different fix i found in another forum but got stuck on step 5.Does anyone know what i might be doing wrong? iam using ubuntu 10.10 also.thanks

[http://ubuntuforums.org/showthread.php?t=340271&highlight=kodak+camera+usb](http://ubuntuforums.org/showthread.php?t=340271&highlight=kodak+camera+usb)

---

### Post by jerrrys on 2011-06-25
step 5 is just making a backup file.  is it not backing up?

---

### Post by cadogan32 on 2011-06-26
this is my output when i run lsusb:

Bus 002 Device 002: ID 040a:0601 Kodak Co. 

when i run the "sudo cp" command,i get this:

cp: cannot stat `/etc/udev/rules.d/45-libgphoto2.rules': No such file or directory

i looked in the /etc/udev/rules.d folder and there are 3 files (70-persistent-cd.rules,70-persistent-net.rules and readme file)

also when i plug in the camera i get 2 "kodak easyshare m530" icons on the desktop.not too sure whats going on but i cant access it.

---

### Post by jerrrys on 2011-06-26
looks like things have been changed a little since 2007.  

double click on the 70-persistent-cd.rules, does it open like its a CD?

---

### Post by cadogan32 on 2011-06-26
it just opens up as a text document for some reaason.

---

### Post by jerrrys on 2011-06-26
here it is

[http://ubuntuforums.org/showthread.php?t=1701719](http://ubuntuforums.org/showthread.php?t=1701719)

---

### Post by cadogan32 on 2011-06-26
i added the device id and vendor id but it still says its not working.I swapped both of the things and it just doesnt work.iam gonna try on a newer kernel and see if it makes a difference.

---

