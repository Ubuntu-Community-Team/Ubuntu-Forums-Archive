---
title: "Invert function behaviour on HP notebook (pb_fnmode=2?)"
date: 2011-07-23
forum: General Help
---

### Post by Mguel on 2011-07-23
Hi,

I've recently bought a HP Pavilion dm1 3060la, in which I installed lubuntu (the problem is also on other ubuntu variants, so I used all variants prefix).

And the keyboard layout uses the (I believe) Mac style function keys, in which to get the actual ie F2 function to rename, you have to press fn+F2... and if you press F2 alone you get a lower screen brightness... which is so screwed imo (HP fault).

So the question is how can I change the Function key behaviour to the normal one?

I've searched the issue and I only have come across solutions for Mac users which don't work on HP notebook like the ones on: [https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard) or adding "options hid pb_fnmode=2" to /etc/modprobe.d/options.save (which doesn't exist on my notebook) or adding "options hid_apple fnmode=2" to /etc/modprobe.d/

Any help is much appreciated.

Best regards,
Mguel

PS: here is a pic of the same notebook/keyboard that I have that I found on internet just in case: [http://bubert.cl/fotos/3.jpg](http://bubert.cl/fotos/3.jpg)

---

### Post by Mguel on 2011-10-16
OK, on the BIOS you can revert to "normal" behaviour of function keys, disabling the "Action Keys Mode"

as it is explained here: [http://goo.gl/nhmP4](http://goo.gl/nhmP4)

[IMG]http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c02035200.jpg[/IMG]

---

