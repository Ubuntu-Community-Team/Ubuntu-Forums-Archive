---
title: "Grub2 background issues"
date: 2010-02-24
forum: General Help
---

### Post by Arkitekt on 2010-02-24
I just upgraded from UNR 9.04 to UNR 9.10, already had GRUB2 1.96 installed on 9.04 and had successfully had a background image displayed. 

After upgrading my GRUB2 was 1.97beta4, i opted to keep ny current 05_debian_theme during upgrade, so i just verifed that gfxmode was set correctly in 00_header and went to change use_bg to "true" in 05_debian_theme. After doing so i ran sudo update-grub and got this:

$ sudo update-grub
Generating grub.cfg ...
Warning: update-grub_lib is deprecated, use grub-mkconfig_lib instead
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.

if i change use_bg to false then I do not get this error, but i don't get a bg image either.

my 05_debian_theme looks like this

```
# check for usable backgrounds
use_bg=true
if [ "$GRUB_TERMINAL" = "gfxterm" ] ; then
  for i in {/usr/share/images/desktop-base}/ubuntu_nurse2.{png,tga} ; do
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

```

I was also reading [https://help.ubuntu.com/community/Grub2#Themes](https://help.ubuntu.com/community/Grub2#Themes) where it said 
>  In later versions of Grub 2 (1.97 and later), found in testing versions of Lucid Lynx 10.04, the line:

    *

      ">for i in {/boot/grub,/usr/share/images/desktop-base}..." has been replaced with a simplified line:

      WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"

however, not sure exactly what I need to do to properly display a bg image in grub2, any help is appreciated

---

### Post by Arkitekt on 2010-02-25
anyone able to help?

---

### Post by Arkitekt on 2010-02-25
I found a couple of posts while googling this issue that mentioned not to set use_bg to true and to leave it as false, however when it is set to false update-grub2 doenst say it has found a background image... not sure what is going on in 1.97beta4 but it isnt working as good as 1.96

---

### Post by jh5637 on 2010-02-25
I'm having the same issue Arkitekt.  How do I find out what version of GRUB I have?  Is it recommended to revert back to a previous version?  I would really like to make this tweak work.  I'm a noob and find my new Linux world a breath of fresh air from the smog infested WinWorld.  I find problems like these intrigue me rather than discourage.  Knowing me I'll keep at this forever until I find a fix.  Here is my code in case someone is wondering:

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
use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/ubuntuhhok6.{png,tga} ; do
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
fi

---

### Post by Arkitekt on 2010-02-25
the check grub version type 'grub-setup -v' in terminal (without ') 

for now I have set use_bg to false, not sure why it isn't working like it did in 1.96, very frustrated

---

### Post by jh5637 on 2010-02-25
Thanx Arkitekt.  Hopefully someone will come up with a reason and a fix as to why this grub splash screen tweak isn't working.  I'm not complaining though, Linux is far more lucid that my Windows machine ever was.

---

### Post by jh5637 on 2010-02-28
Hey Arkitekt...I tried that command you posted and got this error:

jimmy@ubuntu:~$ grub-setup-v
grub-setup-v: command not found
jimmy@ubuntu:~$ grub-setup -v
No device is specified.
Try ``grub-setup --help'' for more information.
jimmy@ubuntu:~$ grub-setup -v
No device is specified.
Try ``grub-setup --help'' for more information.
jimmy@ubuntu:~$ grub-setup --help
Usage: grub-setup [OPTION]... DEVICE

Set up images to boot from DEVICE.
DEVICE must be a GRUB device (e.g. ``(hd0,1)'').

  -b, --boot-image=FILE   use FILE as the boot image [default=boot.img]
  -c, --core-image=FILE   use FILE as the core image [default=core.img]
  -d, --directory=DIR     use GRUB files in the directory DIR [default=/boot/grub]
  -m, --device-map=FILE   use FILE as the device map [default=/boot/grub/device.map]
  -r, --root-device=DEV   use DEV as the root device [default=guessed]
  -f, --force             install even if problems are detected
  -h, --help              display this message and exit
  -V, --version           print version information and exit
  -v, --verbose           print verbose messages

Report bugs to <bug-grub@gnu.org>.
jimmy@ubuntu:~$ 


Any idea why I'm getting this? Did I mistype something?  Man...I'm really loving Linux...even thinking about taking some courses or just really digging into some Interweb schooling.  Any suggestions on where I can get some good material and really start messing around with Linux?

---

### Post by Arkitekt on 2010-02-28
I was at fault a bit, I put -v (which is verbose) when it should be -V (Version) 

Does look like you didnt put a space between grub-setup and -V though, needs to be a space before you put the option so it should be:

grub-setup -V

---

### Post by mechanic on 2010-03-06
So why not edit your previous post? I tried the command as written, then after running the --help option realised the typo - as you explained later. Editing the original would be neater!

---

### Post by andrewthomas on 2010-03-07
> **Arkitekt said:**
> . 

After upgrading my GRUB2 was 1.97beta4, i opted to keep ny current 05_debian_theme during upgrade,
This, I believe, is where you went wrong.  You probably should have let it replace and edited that.  

```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  **WALLPAPER="/usr/share/images/grub/Plasma-lamp.tga"**
  COLOR_NORMAL="white/black"
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
```The wallpaper line is all that I changed in this file.

---

