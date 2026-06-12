---
title: "grub splash screen problem"
date: 2009-11-08
forum: General Help
---

### Post by confused_user on 2009-11-08
Hi, i was following a guide on here to edit /etc/grub.d/05_debian_theme to add a grub splash image, it wont work though.

i get the following error when i do an update-grub

matt@matt-netbook:/etc/default$ sudo update-grub
Generating grub.cfg ...
/etc/grub.d/05_debian_theme: line 28: syntax error near unexpected token `fi'

here is the whole file, can anyone see whats wrong? (i stupidly did not back up the original file so i have no point of reference) - in fact it would really help if somebody could post their /etc/grub.d/05_debian_theme for me to look at :)

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
  for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Moraine_Lake_17092005.tga.{png,tga} ; do
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

### Post by c-oss on 2010-03-12
i want to reply but when i go to my terminal my computer freezes - so i'm confused too! I have just been looking into splash screens and am interested in a response
i am using 9.10 xubuntu - what version are you using?

---

### Post by confused_user on 2010-04-09
9.10, for some reason after just deleting and trying again and again and again it worked, but then i could not see the text due to a colour clash.

Got the same problem with trying to change the text colours.

In short the solution is to leave well alone since grub2 is still buggy as hell and should not be used in this state let alone reconfigured.

---

