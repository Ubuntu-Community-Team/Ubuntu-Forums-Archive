---
title: "[Burg] After I enter F8 can I see the beautiful  graphic"
date: 2010-05-22
forum: General Help
---

### Post by xgh6990 on 2010-05-22
Yestody I installed burg, I followed the following steps, but when booting , the default surface is white/block, when enter F8, it will change between white/block and beautiful graphic surface.I want to set it default surface is beautiful graphic mode, any body know how to do it? 
I use ubuntu-desktop-10.04.

1.add source 
deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu)  karmic main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu)  karmic main

2.intall burg
sudo apt-get update
sudo apt-get install burg  burg-themes

3.
sudo burg-install "(hd0)"

4.
sudo gedit  /etc/default/burg

delete "#" before GRUB_TERMINAL=

5.
sudo gedit  /etc/burg.d/40_custom

then I copy these codes to it. 

set gfxmode="640x480"
set gfxfont="Unifont  Regular 16"
loadfont /boot/burg/fonts/unifont.pf2
loadfont  /boot/burg/fonts/aqui.pf2
loadfont  /boot/burg/fonts/edges.pf2
loadfont  /boot/burg/fonts/lime.pf2
loadfont  /boot/burg/fonts/7x13B.pf2
loadfont  /boot/burg/fonts/smoothansi.pf2
loadfont  /boot/burg/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod  png
insmod coreui
load_config /boot/burg/themes/proto/theme

6.
sudo  update-burg

7.my burg.cfg

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
if terminal_input console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal console
fi
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    menu_refresh
  fi
}
set theme_name=proto
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
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
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
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  controller.ext
fi
set timeout=5
### END /etc/burg.d/00_header ###


### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

set root='(hd0,7)'
set gfxmode="640x480"
set gfxfont="Unifont Regular 16"
loadfont /boot/burg/fonts/unifont.pf2
loadfont /boot/burg/fonts/aqui.pf2
loadfont /boot/burg/fonts/edges.pf2
loadfont /boot/burg/fonts/lime.pf2
loadfont /boot/burg/fonts/7x13B.pf2
loadfont /boot/burg/fonts/smoothansi.pf2
loadfont /boot/burg/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod png
insmod coreui
load_config /boot/burg/themes/proto/theme

menuentry "Windows 7 Ultimate (loader) (on /dev/sda1)" --class windows --class os {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 66a0f23ca0f21273
    chainloader +1
}

menuentry "Mac OS X 10.6.3 (on /dev/sda2)" --class macosx --class os {
    insmod ntfs
    set root='(hd0,1)'
    chainloader /btldr.mbr
}


menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 88d0f0a3-6860-4843-875e-81432e22e5e4
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda7 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-21-generic
}

menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 88d0f0a3-6860-4843-875e-81432e22e5e4
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda7 ro single 
        initrd  /boot/initrd.img-2.6.32-21-generic
    echo    'Loading initial ramdisk ...'
}


menuentry "GRUB4DOS (on /dev/sda1)" --class ubuntu --class gnu-linux --class gnu --class os {
    insmod ntfs
    set root='(hd0,1)'
    linux /grub.exe
}
### END /etc/burg.d/40_custom ###

8.my /etc/default/burg


GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x800x32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

# Use the previous selected theme, you can also specify a theme to be used
# In the boot menu, use hotkey 't' to popup a theme selection menu
GRUB_THEME=proto

# Use the previous folding option, its value can be 'yes', 'no' or 'saved'
# In the boot menu, use hotkey 'F7' to show the full list, 'f' to toggle
# between folding modes.
GRUB_FOLD=saved

# Add user with burg-adduser, then use GRUB_USERS to config authentication.
# The following example means user1 can boot Ubuntu, no password is needed to
# boot Windows, user1 amd user2 can boot other OS. Superusers can boot any OS
# and use hotkeys like `c' to enter console mode.
#GRUB_USERS="*=user1,user2:ubuntu=user1:windows="

9.my disk partition   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40960000    7  HPFS/NTFS
/dev/sda2            5100       10199    40960000   af  HFS / HFS+
/dev/sda3           10199       60802   406464481+   f  W95 Ext'd (LBA)
/dev/sda5           10199       20397    81917847    7  HPFS/NTFS
/dev/sda6           20398       55702   283587381    7  HPFS/NTFS
/dev/sda7           55703       58313    20971520   83  Linux
/dev/sda8           58313       60540    17887232   83  Linux
/dev/sda9           60540       60802     2098176   82  Linux swap / Solaris

---

### Post by xgh6990 on 2010-05-22
No body help me ?

---

### Post by Phrea on 2010-05-22
Not sure if it'll help, but 10.04 is called Lucid Lynx, and not Karmic Koala.

---

### Post by xgh6990 on 2010-05-23
> **Phrea said:**
> Not sure if it'll help, but 10.04 is called Lucid Lynx, and not Karmic Koala.

I reinstalled ubuntu 9.10, but same bug still here

---

### Post by cfalzone on 2010-06-10
If you install the latest version of BURG bootloader you should find that it doesn't require really any configuration to "make it work."

That said, have you tried installing BURG and then installing it to the MBR and then rebooting the machine *before* you have made any modifications to the configuration files?

Try and do that to see if BURG works.  If you want to change to the graphical interface (icons only, for example) simply press the "T" key while the BURG bootloader menu appears and you may choose a theme.

---

