---
title: "grub2 splash image"
date: 2010-10-19
forum: General Help
---

### Post by Craigular.B on 2010-10-19
Hey all,

Yesterday I did a clean install of Ubuntu 10.10 on my laptop and have been trying to re-customise my GRUB menu. I've edited the 05_debian_theme file to include the path of the image and the colors I want, but when I run update-grub it doesn't seem to pick up on the image OR the colors. Here is my file:
```
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/home/cmbelped/Pictures/purple_ub.png"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="red/black"
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
    for i in {/usr/share/images/grub}/purple_ub.{png,tga} ; do
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
    break
  fi
done

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=white/black
  set color_highlight=red/black
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

I did manage to change the resolution of GRUB (in the /etc/default/grub file) on the GRUB_GFXMODE line. Also, my #GRUB_TERMINAL=console is still commented out.

This is the output of my update-grub:```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
Found Windows Vista (loader) on /dev/sda3
done

```

Neither the colors nor the image are detected, but the changed resolution is.

05_debian_theme is executable, I checked that out. And the file is also in the correct place. I'm not sure what to do!

Thanks,
Craig

---

### Post by yetiman64 on 2010-10-19
> **Craigular.B said:**
> Hey all,

Yesterday I did a clean install of Ubuntu 10.10 on my laptop and have been trying to re-customise my GRUB menu. I've edited the 05_debian_theme file to include the path of the image and the colors I want, but when I run update-grub it doesn't seem to pick up on the image OR the colors. Here is my file:
```
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  [COLOR=Red]WALLPAPER="/home/cmbelped/Pictures/purple_ub.png"[/COLOR]
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="red/black"
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
    for i in {/usr/share/images/grub}/purple_ub.{png,tga} ; do
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
    break
  fi
done

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=white/black
  set color_highlight=red/black
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
```I did manage to change the resolution of GRUB (in the /etc/default/grub file) on the GRUB_GFXMODE line. Also, my #GRUB_TERMINAL=console is still commented out.

This is the output of my update-grub:```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
Found Windows Vista (loader) on /dev/sda3
done

```Neither the colors nor the image are detected, but the changed resolution is.

05_debian_theme is executable, I checked that out. And the file is also in the correct place. I'm not sure what to do!

Thanks,
Craig
Note during the grub boot process your home directory is not mounted, this may be a problem for you. In my setup I create a folder /boot/grub/images where images (in tga format, png should be ok though) are stored, that is in the same base path grub looks for its files.
I create the images in the same size I have set in /etc/default/grub GRUB_GFXMODE (1024x768 --) -- is to beat the smiley code in the reply editor only :).

I'll include my 05_debian_theme_file for you to compare. End result is on the left in the attached low res photo (800 x 500).

05_debian_theme
```
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
[COLOR=Blue]  WALLPAPER="/boot/grub/images/BigCats.tga"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="red/light-gray"[/COLOR]
fi

set_mono_theme()
{
  cat << EOF
[COLOR=Blue]set menu_color_normal=white/black
set menu_color_highlight=red/light-gray[/COLOR]
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
``` Blue is highlighting changes I made to get it working.

---

### Post by Craigular.B on 2010-10-19
> **yetiman64 said:**
> Note during the grub boot process your home directory is not mounted, this may be a problem for you. In my setup I create a folder /boot/grub/images where images (in tga format, png should be ok though) are stored, that is in the same base path grub looks for its files.
I create the images in the same size I have set in /etc/default/grub GRUB_GFXMODE (1024x768 --) -- is to beat the smiley code in the reply editor only :).

I'll include my 05_debian_theme_file for you to compare. End result is on the left in the attached low res photo (800 x 500).

05_debian_theme
```
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
[COLOR=Blue]  WALLPAPER="/boot/grub/images/BigCats.tga"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="red/light-gray"[/COLOR]
fi

set_mono_theme()
{
  cat << EOF
[COLOR=Blue]set menu_color_normal=white/black
set menu_color_highlight=red/light-gray[/COLOR]
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
``` Blue is highlighting changes I made to get it working.

Thanks for the reply! I think the combination of moving the image to a folder in /boot and using the wallpaper variable in the for-loop got it working! I really appreciate it :)

---

### Post by yetiman64 on 2010-10-19
> **Craigular.B said:**
> Thanks for the reply! I think the combination of moving the image to a folder in /boot and using the wallpaper variable in the for-loop got it working! I really appreciate it :)

You're welcome, If all is working OK could you mark as solved. Link 5 in my sig has instructions. yetiman64

---

