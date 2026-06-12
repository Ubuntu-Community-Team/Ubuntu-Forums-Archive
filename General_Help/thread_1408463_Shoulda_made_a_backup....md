---
title: "Shoulda made a backup..."
date: 2010-02-16
forum: General Help
---

### Post by huggs on 2010-02-16
Can somebody please type " gksudo gedit /etc/grub.d/05_debian__theme " into thier terminal and then copy and paste all the text in that file into code brackets in a reply for me? I seem to have turned it into a blank file and it doesnt seem to be posted anywhere on the internet as far as I can tell. Thanks  :oops:

---

### Post by jblaven on 2010-02-16
> **huggs said:**
> Can somebody please type " gksudo gedit /etc/grub.d/05_debian__theme " into thier terminal and then copy and paste all the text in that file into code brackets in a reply for me? I seem to have turned it into a blank file and it doesnt seem to be posted anywhere on the internet as far as I can tell. Thanks  :oops:

Looks like mine is empty too, so I guess it is OK.  lol

---

### Post by stoneage on 2010-02-16
Mine looks like this:-
> #!/bin/bash -e

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


---

### Post by huggs on 2010-02-16
thats exactly what i needed! thank you so much, i should have backed it up in the first place, but i thought "how could i screw up editing a simple text file?". :oops:  thanks

---

