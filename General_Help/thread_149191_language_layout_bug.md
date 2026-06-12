---
title: "language layout bug?"
date: 2006-03-23
forum: General Help
---

### Post by damu on 2006-03-23
I use both english and french on a daily basis.
So I installed the fr package trhough synaptic.
I also have the Keyboard indicator in my toolbar.

But...

I can't switch from one language to another without right click on the indicator/open Keyboard preferences/ Layouts, tick one language and untick the other one/ move up the selected one.

And after all that, when I select french, the only result is that gnome ponder for a while, becomes blue for few seconds, and greats me with an indicator which indicates "Fra"...Great, but my keyboard is still with an english layout.

ps : when I right click/layout View, the layout displayed is french 

Any help very much appreciated. I did a text file of special characters, but writting letters with Ctrl C / Crtl V for each special character drives me N..

---

### Post by ububaba on 2006-03-23
[QUOTE=damu]I use both english and french on a daily basis.
So I installed the fr package trhough synaptic.
I also have the Keyboard indicator in my toolbar.

But...

I can't switch from one language to another without right click on the indicator/open Keyboard preferences/ Layouts, tick one language and untick the other one/ move up the selected one.

And after all that, when I select french, the only result is that gnome ponder for a while, becomes blue for few seconds, and greats me with an indicator which indicates "Fra"...Great, but my keyboard is still with an english layout.

ps : when I right click/layout View, the layout displayed is french 

Any help very much appreciated. I did a text file of special characters, but writting letters with Ctrl C / Crtl V for each special character drives me N..[/QUOTE]

Hi,

Please open */etc/X11/xorg.conf* in a text editor, then locate "InputDevice"
and change the letters **gb** to **fr** (for French). After the change, save the file. 
This will give you a French keyboard layout. 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"**gb**"

---

### Post by damu on 2006-03-23
Thanks for your help.
I  > sudo gedit /etc/X11/xorg.conf
changed Option > "XkbLayout" "gb" to
> Option "XkbLayout" "fr"
and saved.

I still have an english keyboard layout though.

Another issue is that I changed many times a day, as I email people in france and Uk, so I would need the possibility to switch from one to the other...

:-k

---

### Post by ububaba on 2006-03-24
[QUOTE=damu]Thanks for your help.
I  
changed Option  to

and saved.

I still have an english keyboard layout though.

Another issue is that I changed many times a day, as I email people in france and Uk, so I would need the possibility to switch from one to the other...

:-k[/QUOTE]

Changing like that helped me to switch to another keyboard. Hower I have 
not found a method for quick change over from one to another layout. 
Hope someone who knows more will be able to help.

---

