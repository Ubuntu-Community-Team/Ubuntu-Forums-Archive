---
title: "Grub 2 Graphical menu (themes)"
date: 2010-03-23
forum: General Help
---

### Post by bkbilly on 2010-03-23
I've managed to set a wallpaper to the grub menu, but now I want something more advanced...

[LIST=1]
[*]I've seen this project but I don't know how to put this theme to the grub: [http://grub.gibibit.com/](http://grub.gibibit.com/)
[*]I found and this threat that explains how to change the grub menu theme:
[http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg](http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg)
I followed the whole guide step by step and I couldn't change the theme...
[*]I also found and this one: [http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg](http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg)
To follow this one I first have to
follow the previous one...
[/LIST]
Can you help me by any way to change the theme?
Do I have to do and something else?
I use Ubuntu 9.10 64bit..

---

### Post by bkbilly on 2010-03-23
[SIZE=4]I have copied and pasted some of the commands' results and files so that you can fix something I did wrong...[/SIZE]

sudo apt-get install grub-pc
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc is already the newest version.
The following packages were automatically installed and are no longer required:
  burg-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```sudo gedit /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```sudo gedit /etc/grub.d/40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
set gfxmode="640x480"
set gfxfont="Unifont Regular 16"
loadfont /boot/grub/themes/fonts/unifont.pf2
loadfont /boot/grub/themes/fonts/aqui.pf2
loadfont /boot/grub/themes/fonts/edges.pf2
loadfont /boot/grub/themes/fonts/lime.pf2
loadfont /boot/grub/themes/fonts/7x13B.pf2
loadfont /boot/grub/themes/fonts/smoothansi.pf2
loadfont /boot/grub/themes/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod png
insmod coreui
load_config /boot/grub/themes/proto/theme.txt
```ls /boot/grub/themes/proto
```
bg.png           menubox_ne.png  menubox_w.png       select_blue_se.png
icon-gentoo.png  menubox_n.png   select_blue_c.png   select_blue_s.png
icon-ubuntu.png  menubox_nw.png  select_blue_e.png   select_blue_sw.png
icon-vista.png   menubox_se.png  select_blue_ne.png  select_blue_w.png
menubox_c.png    menubox_s.png   select_blue_n.png   theme.txt
menubox_e.png    menubox_sw.png  select_blue_nw.png
```

---

### Post by Agrezar on 2010-03-27
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console <---

GRUB_TERMINAL=console means not to use the graphics mode, just normal console. Try commenting that out, see if works.

you have to run sudo update-grub after you make this change to update the grub.cfg file.

---

### Post by bkbilly on 2010-03-27
I have also tried this... It doesn't work...

---

### Post by Agrezar on 2010-03-29
from a little research and trying this on my own machine.

a) the package to apt-get install = burg-pc
b) it can coexist with grub-pc
c) Im not 100% if it will work on a raid device. I tryed it and it couldnt find my partition, i didnt dig that hard on it though, maybe i needed to install a mod.
d) all burg files relate to "burg" so if you want to install it, it's burg-install instead of grub-install and so on. The install directory is in the /boot/burg. All references are to the /boot/burg prefix. The 01,05,10 etc headers aswell in /etc/burg.d/<headers>
e) there is no /etc/default/burg file, it does exist in the /usr/share/burg dir, under the filename of "default"
f) For my instance i do believe i need to compile burg from scratch to implement my raid. I am going to try this and see.\
g) upgradeing it again with "burg" #update-burg

[URL="https://help.ubuntu.com/community/Burg"]
https://help.ubuntu.com/community/Burg[/URL]

check this site out, remember it's burg-pc now.

---

### Post by Agrezar on 2010-03-29
I finally had success with this on a usb drive. I ended up recompiling burg from the bzr. It still could not initialize on my raid with the new compiled burg so on the usb it went. :D

If you wanna try it, create a fat partition on a usb, create a /boot/burg directory. mount it somewhere other than where the system does (burg errors if you dont) I chose /mnt

burg-install --root-directory=/mnt /dev/sdd (replace with your /dev)
burg-mkconfig -o /mnt/boot/burg/burg.cfg

at this point unfortunately the generated cfg has to be edited or at least i did, im sure some could have figured out why it wouldnt pick up the theme from GRUB_THEME=<theme>. In my case the cfg did have my change but didnt want to use it. I think it's because some of these are old themes meant for grub

make sure your ${prefix} is right if you want to leave them in. In a grub shell type, **set** and it will show you what your grub prefix is. (hd0,1)/boot/burg in my case

[B]last two entries of the 00 header:
[/B]
set theme_fold=${prefix}/themes/ **# added specific path**
if test -f ${prefix}/themes/ubuntu/theme.txt ; **# added specific path**
  insmod coreui
  menu_region.text
  load_config ${prefix}/themes/ubuntu/theme.txt **# added specific path**
  insmod vbe
  insmod png
  insmod jpeg
  set gfxmode=1280x800
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  controller.ext
fi
insmod fat  **## added this for pen drive fs**
insmod ext2
set root='(/dev/sdd1)' **## had to change this for the pen drive**
search --no-floppy --fs-uuid --set 80F9-C263 **## changed uuid for pen**
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
if sleep --interruptible 0 ; then
  set timeout=10
fi


**### END /usr/etc/burg.d/40_custom ###**
loadfont /boot/burg/themes/fonts/unifont.pf2
loadfont /boot/burg/themes/fonts/aqui.pf2
loadfont /boot/burg/themes/fonts/edges.pf2
loadfont /boot/burg/themes/fonts/lime.pf2
loadfont /boot/burg/themes/fonts/7x13B.pf2
loadfont /boot/burg/themes/fonts/smoothansi.pf2
loadfont /boot/burg/themes/fonts/Helvetica-Bold-14.pf2
loadfont /boot/burg/themes/fonts/unifont.pf2
loadfont /boot/burg/themes/fonts/Helvetica-10.pf2
loadfont /boot/burg/themes/fonts/Helvetica-Bold-12.pf2


I found too the path in the cfg, and txt files of the themes were /boot/grub/theme, changed these to reflect /boot/burg/themes

themes that worked:
proto
winter
ubuntu

I tried useing a theme called sora, looks nice, but when i try loading it, it either pukes or i end up with a blank screen. I think it has to do with the bg image being 2+ megs :D -goodluck

---

### Post by Agrezar on 2010-03-30
... after a little more digging

enable the ppa from [B][I][https://help.ubuntu.com/community/Burg]("https://help.ubuntu.com/community/Burg")
[/I][/B]
open up your synaptic package manager, reload, search for burg, mark **burg-pc**, **burg-themes**, install.

burg-pc didnt put a **/etc/default/grub** file, so i copied it from **/usr/share/burg/default/burg**

edit the **/etc/default/burg** file to make the changes to **GRUB_THEME** and **GRUB_GFXMODE**. ie:  GRUB_THEME=sora and GRUB_GFXMODE=1680x1050

if your video pukes to the setting you chose for the gfxmode it is possible you dont have that vbe mode, in a grub prompt run vbeinfo.

[B]burg-mkconfig -o /boot/burg/burg.cfg
burg-install /dev/sdd[/B]

check your **/boot/burg/burg.cfg** file to make sure the changes have been made.

If **sora** is in that file, then you know it used your imputs from /etc/default/burg file. You should be looking at something like:

[PHP]#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu
    load_config ${prefix}/themes/${theme_name}/theme
    menu_refresh
  fi
}
set theme_name=sora
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme
  insmod vbe
  insmod png
  insmod jpeg
  set gfxmode=1680x1050
  set gfxfont="Unifont Regular 18"
  menu_region.gfx
  controller.ext
fi
insmod fat
insmod ext2
set root='(/dev/sdd1)'
search --no-floppy --fs-uuid --set 80F9-C263
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry "Lucid Lynx 10.04" --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	set gfxpayload=keep
	insmod ext2
	set root='(/dev/mapper/pdc_effeidaf4)'
	search --no-floppy --fs-uuid --set 3a3dafca-e2cf-432e-99c0-20481fb4cca5
	echo	Loading Linux 2.6.32-17-generic ...
	linux	/boot/vmlinuz-2.6.32-17-generic root=UUID=3a3dafca-e2cf-432e-99c0-20481fb4cca5 ro  quiet splash
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-17-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "Win7ows" --class windows --class os {
	insmod ntfs
	set root='(/dev/mapper/pdc_effeidaf1)'
	search --no-floppy --fs-uuid --set 748e3f698e3f2352
	chainloader +1
}
menuentry "Karmic Kola 9.10" --class ubuntu --class os --group group_/dev/mapper/pdc_effeidaf3 {
	insmod ext2
	set root='(/dev/mapper/pdc_effeidaf3)'
	search --no-floppy --fs-uuid --set 1db1d72e-aa0e-488e-8b51-b245b95a8a1b
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=1db1d72e-aa0e-488e-8b51-b245b95a8a1b ro
	initrd /boot/initrd.img-2.6.31-21-generic
}
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###[/PHP]

I think a few fonts are missing due to some scene borders are ? for characters. Try that :D a little simpler. Still no support for booting from a striped drive.

if you finally get it working, you can actually change your theme while at the menu, i think it's the key "t"

---

### Post by bkbilly on 2010-03-30
Thank you for your info...
I will try these things out in about 2 weeks because I am on vacation...
If I get any results then, I will tell you!

---

### Post by Agrezar on 2010-03-31
This does work with grub-pc
[URL="http://www2.apebox.org/wordpress/linux/228/"]
http://www2.apebox.org/wordpress/linux/228/[/URL]

---

### Post by bmck on 2010-05-02
im on karmic and i installed burg, rebooted and the interace resolution is way to big, also changed resolution of ubuntu bootsplash. i edited burg.cfg and changed the resolution but that didnt the resolution. how do i remove burg and go back to plain grub menu?

---

### Post by techunit on 2010-05-02
I know that this doesn't help but I would advise you stay away from messing with the GRUB boot menu if you don't know what your getting into.

---

### Post by bkbilly on 2010-05-15
I Managed to change the theme... I found the tutorial here: [http://nourlinux.wordpress.com/2010/04/06/get-animated-themed-icon-only-grub-menu-using-burg/](http://nourlinux.wordpress.com/2010/04/06/get-animated-themed-icon-only-grub-menu-using-burg/)
Here is what i did

[SIZE="3"][COLOR="DarkRed"]INSTALL[/COLOR][/SIZE]
_sudo add-apt-repository ppa:bean123ch/burg_
_sudo apt-get update_
_sudo apt-get install burg burg-themes_
_sudo burg-install "(hd0)"_
_gksu gedit /etc/default/burg_
> uncomment the following:
[B]GRUB_THEME=saved
GRUB_FOLD=saved[/B]
_sudo update-burg_

[SIZE="3"][COLOR="DarkRed"]TEST THEMES[/COLOR][/SIZE]
_sudo apt-get install burg-emu_
_burg-emu -r host_

[SIZE="3"][COLOR="DarkRed"]SHORTCUTS[/COLOR][/SIZE]
To see the shortcuts you can press "**F**"
there are two that it doesn't mention...
You can press "**F**" to *Toggle between toggle mode*
And you can press "**F7**" to *List the folded boot items*

---

