---
title: "I need help from someone on here"
date: 2010-01-09
forum: General Help
---

### Post by Jackzor on 2010-01-09
Can someone give me the default contents for the file that opens when you run

gksudo gedit /etc/grub.d/05_debian_theme

in terminal

---

### Post by spiderbatdad on 2010-01-09
```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/white
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do
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
  set color_normal=black/black
  set color_highlight=magenta/black
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

### Post by spiderbatdad on 2010-01-09
if you modified the file there is more than likely a hidden backup. Look at 
```
ls -al /etc/grub.d
```

---

### Post by Jackzor on 2010-01-09
I had changed ot. But I didn't break it. I thought MAYBE that if I put it back to defaults then I would be able to get the terminal to come up at the login screen


[http://ubuntuforums.org/showthread.php?t=1377000](http://ubuntuforums.org/showthread.php?t=1377000)

---

