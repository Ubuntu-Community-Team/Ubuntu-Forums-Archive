---
title: "How can I use a Custom Keyboard Layout ?"
date: 2009-08-14
forum: General Help
---

### Post by vaerer on 2009-08-14
How can I use a custom keyboard layout?

I've been reading [http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html)

However none of the files he talks about exist on my system :confused:

---

### Post by soapBAR2 on 2009-08-14
I'm not quite sure what you mean by custom keyboard layout. Are you trying to switch keyboard layouts, eg, to Dvorak, or to an international QWERTY variant? Or are you trying to bind SOME keys to extra functions (eg, you could bind F12 to launch some program). If the latter, you want to look into xbindkeys. If the former, you want to edit your /etc/X11/xorg.conf and add the relevant Options. If you're using the driver kbd (as I am in my xorg.conf), you can check the manpage for kbd (man kbd) to see what options are valid.

So, in /etc/X11/xorg.conf, change

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"      
EndSection          

to

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"      
    Option         "XkbLayout" "YourLayoutName"
    Option         "XkbVariant" "YourVariantName"
EndSection

Or whatever it is that you want. 

PS. A list of valid keyboard layouts can be found in /usr/share/X11/xkb/rules/xorg.lst

---

### Post by vaerer on 2009-08-14
By custom I mean that I want to define my own layout.

I'll probably base it on US Dvorak Classic, but I need a Pound sign (which I can't type right now), an inverted number pad like mobile phones use and a few other things. (I want to have full control of what happens when I click a key.)

So what I need to know is:
Where can I get a copy of the layouts that are already installed and, 
After modifying one, how can I use/register/install the modified version as a layout that the system will recognize.

I'd like the modified layout to be the default so I can use it if I get stuck in single user mode, is that possible?

---

### Post by kyrandesa on 2009-10-01
have you managed yet? I'd like to do something similar to the English layout, rearranging all the symbols to more 'memorable' places

---

### Post by tmetro on 2009-12-12
> **vaerer said:**
> 
I've been reading [http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html)

However none of the files he talks about exist on my system :confused:

Perhaps the article has been updated, but it seems to refer to the new file locations and names that are applicable to Ubuntu 9.04.

See also:
[http://blog.knuthaugen.no/2009/07/keyboard-layout-and-remapping-for-fun-and-profit.html](http://blog.knuthaugen.no/2009/07/keyboard-layout-and-remapping-for-fun-and-profit.html)

 -Tom

---

