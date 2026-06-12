---
title: "Grub2 Splash"
date: 2010-02-14
forum: General Help
---

### Post by speed32219 on 2010-02-14
I'm trying to load a grub2 splash screen. I have followed the procedures on the grub2 wiki ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)). During boot an error flashes across the screen saying it can not find file or directory. I also tried to view the boot log file but that doesn't work either, I did enable it though but there seems to be a kernel problem. Seems to be a problem with Karmic Kola right now per some other posts.
Boot error that flashes on screen for a second as soon as grub starts.
**error: "could not start boot splash no file or directory".**
1.	Here is my /etc/default/grub file.
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="splash" #Removed quiet**
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1200x24,1440x900x24,1280x720x24, 1024x768x24,800x600x24,640x480x24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

2.	Here is the 05_debian_theme entry
The highligted line is the path to the grub boot image.
sudo nano /etc/grub.d/05_debian_theme

# check for usable backgrounds
use_bg=false
[COLOR="Blue"]**if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then**[/COLOR][B]
for i in {/boot/grub,/usr/share/images/grub}/Apollo_17_The_Last_Moon_Shot_Edit1.{png,tga} ; do[/B]
if is_path_readable_by_grub $i ; then
bg=$i
case ${bg} in
*.png) reader=png ;;
*.tga) reader=tga ;;
*.jpg|*.jpeg) reader=jpeg ;;
esac
if test -e /boot/grub/${reader}.mod ; then
echo "Found Debian background: `basename ${bg}`" >&2
use_bg=true
break
fi
fi
done
fi



When I run the update-grub it finds the background imaged and updates the boot.cfg I assume. 
sudo update-grub2
**Found Debian background: Apollo_17_The_Last_Moon_Shot_Edit1.tga**
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found memtest86+ image: /boot/memtest86+.bin
done

Could it be something to do with the 
if [ "$GRUB_TERMINAL_OUTPUT" = "**gfxterm**" ] entry in the 05_debian_theme file above (In blue)?

---

### Post by speed32219 on 2010-02-15
bump

---

