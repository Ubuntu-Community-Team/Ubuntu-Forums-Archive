---
title: "GRUB 2 installation error"
date: 2010-07-03
forum: General Help
---

### Post by asorron on 2010-07-03
While attempting to sudo apt-get install grub2 i get this messages:```

(Reading database ... 230649 files and directories currently installed.)
Removing grub ...
Processing triggers for man-db ...
Selecting previously deselected package grub-pc.
(Reading database ... 230603 files and directories currently installed.)
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu6_i386.deb) ...
Selecting previously deselected package grub2.
Unpacking grub2 (from .../grub2_1.98-1ubuntu6_i386.deb) ...
Processing triggers for man-db ...
Setting up grub-pc (1.98-1ubuntu6) ...
Installation finished. No error reported.
Generating grub.cfg ...
/etc/grub.d/05_debian_theme: line 48: unexpected EOF while looking for matching ``'
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc; however:
  Package grub-pc is not configured yet.
dpkg: error processing grub2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 grub-pc
 grub2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any idea what is causing it not to install?
im afraid to run it grubless so im always reinstalling grub 0.97 after it will show me that error...
Thanks!

---

### Post by ajgreeny on 2010-07-03
What version of ubuntu are you running?
Have you removed legacy grub before trying to install grub2?
Have you seen this information?  [https://wiki.ubuntu.com/Grub2#Installing%20%28Ubuntu%209.04+%29](https://wiki.ubuntu.com/Grub2#Installing%20%28Ubuntu%209.04+%29)

---

### Post by asorron on 2010-07-03
running Ubuntu Lucid Lynx
and i removed grub legacy with apt-get remove grub
is there any step further i need to take in order to update it? just to make sure...
the wierd thing is i "installed" grub legacy, which means i had grub installed (1.96) on the grub loader it states its 1.96... but for some reason whatever i configure to it wont take any changes (i.e splash screen and such) i'm doing something wrong? all my configurations go to /boot/grub foler.

---

### Post by ajgreeny on 2010-07-03
Perhaps it's worth trying to install grub using the live CD.

See [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by wilee-nilee on 2010-07-03
Carefully read this wiki it gives exact instructions on installing grub2 and making sure you remove grub-legacy and all of it's files in the OS.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by Leppie on 2010-07-03
> **asorron said:**
> While attempting to sudo apt-get install grub2 i get this messages:```

Installation finished. No error reported.
Generating grub.cfg ...
[COLOR=Red]/etc/grub.d/05_debian_theme: line 48: unexpected EOF while looking for matching ``'[/COLOR]
```Any idea what is causing it not to install?
im afraid to run it grubless so im always reinstalling grub 0.97 after it will show me that error...
Thanks!
could you post your 05_debian_theme?

---

### Post by asorron on 2010-07-03
```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi
```


Though i tried to have a splash image to it... which didnt work out.

Plus, I also noted grub2 was installed all along (messed out with .../menu.lst and ../grub.cfg, menu.lst gave no results, and grub.cfg changed my win7 title.)

now I only have left to set a splash screen behind and im all set ;]

grub 2 was installed after reboot, i took  a risk with first backuping my system using acronis.

---

### Post by asorron on 2010-07-03
problem solved, grub2 was installed after a reboot (seems it was installed already and by apt-get grub it messed the config of it, some collisions and such)
now i edited the grub 05_deb file and it loads the splash smoothly.

I knew i can fix it eventually, didn't knew it'll take that long XD thanks all.

---

### Post by Leppie on 2010-07-03
lol, glad it's working ;)

---

