---
title: "How to setup my Logitech Wave wireless keyboard+mouse?"
date: 2009-08-15
forum: General Help
---

### Post by mirkko22 on 2009-08-15
Hello

It is now more then 1 years I am under Ubuntu and using Logitech Wave wireless keyboard+mouse without problem...I have setup keyboard and device and all worked fine until fiew days ago. It seem last ubuntu update have make some change inside xorg.conf because I get problem with this devices...If a put a standard mouse+keyboard non wireless and no usb I don't get any problem...

I have open my current xorg.conf and here is the param about mouse and keyboard:

> # commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"ch"
#	Option		"XkbVariant"	"fr"
#	Option		"XkbOptions"	"lv3:ralt_switch"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"	"false"
#	Option		"Buttons"	"7"
#	Option		"ButtonMapping"	"1 2 3 6 7"
#	
#EndSection

My past xorg.conf was exactly the same except all param are commented and not uncommented like in this new xorg.conf....I see also a new line telling "commented out by update-manager, HAL is now used"...So it's the update manager have uncomment the config...but why ?? And what mean "HAL is now used" ??

I have try to comment all param and I get problem...My keyboard write alone and my mouse can move but can't click in any place...

Any suggestions ??

Thank

---

