---
title: "How can i set grub2 splashimage?"
date: 2010-08-15
forum: General Help
---

### Post by colau on 2010-08-15
Can anyone post the methods to set grub2 splashimage?

---

### Post by Ginsu543 on 2010-08-15
Assuming you are running grub 1.97 (one that comes with Jaunty), check out [_this website_](https://help.ubuntu.com/community/Grub2) under the section entitled "Splash Images and Theming." It gives step by step instructions.

If you are running grub 1.98 (one that comes with Lucid), then it's even easier. Let us know and I'll give you step by step directions.

---

### Post by colau on 2010-08-15
> **Ginsu543 said:**
> Assuming you are running grub 1.97 (one that comes with Jaunty), check out [_this website_](https://help.ubuntu.com/community/Grub2) under the section entitled "Splash Images and Theming." It gives step by step instructions.

If you are running grub 1.98 (one that comes with Lucid), then it's even easier. Let us know and I'll give you step by step directions.
```

ii  grub-common                           1.98-1ubuntu5                                   GRand Unified Bootloader, version 2 (common 
ii  grub-pc                               1.98-1ubuntu5                                   GRand Unified Bootloader, version 2 (PC/BIOS
ii  grub-splashimages                     1.2.3                                           a collection of great GRUB splashimages
ii  grub2                                 1.98-1ubuntu7                                   GRand Unified Bootloader, version 2 (dummy p
ii  grub2-splashimages                    1.0.0                                           a collection of great GRUB2 splashimages

```

---

### Post by colau on 2010-08-15
cat /etc/grub.d/05_debian_theme

```

#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/home/<user>/vista2.jpg"
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
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image /usr/share/images/grub/Moraine_Lake_17092005.tga ; then
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

### Post by Ginsu543 on 2010-08-15
Okay, so you have 1.98... then it's easy. Notice in your /etc/grub.d/05_debian_theme file the line which reads:
```

WALLPAPER="/home/<user>/vista2.jpg"

```
Just change the "/home/<user/vista2.jpg" to whichever splash image you want, using the proper directory tree.

---

### Post by colau on 2010-08-20
> **Ginsu543 said:**
> Okay, so you have 1.98... then it's easy. Notice in your /etc/grub.d/05_debian_theme file the line which reads:
```

WALLPAPER="/home/<user>/vista2.jpg"

```
Just change the "/home/<user/vista2.jpg" to whichever splash image you want, using the proper directory tree.
I have changed it.Nothing works.
```

#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/grub/Lake_mapourika_NZ.tga"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_blue_theme()
{
  cat << EOF
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
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

# otherwise, set the traditional Debian blue theme
if ${use_bg} ; then
  set_blue_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_blue_theme
fi

```

---

