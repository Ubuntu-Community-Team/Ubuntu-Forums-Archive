---
title: "Completely disabling touchpad"
date: 2010-09-12
forum: General Help
---

### Post by gcday on 2010-09-12
I have a faulty touchpad on a laptop (asus 1001) and want to completely disable it (using the machine with a mouse) - how do I do it? I can see that you can disable the touchpad for a couple of seconds but I want to switch the whole thing off.

---

### Post by gcday on 2010-09-12
Investating further it's the left hard button under the touchpad that is the problem - gpointing will disable the touchpad but not the button. Surely there must be a way to turn this off?

---

### Post by dirty_harry on 2010-09-12
I have an Asus PRO55s and used to have the same problem. Some day I update and asus-acpi worked.

Before that I used an hotlink and toggletouchpad-script source unknow:
```
state=`synclient -l | fgrep TouchpadOff | sed 's/^.*= //'`
if [ $state -eq 1 ]
then
        synclient TouchpadOff=0
else
        synclient TouchpadOff=1
fi

```If want to deactivate your touchpad completely you should be able to do that here:
Gnome > System(Menu) > Mouse(Settings) > Touchpad(tab)

As I said, I don't this anymore because asus-acpi works fine with the Asus buttons:
```
$:/# locate touchpad
/etc/acpi/asus-touchpad.sh
/etc/acpi/thinkpad-stretchortouchpad.sh
/etc/acpi/events/asus-a6u-touchpad
/etc/acpi/events/asus-touchpad
/etc/acpi/events/lenovo-touchpad
/usr/local/bin/toggletouchpad
/usr/share/app-install/icons/touchpad.png
$:/# uname -a
Linux system 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux
$:/# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

```

---

### Post by gcday on 2010-09-12
There is a physical short in the left button which is why I need to disable it completely. The mouse menu will disable the pad but not the buttons. 

Hit a button on the keyboard starts the "disable for two seconds" thing and I can select menus and the like but only for two seconds...

---

### Post by dirty_harry on 2010-09-12
Have you tried to turn it off in the bios? 


And I found the source of the script I used to have:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Here it says:
> Disabling Touchpad for X.Org **The easiest way to disable the Touchpad for X.Org system-wide, is to uninstall the package xserver-xorg-input-synaptics.**

---

### Post by gcday on 2010-09-12
> **dirty_harry said:**
> Have you tried to turn it off in the bios? 


And I found the source of the script I used to have:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Here it says:

thanks, I've uninstalled the package and yet the touchpad still works?? odd,no?

---

### Post by dirty_harry on 2010-09-12
But restarted your system? *just_guessing*

---

### Post by gcday on 2010-09-12
> **dirty_harry said:**
> But restarted your system? *just_guessing*

Yeah it's still working so something else must be driving the touchpad but what?

---

### Post by dirty_harry on 2010-09-12
used my googlefu:

[http://wiki.archlinux.org/index.php/Asus_Eee_PC_1001p#Touchpad](http://wiki.archlinux.org/index.php/Asus_Eee_PC_1001p#Touchpad)
```
**/etc/X11/xorg.conf**
...
 #Option      "Device"            "/dev/input/mice"   
Option      "Device"            "/dev/psaux"
... 
```You should try it the other way around using /dev/input/mice  as you want to use only a usb mouse.

---

### Post by llamabr on 2010-09-12
Put a screwdriver on it.

1. Take the keyboard off
2. Loosen the cover
3. lift up the touchpad
4. yank that silver wire that attaches it to the mother board
5. put it all back together

it'll never bother you again.

---

### Post by dirty_harry on 2010-09-12
Disconnecting the touchpad would be the hardcore method. :twisted: But surely more effective. 

The last time I took a notebook apart was when a friend got beer into his; it's working perfectly again. To be honest, I prefer the soft method. ;)

---

### Post by Dave_gb on 2010-09-12
Install Gsynaptics.

New menu item for Touchpad in Preferences. Uncheck 'enable touchpad'. Close.

In the 'mouse' menu item uncheck everything in the touchpad section.

Works for me :)

---

### Post by TNT1 on 2010-09-12
> **llamabr said:**
> Put a screwdriver on it.

1. Take the keyboard off
2. Loosen the cover
3. lift up the touchpad
4. yank that silver wire that attaches it to the mother board
5. put it all back together

it'll never bother you again.

Yip! What he said. I have a laptop that got soaked in the best part of a glass of red wine. I took it apart, dried it, cleaned it, dried it again, waited a month, and it all works except the touchpad. Opened it, disconnected the physical device, and use a mouse.

---

### Post by gcday on 2010-09-14
I've cracked up the case and it seems to be two dip switches for the mouse buttons, *seperate* to the trackpad controls, so I guess I'll have to literally pull it off the board...

---

### Post by gcday on 2010-09-14
> **Dave_gb said:**
> Install Gsynaptics.

New menu item for Touchpad in Preferences. Uncheck 'enable touchpad'. Close.

In the 'mouse' menu item uncheck everything in the touchpad section.

Works for me :)

Same problem with other solutions, the touchpad remains enabled.

---

### Post by the.scarecrow on 2012-10-29
> **dirty_harry said:**
> Have you tried to turn it off in the bios? 


And I found the source of the script I used to have:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Here it says:

Touchpad failure just struck my old Dell Latitude D600 and thanks to this post I was able to fix it in a jiffy.

I just went into the BIOS and disabled the touchpad, only leaving serial mouse input. Bingo! problem solved so I can wring a few more years out of this trusty old PC.

Thanks dirty_harry

---

### Post by wildmanne39 on 2012-10-30
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

