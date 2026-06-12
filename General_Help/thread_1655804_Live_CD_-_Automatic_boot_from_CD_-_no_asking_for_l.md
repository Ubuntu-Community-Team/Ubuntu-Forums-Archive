---
title: "Live CD - Automatic boot from CD - no asking for language &amp; livecd|hdd boot"
date: 2010-12-30
forum: General Help
---

### Post by azorgmail on 2010-12-30
Hi all,
 i do software (learn keyboard) for blind people. I selected ubuntu and festival and TTS.
 Please i NEED (mandatory for disabled people) live cd what can be inserted into cdrom and everything
 is done - automatic boot, settings done, software is on start-up...
 I created own distribution, programed software, done settings, but what kills me is :
 
** How i can run AUTOMATIC (without asking, no enter) boot from CD-ROOM. Now CD asking :**
 - 1) What language want you (here is only czech) - need ENTER (killer for disabled people)
 - 2) Boot from CD or hdd - need ENTER (killer no. 2 for disabeld people)
   - after 2) I m ok, i can handle it myself, works.
 
 I edited file in isolinux menu.lst etc - I can edit text but i do not know how run defalut
 choice automaticly. timout 0 does not work :/
  
 PLEASE - if you can/want help me please be specific, I spent a lot of hours reading tutorials
  grub/isolinux and have nothing ;)...
  
  Thank you.

P.S I do own custommize by [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by azorgmail on 2010-12-30
I m at home, so here is my files:
menu.lst
```
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz
```
and text.cfg
```
default live
label live
  menu label Spustit výuku psaní pro nevidomé 
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet ro quiet splash vga=791 lang=cs
label hd
  menu label Nabootovat z disku
  localboot 0x80
```

thank you all !

---

### Post by azorgmail on 2010-12-31
nobody have a idea?

---

### Post by azorgmail on 2011-01-03
please can someone help me disable this menu :/

---

