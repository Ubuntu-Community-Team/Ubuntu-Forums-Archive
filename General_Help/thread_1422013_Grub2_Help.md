---
title: "Grub2 Help"
date: 2010-03-04
forum: General Help
---

### Post by JrBiem on 2010-03-04
I logged in as root so that I could save my image in /usr/share/images/grub

Then I resized the image to 640x480 and changed it over to .tga forma.

I then altered the 05_debian_theme(etc/grub.d) file to look like this (red font = a change was made):

#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

set_mono_theme()
{
  cat << EOF
set menu_color_normal=black/white
set menu_color_highlight=white/black
EOF
}

# check for usable backgrounds
[COLOR=Red]use_bg=true[/COLOR]
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base[COLOR=Red],/usr/share/images/grub}/MaxLinuxPenguin[/COLOR].{png,tga} ; do
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


Then I ran the update-grub command which gave this output:

  	 	 	 	 	 	  error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 Generating grub.cfg ... 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 [COLOR=Red]Found Debian background: MaxLinuxPenguin.tga [/COLOR]
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 Found linux image: /boot/vmlinuz-2.6.31-20-generic 
 Found initrd image: /boot/initrd.img-2.6.31-20-generic 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 Found memtest86+ image: /boot/memtest86+.bin 
 Found Windows 7 (loader) on /dev/sda2 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 Found Windows 7 (loader) on /dev/sda3 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 error: cannot open `/dev/sdb' while attempting to get disk size 
 done 
 

I made the font red where it says it found the background image.  But I don't understand why all of those errors are there, and also the image does not load when the system boots.  If anyone can offer some help I would appreciate it very much so.

---

