---
title: "keyboard problem with laptop"
date: 2006-03-18
forum: General Help
---

### Post by ozkan on 2006-03-18
i installed ubuntu breezy badger  to my laptop , my laptop's keyboard is Turkish . when i am using my ubuntu,  i cannot put some caracteres such as " @ " . when i try to change system>preferences> keyboard>layout  i am takins some error like  this : 
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

actully i am always taking this error when i  am changing a keyboard configuration.

---

### Post by ozorba on 2006-03-18
Here is how you do it:

1.  sudo gedit /etc/X11/xorg.conf

find the following in the file:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"

and change 

Option "XkbLayout" "us"

to 

Option "XkbLayout" "us,tr"

Save and exit.

2. In GNOME Application Menu

select

System Tools > Configuration Editor 

and in the left window select

 desktop > gnome > peripherals > keyboard > kbd

select 'layout' in the right window and Add 'tr' without quotes.

This will result qwerty Turkish keyboard.




----

---

### Post by ozkan on 2006-03-18
well at least i have every caractere at the keyboard for exemple @ : is shift-2  but there is no turkish keyboard. 
there is a option 
 option variable q     ,what is that ? are they different  `systemtools>configuration editor>gnome>desktop> and System >preference>keyboard

---

### Post by ozorba on 2006-03-18
if your /etc/X11/xorg.conf  file have the following lines:

Code:

Section "InputDevice"
  Identifier   "Generic Keyboard"
  Driver      "kbd"
  Option      "CoreKeyboard"
  Option      "XkbRules"   "xorg"
  Option      "XkbModel"   "pc105" < pc105 or pc 102 maybe pc104
  Option      "XkbLayout"   "tr"
  Option      "XkbVariant"   "q"
EndSection

You will need to comment out or remove the following line.

 Option      "XkbVariant"   "q" 

Then your coder should be :
Code:

Section "InputDevice"
  Identifier   "Generic Keyboard"
  Driver      "kbd"
  Option      "CoreKeyboard"
  Option      "XkbRules"   "xorg"
  Option      "XkbModel"   "pc105"
  Option      "XkbLayout"   "tr"
EndSection

If this has not solved your problem try the following.

sudo dpkg-reconfigure locales
and select tr_TR ISO-8859-9, tr_TR.UTF-8 UTF-8 as well.

I assume that your have added tr to

Desktop->gnome->peripherals->keyboard->kbd

and restarted GNOME by pressing Ctrl-Alt-Backspace

--

---

