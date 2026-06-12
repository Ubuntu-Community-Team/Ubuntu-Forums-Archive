---
title: "multi boot live dvd"
date: 2009-07-29
forum: General Help
---

### Post by konnorrigby on 2009-07-29
hello, im trying to make a multi bootable live dvd with ubuntu and kubuntu.

i havn't got very far but i have

/boot
/ubuntu
/kubuntu
---------------
in boot i have /isolinux which has the isolinux.cfg in it.

heres my isolinux.cfg: 

```

DEFAULT /boot/isolinux/vesamenu.c32
PROMPT 0
TIMEOUT 300
TOTALTIMEOUT 450
####
MENU BACKGROUND /boot/isolinux/splash.png
MENU TITLE Super-Disc ** July09 Edition

Label Ubuntu
MENU LABEL ^1 Ubuntu

KERNEL /ubuntu/casper/vmlinuz
append file=/ubuntu/casper/preseed/ubuntu.seed boot=casper initrd=/ubuntu/casper/initrd.gz

Label Kubuntu
MENU LABEL ^2 Kubuntu

KERNEL /kubuntu/casper/vmlinuz
append file=/kubuntu/casper/preseed/ubuntu.seed boot=casper initrd=/ubuntu/casper/initrd.gz

```im sure i have all the directories correct.

thanks in advance

--konnor

edit: i am using Kubuntu-9.04-desktop-i386.iso and Ubuntu-9.04-desktop-i386.iso. by the way

---

### Post by konnorrigby on 2009-07-29
update: ok i realized i had two isolinux folders- one in the root and one in the kubuntu folder.

so i restarted and now have

boot/
kubuntu/
ubuntu/
----------------
i also noticed that the isolinux.cfg was different so i followed the format that it allready had...

so now i have in isolinux.cfg

```

include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo

```

and menu.cfg
```

menu hshift 13
menu width 49
menu margin 8

menu title Installer boot menu
include stdmenu.cfg
include text.cfg
include amdtext.cfg
include gtk.cfg
include amdgtk.cfg
menu begin advanced
    menu title Advanced options
    label mainmenu
        menu label ^Back..
        menu exit
    include stdmenu.cfg
    include adtext.cfg
    include adamdtext.cfg
    include adgtk.cfg
    include adamdgtk.cfg
menu end
label help
    menu label ^Help
    config prompt.cfg

```
and finally i have text.cfg
```

default live
label live
  menu label ^Ubunutu
  kernel ubuntu/casper/vmlinuz
  append  file=/cdrom/ubuntu/preseed/ubuntu.seed boot=casper initrd=ubuntu/casper/initrd.gz quiet splash --
label kubuntu
  menu label ^kubuntu
  kernel kubuntu/casper/vmlinuz
  append  file=/cdrom/kubuntu/preseed/ubuntu.seed boot=casper only-ubiquity initrd=kubuntu/casper/initrd.gz quiet splash --  

```

it still does not work and is making me sad... :(

---

### Post by konnorrigby on 2009-07-30
ok, if any one is reading this, i have after hours of trial and error i have perfected my ubuntu kubuntu 9.04 live dvd, i have booted from both kernels so i know they work...

sooo heres folders

/boot
/ubuntu
/kubuntu
---------------------
/boot/isolinux/isolinux.cfg

```

include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo

```

/boot/isolinux/menu.cfg
```

menu hshift 13
menu width 49
menu margin 8

menu title Installer boot menu
include stdmenu.cfg
include text.cfg
include amdtext.cfg
include gtk.cfg
include amdgtk.cfg
menu begin advanced
    menu title Advanced options
    label mainmenu
        menu label ^Back..
        menu exit
    include stdmenu.cfg
    include adtext.cfg
    include adamdtext.cfg
    include adgtk.cfg
    include adamdgtk.cfg
menu end
label help
    menu label ^Help
    config prompt.cfg

```

and finally /boot/isolinux/text.cfg
```

default ubuntu
label ubuntu
  menu label ^Ubunutu
  kernel /ubuntu/casper/vmlinuz
  append  file=/cdrom/ubuntu/preseed/ubuntu.seed boot=casper initrd=/ubuntu/casper/initrd.gz quiet splash --
label kubuntu
  menu label ^Kubuntu
  kernel /kubuntu/casper/vmlinuz
  append  file=/cdrom/kubuntu/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/kubuntu/casper/initrd.gz quiet splash --

```

there are two options on my boot menu: Ubuntu and Kubuntu.

---

### Post by shikima on 2009-08-31
I will check, but if u can tell me what are you put in the folders? :P

Edit: I mean, the kubuntu and ubuntu folder, is the files of the iso?

---

### Post by shikima on 2009-09-09
[konnorrigby]("http://ubuntuforums.org/member.php?u=861155"), Can u tell what you put in the root folder of the DVD???:popcorn:

---

### Post by shikima on 2009-09-29
I'm already done this, thx but I have a problem with make a submenus for each distro...I don't know how to make them :(

---

### Post by prshah on 2009-10-23
You can also check out [http://ubuntuforums.org/showpost.php?p=8147658&postcount=12](http://ubuntuforums.org/showpost.php?p=8147658&postcount=12) (or my sig) for a multiboot live DVD which includes Ubuntu, Kubuntu, Xubuntu, MythBuntu, etc

---

### Post by shikima on 2009-10-23
thank you for u time...I finished the project last month...with submenus and others apps like rescuecd, ophcrack, and almost all the buntus, except edubuntu, cause I didn't have enough time to remasterize that distro

thank you again :P

---

### Post by dadep on 2009-11-04
> **shikima said:**
> thank you for u time...I finished the project last month...with submenus and others apps like rescuecd, ophcrack, and almost all the buntus, except edubuntu, cause I didn't have enough time to remasterize that distro

thank you again :P

Nice. I'm interested. Can you post here how you did it?
Thank you
Daniele

---

### Post by shikima on 2009-11-04
well, I'm used this documents [http://ubuntuforums.org/showthread.php?t=703905&page=3](http://ubuntuforums.org/showthread.php?t=703905&page=3) , and I developed some submenus to make easy to use the dvd as a matter in fact, I did 3 dvds, one with distros for 32 bits, second with distros 64 bits, and the last with recovery tools, backtrack, gparted, etc...

If u need any advice, I will be able to help u :D;)

---

