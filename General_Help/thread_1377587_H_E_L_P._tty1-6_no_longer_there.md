---
title: "H E L P. tty1-6 no longer there?"
date: 2010-01-10
forum: General Help
---

### Post by Jackzor on 2010-01-10
I have been googling for hours upon hours and I have found one other thread about this...: [http://ubuntuforums.org/showthread.php?t=1373197](http://ubuntuforums.org/showthread.php?t=1373197)

And then there is my other thread :[http://ubuntuforums.org/showthread.php?t=1377000](http://ubuntuforums.org/showthread.php?t=1377000)


Anyways. I try to pull up tty1-6 and none show anything but a cursor in the top left corner of the screen. What I did before this happened was:

I followed a tutorial that I found on the web. 

[http://ubuntuforums.org/showthread.php?t=1377000](http://ubuntuforums.org/showthread.php?t=1377000)

It worked perfectly, I changed the xsplash background.

Also I edited the the grub to put a background on it.

I used the command:

gksudo gedit /etc/grub.d/05_debian_theme

Thats all I got for you. Please tell me what happened.

---

### Post by Jackzor on 2010-01-10
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
use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/ubuntu.{png,tga} ; do
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
  set color_highlight=black/white
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


The file I edited before It broke.

---

### Post by impact on 2010-01-10
Did you make a backup copy of the file before editing? If so, restore it, reboot and see if it works.

---

### Post by Jackzor on 2010-01-10
Yes I did. And I have already tried it.

Doesn't work...

:(

---

### Post by Jackzor on 2010-01-11
bump

---

### Post by Iowan on 2010-01-11
**ps -ef** on my machine shows ```
root         1     0  0 14:56 ?        00:00:02 /sbin/init

root      4270     1  0 14:57 tty4     00:00:00 /sbin/getty 38400 tty4
root      4271     1  0 14:57 tty5     00:00:00 /sbin/getty 38400 tty5
root      4275     1  0 14:57 tty2     00:00:00 /sbin/getty 38400 tty2
root      4276     1  0 14:57 tty3     00:00:00 /sbin/getty 38400 tty3
root      4281     1  0 14:57 tty6     00:00:00 /sbin/getty 38400 tty6

```Doubt this helps...

---

### Post by Jackzor on 2010-01-13
> **Iowan said:**
> **ps -ef** on my machine shows ```
root         1     0  0 14:56 ?        00:00:02 /sbin/init

root      4270     1  0 14:57 tty4     00:00:00 /sbin/getty 38400 tty4
root      4271     1  0 14:57 tty5     00:00:00 /sbin/getty 38400 tty5
root      4275     1  0 14:57 tty2     00:00:00 /sbin/getty 38400 tty2
root      4276     1  0 14:57 tty3     00:00:00 /sbin/getty 38400 tty3
root      4281     1  0 14:57 tty6     00:00:00 /sbin/getty 38400 tty6

```Doubt this helps...

Yeah.. I'm not exactly sure what that was supposed to show me.. or do.. or whatever.

---

### Post by Jackzor on 2010-01-15
So its still not there?

---

### Post by falconindy on 2010-01-15
You're not, by chance, trying to use the right alt key, are you? By default, that's not Alt... That's AltGr, or Alt Graph.

Anyways, I'm fairly sure Iowan was trying to imply that you should do the same (ps -ef) to ensure that those gettys really aren't getting created.

---

