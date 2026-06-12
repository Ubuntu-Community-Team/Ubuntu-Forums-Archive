---
title: "xmodmap"
date: 2009-08-07
forum: General Help
---

### Post by AnarchyMaster on 2009-08-07
i'm trying to remap my keyboard with xmodmap but for some reason shift isn't changing what is being placed ( shift + f1 is still 1 )
```
#!/bin/bash


xmodmap -e "keycode 68 = 2 quotedbl 2 quotedbl twosuperior oneeighth"
xmodmap -e "keycode 92 = 0xFFE9"
xmodmap -e "keycode 49 = Tab"
xmodmap -e "keycode 70 = 4 dollar 4 dollar EuroSign onequarter"
xmodmap -e "keycode 67 = 1 exclam 1 exclam onesuperior exclamdown"

```

can anyone help?

Thanks

---

### Post by Icebear on 2009-08-07
I use xkb to change the keyboard this might help you for normal keys.

Go to X11/symbols directory, 	by typing cd /usr/share/X11/xkb/symbols
then find layout you want to change

for example ru (for Russian)

make a backup of the selected file,	sudo cp ru ru_backup
then load the file up to edit,	sudo gedit ru

find the section you want in it to change 
in my case the phonetic layout

then swap changes you wish to make

for example: from
key	<LatV> {	[    Cyrillic_zhe,    Cyrillic_ZHE	]	};
to
key	<LatV> {	[    Cyrillic_ve,    Cyrillic_VE	]	};

If you want to add a  2nd letter to a key then at the spot where it describes the level

in the Russian phonetic spot change the level from ALPHABETIC to FOUR_LEVEL_ALPHABET or  FOUR_LEVEL

for example from
key.type[group1]="ALPHABETIC";
to
key.type[group1]="FOUR_LEVEL_ALPHABETIC";

and at the key add the letter you want to change after the first two settings.

You can use unicode numbers also instead of names. (Don't use the +  sighn  ie. U4C7)

from
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN	]	};
to
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN,	U04C8,		U4C7	]	};

then save

Then go System>preferences>Keyboard

then click layout options
then click the other options button
then choose third level choosers
and choose button you wish to use for the 2 
To get the 2 letter while typing hold down the 3rd level key plus the key you want to use and for capital hold shift as well

next time you log in it should work
It would be most likely best not to experiment on the default language until you tried your changes on a second language keyboard.

---

### Post by AnarchyMaster on 2009-08-08
Ahhh, worked a charm!

thank you very much!

---

### Post by davegk on 2009-08-10
Brilliant! Thanks, Icebear.
 
Not only I managed to get rid of German accent in RU Phonetic (i.e. W=V ... not!), moved the hard sign to a single key (backslash), but I also put [@] [£] [$] ["] in their rightful places (as in the UK layout) and added the number sign. Great! 
 

 Thanks again.

---

