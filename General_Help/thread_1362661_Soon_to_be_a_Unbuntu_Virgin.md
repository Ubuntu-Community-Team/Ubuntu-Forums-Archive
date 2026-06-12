---
title: "Soon to be a Unbuntu Virgin"
date: 2009-12-23
forum: General Help
---

### Post by DevonDaDude on 2009-12-23
Sorry, if i posted in the incorrect forum.

Hello, everyone! I'm new to Unbuntu forum and I'm looking to install Unbuntu on my laptop. I need some help.

I have an HP Pavilion tx2000, it's a touch screen tablet. I would like to know if I install unbuntu if my touchscreen and  pen tablet will work?

Attach is a copy of dxdiag hopefully this will help you determine if I qualify.

---

### Post by Treeh on 2009-12-23
The TX2000 is a wacom-based tablet, so I would presume that a basic modification of this method will work (to enable touchscreen support) for Karmic Koala: [http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915). I had 8.10 running on my x64t (also a tablet) and the touchscreen worked beautifully.

I'm sure that upon more extensive search of the forum, you could find more 9.10-specific based information.

Also, given that you have a tablet, I presume you do not have a CD-drive available (unless you have some sort of docking station). As such, the easiest method for install is using a USB stick: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

And lastly, it's "Ubuntu" not "Unbuntu"...as you can see in the site's URL and the forum's header...and pretty much everywhere else your eyes happen to wander.

---

### Post by nothingspecial on 2009-12-23
From a quick search, it seems so, with a little fiddling.

---

### Post by DevonDaDude on 2009-12-23
[LIST=1]
[*] Sorry, I was in a hurry and I didn't double check for errors.
[*]I did search before I posted, I already have Hardy 8.0.4 I just wanted to know if theres any other version or type would work
[*]I would like to delete Windows Vista and Install Hardy as my primary OS, how would I do something like that?
[/LIST]

---

### Post by Favux on 2009-12-23
Hi DevonDaDude,

I wouldn't do that.  Why not dual boot?  That's what I do with my TX200.

Pretty much everything works on it including Wacom.

Why Hardy?

Some resources:

Linuxwacom compile and installation [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  If you want other than the installed default version.  Has xorg.conf's useful for Hardy and Intrepid.

Jaunty and Karmic [HOW TO]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104").  Has the wacom.fdi you need to get touch working.  In Jaunty you'll need to compile a new wacom.ko (usb kernel driver/module) which is easy.  In Karmic you just need the .fdi.

Rotation [HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  If you install Intrepid or higher you can get automatic screen rotation.

---

