---
title: "Grub Splashimage Issue"
date: 2010-12-04
forum: General Help
---

### Post by bootbat on 2010-12-04
Dear Experts,

I followed [http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#GRUB2_splashimages](http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html#GRUB2_splashimages) to have a splashscreen for my GRUB in 10.10. It is able to detect the splashscreen but does not show up when I boot the machine:


[PHP]bootbat@Home:~$ sudo update-grub
[sudo] password for bootbat: 
Generating grub.cfg ...
Found Debian background: Moraine_Lake_17092005.tga
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found Windows 7 (loader) on /dev/sda1
done[/PHP]

Here's what my /etc/grub.d/05_debian_theme looks like:

[PHP]#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/white
EOF
}

# check for usable backgrounds
use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  # for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub/Plasma-lamp.tga} ; do
    for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Moraine_Lake_17092005.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
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
  set color_normal=white/black
  set color_highlight=brown/black
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi[/PHP]

Any guidance is appreciated.

---

### Post by lindsay7 on 2010-12-04
this is what my file looks like,



> #!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/grub/Lake_mapourika_NZ.tga"
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
for output in ${GRUB_TERMINAL_OUTPUT}; do
  if [ "$output" = "gfxterm" ] ; then
    for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
      if is_path_readable_by_grub $i ; then 
        bg=$i
        case ${bg} in
          *.png)		reader=png ;;
          *.tga)		reader=tga ;;
          *.jpg|*.jpeg)	reader=jpeg ;;
        esac
        if test -e /boot/grub/${reader}.mod ; then
          echo "Found background image: `basename ${bg}`" >&2
          use_bg=true
          break
        fi
      fi
    done
    break
  fi
done

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

---

### Post by bootbat on 2010-12-04
Hi lindsay7,

Thank you for your response. I tried using your file as well but it continues to ignore the splashimage. The one thing that I have noticed is just before it presents me the grub menu, it gives an error to the effect "No Video...something". However, it flashes by so quickly that I am unable to read it even after multiple reboots just to make that out.

Do you have any other ideas that I can try?

---

### Post by lindsay7 on 2010-12-04
I would reinstall grub and try working on the splash image again.


Try,

sudo apt-get install grub

---

### Post by lindsay7 on 2010-12-04
also look at this,

[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html](http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html)

---

