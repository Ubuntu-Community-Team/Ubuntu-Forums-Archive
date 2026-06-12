---
title: "ati drivers black screen trying to go back to vesa but no xorg config"
date: 2010-12-04
forum: General Help
---

### Post by slpixe on 2010-12-04
hey,

Was trying to play some new games, so was trying to install the ati drivers for my x15xx or something card.

anyway i am using ubuntu 10.10, so was having to try force them, using 9.10 config or something.

anyway got it installed, restarted and I get black screen

have been trying to go back to "vesa" drivers or something.

but been having no luck

I do not have a "/etc/X11/xorg.conf". and I cannot seam to make 1 using stuff like aticonifig --initial --input=/etc/X11/xorg.cong

or anything like that

I am really stuck, even using dpkg-reconfigure or something didnt make the X11 conf

---

### Post by slpixe on 2010-12-05
any sort of help would be great.
e.g. idea on how to generate a xorg.conf, or how to switch it to the default drivers
or set it to vesa somehow ?

---

### Post by slpixe on 2010-12-08
just telling me a simple command I can type in to set graphics to use vesa?
or even if I go into support mode, anything easy I can change to put it to the preliminary drivers ?

---

### Post by matt_symes on 2010-12-08
Hi

Have a look at this page

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

and then you will want to change the driver to vesa. I.E something along the lines of (ensure everything matches)

Section "Device"
    Identifier     "Device0"
    **Driver         "vesa"**
EndSection

and then move it to

/etc/X11/

If in doubt post the Xorg.conf file on here before using.

Kind regards

---

### Post by slpixe on 2010-12-08
Hey matt_symes thanks for the reply.

I had a go at that,

but after the
Sudo Xorg -configure

it ran the script, but came up with some errors
"Failed to load fglrx"

and trying to run the test script it generated, resulted in a black screen still.

---

### Post by Decatf on 2010-12-08
fglrx doesn't support the x1k and older cards anymore.

Remove it and use the open source drivers with the following instructions 
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by matt_symes on 2010-12-08
Hi

+1 Decatf

Better to use the open source drivers than vesa. If you do need a fall back position you should be able to use vesa though. I use it for trouble shooting X problems

Kind regards

---

### Post by slpixe on 2010-12-09
oh right, in the script it generated, I need to change it to vesa.
or download some opensource ati drivers

will try it later and report on success or failure

---

