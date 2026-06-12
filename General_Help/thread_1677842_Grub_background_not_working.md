---
title: "Grub background not working"
date: 2011-01-29
forum: General Help
---

### Post by c2tarun on 2011-01-29
I tried to use an image of name splash.png as background of grub boot menu.

here is my output of `sudo update-grub`
```

Generating grub.cfg ...
Found background image: splash3.png
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda5
done

```

Image is of resolution 640x480
but still grub boot menu is not showing any background.
Can anybody please help?

---

### Post by Rubi1200 on 2011-01-29
Did you edit the 05_debian_theme file?

Can you post the contents please so we can take a look?

Thanks.

---

### Post by c2tarun on 2011-01-29
> **Rubi1200 said:**
> Did you edit the 05_debian_theme file?

Can you post the contents please so we can take a look?

Thanks.

I forgot to mention one thing, I have two distros installed on my system in different partitions.
Yes, I edited the 05_debian_theme file in both the distros.
here is the content of my 05_debian_theme file

```

#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/splash3.png"
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
#use_bg=false
use_bg=true
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

```The above file is from kubuntu. I first installed kubuntu and then installed ubuntu.

---

### Post by c2tarun on 2011-01-29
bump

---

### Post by Rubi1200 on 2011-01-30
Silly question, but which OS controls booting? If Ubuntu, since you installed it, last then you probably need to run the update-grub command there to get things working.

---

### Post by c2tarun on 2011-01-30
I got this error, when I tried to run update-grub from ubuntu.

```

Generating grub.cfg ...
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.

```

Can anyone please explain.
Thanks

---

### Post by c2tarun on 2011-01-30
I changed the location of splash3.png file
now this file is in folder /boot/image/splash3.png

now my 05_default_theme file look like this
```

#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/boot/image/splash3.png"
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
use_bg=true
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

```now when I executed 'sudo update-grub'

my new message is:
```

Generating grub.cfg ...
Found background image: splash3.png
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done

```but still I can't see any background image in my grub boot menu.

my laptop screen is of resolution 1366x768. The splash3.png file is of resolution 640x480
Can that be a problem?

---

### Post by Rubi1200 on 2011-01-30
Not sure what is going on there and I have asked someone to take a look so hang in there.

In the meantime, please post the contents of the file>  /etc/default/grub

Thanks.

---

### Post by c2tarun on 2011-01-30
> **Rubi1200 said:**
> Not sure what is going on there and I have asked someone to take a look so hang in there.

In the meantime, please post the contents of the file

Thanks.

here is my /etc/default/grub file
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by drs305 on 2011-01-30
Grub 2 has several major revisions now, and the way images are registered has changed several times. We may need to see the contents of /boot/grub/grub.cfg, since your menu is based on what is included in that file. But let's check something else first.

Since the latest update-grub command is finding your splash3 image file, I suspect the problem is with that file. 

In troubleshooting these types of problems, I generally find it useful to install grub2-splashimages, since I *know* these images will work with Grub2.
```

sudo apt-get install grub2-splashimages

```
They will be downloaded to */usr/share/images/grub/*. Find one you like and copy it to the same location as your splash3 image (boot/image). Change the name in your 05_debian_theme file to match your new selection, update-grub and make sure the new image is found in the terminal output. Then reboot and see if the new image appears as a background.

If it does, it means your splash3 image probably doesn't meet the requirements of Grub 2. Since we know it's a png image, make sure it's in RGB format and not indexed. You can check with GIMP using the Image > Mode menu options.

Note: The later versions of Grub2 will stretch the image to make it work at various resolutions, so I don't think that is the issue here.

---

### Post by Cavsfan on 2011-01-30
I have had this issue before and a lot of times I just took the picture into **Gimp** and clicked **Image** and then **Scale Image**.
Then made sure it was set to the correct size and clicked **Scale**.
Then I just saved it after doing this and it worked. And I use 1920x1200 pictures for my Grub.

Not sure why this approach worked, but it has worked on more than one of my pics.

Just my 2 cents.

---

### Post by c2tarun on 2011-01-30
> **drs305 said:**
> Grub 2 has several major revisions now, and the way images are registered has changed several times. We may need to see the contents of /boot/grub/grub.cfg, since your menu is based on what is included in that file. But let's check something else first.

Since the latest update-grub command is finding your splash3 image file, I suspect the problem is with that file. 

In troubleshooting these types of problems, I generally find it useful to install grub2-splashimages, since I *know* these images will work with Grub2.
```

sudo apt-get install grub2-splashimages

```They will be downloaded to */usr/share/images/grub/*. Find one you like and copy it to the same location as your splash3 image (boot/image). Change the name in your 05_debian_theme file to match your new selection, update-grub and make sure the new image is found in the terminal output. Then reboot and see if the new image appears as a background.

If it does, it means your splash3 image probably doesn't meet the requirements of Grub 2. Since we know it's a png image, make sure it's in RGB format and not indexed. You can check with GIMP using the Image > Mode menu options.

Note: The later versions of Grub2 will stretch the image to make it work at various resolutions, so I don't think that is the issue here.

Ya you are right, the problem was with my image file. Two questions please
1. When I was trying to download grub2-splashimages during day time today, I got a error of package not found. Why so?
2. Is there anyway that we can make our images compatible with the type supported by grub2?

---

### Post by Cavsfan on 2011-01-30
> **c2tarun said:**
> Ya you are right, the problem was with my image file. Two questions please
1. When I was trying to download grub2-splashimages during day time today, I got a error of package not found. Why so?
2. Is there anyway that we can make our images compatible with the type supported by grub2?

See my post above this one. Gimp has always worked for me.
And if you remove the [COLOR="Red"]#[/COLOR] sign in front of the resolution at the bottom of **/etc/default/grub** and set this to your default monitor resolution, you can use that size picture for Grub.

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[COLOR="Red"]#[/COLOR]GRUB_GFXMODE=[COLOR="RoyalBlue"]640x480[/COLOR]
```.
I have mine set to 1920x1200-24. (24 bit color depth) Another reason I have had to use Gimp to get the 24 bit color depth.

---

### Post by c2tarun on 2011-01-30
> **Cavsfan said:**
> See my post above this one. Gimp has always worked for me.
And if you remove the [COLOR=Red]#[/COLOR] sign in front of the resolution at the bottom of **/etc/default/grub** and set this to your default monitor resolution, you can use that size picture for Grub.

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[COLOR=Red]#[/COLOR]GRUB_GFXMODE=[COLOR=RoyalBlue]640x480[/COLOR]
```.
I have mine set to 1920x1200-24. (24 bit color depth) Another reason I have had to use Gimp to get the 24 bit color depth.

OK :)
Can you please tell me how can i edit the entries of grub menu, I want to remove some entries and change name of some.

---

### Post by drs305 on 2011-01-30
The grub2-splashimages is located in the *Universe* repository. Make sure it is enabled: System > Administration > Synaptic > Settings > Repositories > Ubuntu Software tab.

There are different Grub2 files which can be edited. Normally the changes are made in /etc/default/grub. As you have already found, some changes are made to the scripts in /etc/grub.d

Several of the linked guides in my signature line discuss editing Grub2 selections. "Basics" covers most of them, while "Tasks" covers the ones most often changed by users.

If you have questions about how to make a specific change and can't find the answer, just ask here.

An excellent new tool for editing the Grub2 configuration settings is Grub Customizer. I wrote a guide on how to use it. See the link for "Customizer".

---

### Post by Cavsfan on 2011-01-30
> **c2tarun said:**
> OK :)
Can you please tell me how can i edit the entries of grub menu, I want to remove some entries and change name of some.

Not meaning to step on **drs305**'s toes as he is the GRUB go-to person around here even for me! He knows more about this stuff than I ever will.
But, you might also find some of the answers to your questions in the Tutorial in my sig.

---

### Post by c2tarun on 2011-01-30
Thanks a lot guys :)

---

### Post by Cavsfan on 2011-01-30
> **c2tarun said:**
> Thanks a lot guys :)
You are most welcome! And you should bookmark **drs305**'s links as he is the person that knows GRUB.
I only know a tiny portion and a friend on here told he how to do that. I just converted what he told me into a tutorial for all to benefit from.

---

### Post by drs305 on 2011-01-30
> **Cavsfan said:**
> You are most welcome! And you should bookmark **drs305**'s links as he is the person that knows GRUB.
I only know a tiny portion and a friend on here told he how to do that. I just converted what he told me into a tutorial for all to benefit from.


I have Cavsfan's guide bookmarked and refer users to it. It's a great way to have a customized menu that doesn't need tending. Even with Grub Customizer now available a 'set it once and forget it' method is a great option for many users.

---

### Post by Rubi1200 on 2011-01-30
> **c2tarun said:**
> Thanks a lot guys :)
Glad you got it all sorted out now :-)

As Cavsfan already mentioned, bookmark the guides by drs305; they are an invaluable resource.

By the way, the guide by Cavsfan is pretty good too!

---

### Post by Cavsfan on 2011-01-30
Thank you! :redface:

Here is my latest screen shot and this is as simple you can get with dual booting. 

[[IMG]http://ompldr.org/tNzV0cQ[/IMG]]("http://ompldr.org/vNzV0cQ")

---

### Post by c2tarun on 2011-01-30
> **Rubi1200 said:**
> Glad you got it all sorted out now :-)

As Cavsfan already mentioned, bookmark the guides by drs305; they are an invaluable resource.

By the way, the guide by Cavsfan is pretty good too!

sure :)
I'll bookmark the whole thread. Whole thread is very valuable to  me.
Thanks

---

