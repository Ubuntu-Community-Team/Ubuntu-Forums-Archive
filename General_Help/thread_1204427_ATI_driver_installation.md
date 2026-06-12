---
title: "ATI driver installation"
date: 2009-07-04
forum: General Help
---

### Post by anv on 2009-07-04
I have integrated ATI HD 3300 in my motherboard, I have earlier installed driver for it, successfully according this manual: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide). After unistalling the old driver and trying to start upgrading though I did as instructed the problem started already in this second point in manual installation, to create package:


sh ati-driver-installer-9-6-x86.x86_64.run --builddpkg Ubuntu/8.10

ati-driver-installer-9-6-x86.x86_64.run: 1: Syntax error: redirection unexpected



I ask help to solve it

---

### Post by markharding557 on 2009-07-04
have you tried the hardware drivers applet? this should have a driver

---

### Post by anv on 2009-07-04
I don't have gnome so I don't have that applet

there was some problem with my downloaded Catalyst file after I did new download manual installation went fine.

---

### Post by markharding557 on 2009-07-06
i think xubuntu has the same applet there is a version of it on kde also.
if it is not then install it
> sudo apt-get install jockey-gtk

---

### Post by anv on 2009-07-08
as said I don't use Gnome it is Gnome software and dependent of several gnome libraries I have taken nearly all of those away from my Xubuntu install...much faster, less security risks etc.

---

