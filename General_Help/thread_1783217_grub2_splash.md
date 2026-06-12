---
title: "grub2 splash"
date: 2011-06-15
forum: General Help
---

### Post by boblizar on 2011-06-15
[https://help.ubuntu.com/community/Grub2#Set%20the%20splash%20image](https://help.ubuntu.com/community/Grub2#Set%20the%20splash%20image)

incorrectly says that maverick is controlled by /etc/default/grub, im still getting debian moar blue splash....  investigation of the 10.04 settings shows lines that would load debian moar blue...


testing this edit to /etc/grub.d/05_debian_theme
#  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  WALLPAPER="/usr/share/images/grub/nebula.jpg"

(why nebula? because the universe kicks ***, just ask the folks @ debian!)

&& going to issue ```
sudo update-grub
``` to make sure the changes are installed

i had to further brutalize the fonts in the debian theme file to get the fonts to clash to where i could see them.  black text on space background works well for starwars editing but not for selecting what kernel im booting!

now on to figure out how to get rid of this FUGLY purple gdm background

edit to post my /etc/grub.d/05_debian_theme file for backup since grub wants to update on me
```

cat 05_debian_theme 
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
#  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  WALLPAPER="/usr/share/images/grub/nebula.jpg"
  COLOR_NORMAL="light-green/black"
  COLOR_HIGHLIGHT="green/light-gray"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=light-green/black
set menu_color_highlight=green/light-gray
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

```

---

