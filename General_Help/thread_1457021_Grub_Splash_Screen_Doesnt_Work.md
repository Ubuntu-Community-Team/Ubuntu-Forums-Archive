---
title: "Grub Splash Screen Doesnt Work"
date: 2010-04-18
forum: General Help
---

### Post by Jack3500 on 2010-04-18
So I installed Ubuntu 9.10 64 bit 2 days ago and am now using grub for a triboot of windows 7, Ubuntu and OS X, and it works great !!! It even fixed a problem i had with booting OSX

but i still cant get the splash screen to work, i have read many, many other posts and spent many, many hours on this

 I used this: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)  to see how to do it and am almost certain i did everything right

This is what my "/etc/grub.d/05_debian_theme" looks like:

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
  
for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Plasma-lamp.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
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
```And this is what i get when i run "update-grub"

```

Generating grub.cfg ...
Found Debian background: Plasma-lamp.tga
Found Windows 7
Found Mac OS X
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
done
```Any help would be VERY appreciated and i would like to thank in advance :P

---

### Post by mockingbird on 2010-04-18
I have a similar problem.  I have a fresh Lucid install on a tertiary partition and when Grub loads from the Vista menu, it's black and white.

I think this has something to do with the fact that I installed it on the third partition and not on the primary boot partition.  In fact Grub gave me some kind of warning (Something to the extent of "Installing to block device can be unreliable) when I had to repair it and I had to --force it.

Oddly enough, I did not have this problem with Debian Lenny.

---

### Post by Jack3500 on 2010-04-18
I've tried more things like creating my own picture and using smaller ones and im still doesnt work :(

---

### Post by Jack3500 on 2010-04-18
Well so far i have no luck but i was able to change the colour of text, which i kinda dont want to do :P

---

### Post by elliotn on 2010-04-18
try this guide it worked for me this morning

blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/

just get a pic, make it a .tga

---

### Post by elliotn on 2010-04-18
[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/]("http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/")

here it is.
Gr8 guide

---

