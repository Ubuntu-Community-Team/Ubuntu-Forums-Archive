---
title: "fn up or down screen brightness not working, acer 5750 laptop -- help please! TY"
date: 2012-02-05
forum: General Help
---

### Post by kaisar89 on 2012-02-05
Hi, i just bought a new acer 5750 laptop and decided i would like to dualboot the laptop with window 7. so far its a right pain in the ***. 

can anyone tell me on how to adjust the brightness. fn+ up/down does not work nor does brightness menu.
any help????

also is there a way to make ubuntu startup menu look similar to linux mint???

and finally...

is there something similar to aero like in windows 7 ????????

thanks in advance.:popcorn:

---

### Post by techvish81 on 2012-02-05
> **kaisar89 said:**
> Hi, i just bought a new acer 5750 laptop and decided i would like to dualboot the laptop with window 7. so far its a right pain in the ***. 

can anyone tell me on how to adjust the brightness. fn+ up/down does not work nor does brightness menu.
any help????

also is there a way to make ubuntu startup menu look similar to linux mint???

and finally...

is there something similar to aero like in windows 7 ????????

thanks in advance.:popcorn:



the fn keys sometimes work in a different manner than in windows, in my sony vaio it works by pressing both , while in hp mini they work by just pressing the fn key first and then the corresponding keys, no need to press them simultaneously. so you should try some ways and also see the bios if there is something related to fn keys.


you cannot get the exact win7 aero theme look with ubuntu but a somewhat similiar look in kubuntu.

---

### Post by kaisar89 on 2012-02-05
> **techvish81 said:**
> the fn keys sometimes work in a different manner than in windows, in my sony vaio it works by pressing both , while in hp mini they work by just pressing the fn key first and then the corresponding keys, no need to press them simultaneously. so you should try some ways and also see the bios if there is something related to fn keys.


you cannot get the exact win7 aero theme look with ubuntu but a somewhat similiar look in kubuntu.
ty, how do i check the bios?

---

### Post by techvish81 on 2012-02-05
it is different in different computers , you have to press f1, f2 , esc, or del key whichever works for you at the startup , you will have to keep pressing those keys to enter the bios setings , "DONT CHANGE ANYTHING" if you dont know what it means.

---

### Post by Toz on 2012-02-05
Try the following kernel parameters (one at a time) to see if they enable the fn brightness keys:

**acpi_backlight**

**acpi_osi=Linux** 

**acpi_osi=Linux acpi_backlight**

Instructions for doing so are here: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot").

Make sure you add the parameters to the end of the line that contains "ro quiet splash" so that it looks something like:

"..... ro quiet splash acpi_backlight=vendor" 
_or_
"..... ro quiet splash acpi_osi=Linux" 
_or_
"..... ro quiet splash acpi_osi=Linux acpi_backlight=vendor"

If you find one that works, you can make the change permanent by editing the /etc/default/grub file to include the parameter that works and then running:
```
sudo update-grub
```

---

