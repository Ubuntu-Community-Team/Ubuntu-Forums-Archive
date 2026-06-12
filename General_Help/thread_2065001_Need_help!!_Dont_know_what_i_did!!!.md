---
title: "Need help!! Dont know what i did!!!"
date: 2012-09-30
forum: General Help
---

### Post by timjacmor on 2012-09-30
:confused:  UM COULD I GET SOME HELP I'M A NEWBIE AND I WANTED TO FORMAT MY USB SO I USED GPARTED NOW THIS LAPTOP WON'T READ IT!!!

---

### Post by Bashing-om on 2012-09-30
timjacmor; Hi ! Welcome to the forum .

In GParted ...what actions did you take ? In Gparted, what did you format the device to ?

Does GParted recognize the device ?

[INDENT]I will try <==BDQ

[/INDENT]

---

### Post by timjacmor on 2012-09-30
umm... i formated it to fat32...
my xbox and ps3 read it...
yes, gparted sees it

---

### Post by Bashing-om on 2012-09-30
ok ....in terminal with the usb devise inserted post output of:
```
sudo fdisk -lu
```(that is a lower case "L") 

as it is formated fat32 this may relate:
[http://support.microsoft.com/default...b;en-us;314463](http://support.microsoft.com/default...b;en-us;314463)

the 4GB limit may apply.
[INDENT]try'n to help <==BDQ


[/INDENT]

---

