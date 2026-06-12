---
title: "Grub2 image"
date: 2010-06-16
forum: General Help
---

### Post by akernan on 2010-06-16
I'm trying to add an image to my grub, I did a clean install of 10.04.  I added a grub image successfully in older versions.  I followed the directions in [Grub2 image]("http://linuxhub.net/2009/07/grub-2-add-splash-image-to-beautify-grub-2/"). But I can't find the line that needs to be changed.  I tried changing other lines with no success.  Here is my 05_debian_theme file ....

> #!/bin/bash -e

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

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi


What line do I change?

---

### Post by cariboo on 2010-06-17
I haven't tried this myself, but have a look at [Burg]("https://help.ubuntu.com/community/Burg"), quite a few of the testers during Lucid used this method had great success.

---

### Post by akernan on 2010-06-17
> **cariboo907 said:**
> I haven't tried this myself, but have a look at [Burg]("https://help.ubuntu.com/community/Burg"), quite a few of the testers during Lucid used this method had great success.

I check it out.

---

### Post by rwgale on 2010-06-17
Hi,

The path and filename you need to change is in the 05_debian_theme at line:
WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"

I changed mine to:
WALLPAPER="/home/robert/grub2_backgrounds/grub2default.jpg"

```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/home/robert/grub2_backgrounds/grub2default.jpg"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="magenta/light-gray"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
EOF
}
```

This is slightly different than the line specified in the earlier Grub-2 Guide. But can be found in the Grub2 - Community Ubuntu Documentation
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

The directory I used can hold your Grub-splash screen wallpapers, then a modified a python script can be used to select a wallpaper and copy it to grub2default.jpg.  Early in Lucid I could not get .jpg to load (and spent a lot of time coverting to .tga) or set my grub screen resolution properly, but now jpg images load properly and I can use the native resolution on a Dell E228WFP widescreen.

Best Regards,
Robert

---

### Post by karthick87 on 2010-06-17
Put all your images in /boot/grub/

Goto terminal and type 

```

gksudo gedit /etc/grub.d/05_debian_theme
```
and change Debian_KDE.png to your file name..

```

#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/[COLOR=Red]Debian_KDE.png[/COLOR]"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="red/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
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

---

### Post by akernan on 2010-06-19
I don't have /grub/boot/ directory.  I tried .png, .jpg, & .tga files in 05_debian_theme, changing the wallpaper line.  The image is not recognized when I update grub.  The image is recognized when I update burg, but the display is just text.  I can change themes with burg to burg themes.

---

### Post by akernan on 2010-06-19
I made a directory in /boot/burg/themes and put my files in it.  I copied the themes file from another theme and made changes to it.  Thanks for the replies.

---

