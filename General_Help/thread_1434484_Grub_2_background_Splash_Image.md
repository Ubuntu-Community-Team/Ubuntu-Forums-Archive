---
title: "Grub 2 background Splash Image"
date: 2010-03-20
forum: General Help
---

### Post by bkbilly on 2010-03-20
I am using ubuntu 9.10 64bit and I am trying to change the splash image of grub but I couldn't do anything...
I followed this guide: [http://www.howtoforge.com/how-to-add-a-splash-image-to-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-add-a-splash-image-to-grub-2-on-ubuntu-9.04)
I have followed every step but I didn't manage to change it...
can you help me?

---

### Post by overdrank on 2010-03-20
Moved to General Help

---

### Post by mcoleman44 on 2010-03-20
Post the section of what that howto tells you to change in the debian theme or whatever. And you might have to instal startupmanager and muck with the resolution. Thats what I had to do.

---

### Post by drs305 on 2010-03-20
If you are using the newer versions of Grub 2 the way to include a splash image has been greatly simplified.

Look at line 10 of /etc/grub.d/05_debian_theme.

If it looks something like this:
> 
WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"

you can edit it to point to your own image, wherever it may be. For instance, if you placed it in /boot/grub and it was called "yourimage.png":
> 
WALLPAPER="/boot/grub/yourimage.png"


Save the file, then "sudo update-grub".

If you have an older version of Grub 2, it may have a line which starts:
> for i in {/boot/grub,/usr/share
If so, post that line and also tell us the path and name of the image you want to use.

You can also reference the "GRUB2" link in my signature line for more information on splash images.

---

### Post by bkbilly on 2010-03-20
this is my 05_debian_theme file:
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
  for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Hortensia-1.{png,tga} ; do
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
The only thing I changed was this one: **for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Hortensia-1.{png,tga} ; do**
The image that I am trying to put is this one: **/usr/share/images/grub/Hortensia-l.tga**

---

### Post by drs305 on 2010-03-21
The line looks correct so here's a quick set of troubleshooting questions:

Do you see the Grub2 menu during boot?   
/etc/grub.d/grub
#GRUB_HIDDEN_TIMEOUT="0"

Is Hortensia-1 located in /usr/share/grub?   
ls /usr/share/images/grub

Have you run "sudo update-grub" ?

When you run "sudo update-grub", do you see this in the terminal as the command executes?
"Found Debian background: Hortensia-1.tga"

---

### Post by bkbilly on 2010-03-21
I can see the grub menu.
The image is located here: /usr/share/images/grub/Hortensia-l.tga
I have opened it so I am sure it is there and the name is correct for sure!
Here is the proof:
```
ls /usr/share/images/grub
050817-N-3488C-028.tga                  Glasses_800_edit.tga
2006-02-15_Piping.tga                   Hortensia-1.tga
Aesculus_hippocastanum_fruit.tga        Lake_mapourika_NZ.tga
Apollo_17_The_Last_Moon_Shot_Edit1.tga  Moraine_Lake_17092005.tga
B-1B_over_the_pacific_ocean.tga         Plasma-lamp.tga
BonsaiTridentMaple.tga                  Sparkler.tga
Flower_jtca001.tga                      TulipStair_QueensHouse_Greenwich.tga
Fly-Angel.tga                           Windbuchencom.tga
```

Every time i change something I run the command "sudo update-grub", I have also tried "sudo update-grub2"
nothing works...
When I write these commands it doesn't show me this message: "Found Debian background: Hortensia-1.tga"
It only shows me this:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```


I have dual boot with windows 7...
Do you know anything else that may help me?

---

### Post by drs305 on 2010-03-21
> **bkbilly said:**
> 
Do you know anything else that may help me?

Until you see the "Found Debian background..." in the terminal as update-grub runs you aren't going to get the background image.

Here are some less-common things you could check. Honestly, there is probably a better chance that this will do more as a thread "bump" than what follows:

Is 05_debian_theme executable?
sudo chmod +X /etc/grub.d/05_debian_theme

Is "gfxterm" enabled? It should be as long as you haven't changed this line.
/etc/default/grub:
#GRUB_TERMINAL=console

And just to confirm we are looking at the correct files, try disabling the memtest86+ option (run update-grub and make sure that you don't see a line in the terminal adding memtest86+ to grub.cfg).
```
sudo chmod -x /etc/grub.d/20_memtest86+
```
If you don't think you'd use memtest you can leave it disabled; otherwise you can restore it by running the same command with the *+x* option.

---

### Post by jsriz on 2010-03-21
just ensuring a few things:
1)did you convert the image into .tga format(using gimp) or just replaced the extension?(just asking cos your tutorial dosent mention it) 
2)what do you get at the grub ,the same thing that you get before you tried all this or any change?(you get someting different, if it is a resolution issue)

---

### Post by bkbilly on 2010-03-21
> **drs305 said:**
> Until you see the "Found Debian background..." in the terminal as update-grub runs you aren't going to get the background image.

Here are some less-common things you could check. Honestly, there is probably a better chance that this will do more as a thread "bump" than what follows:

Is "gfxterm" enabled? It should be as long as you haven't changed this line.
/etc/default/grub:
#GRUB_TERMINAL=console

Problem solved!!!
I had changed the line "**#GRUB_TERMINAL=console**"
I didn't remember that I did...
thank you everybody Very Mach for your help!!!

---

### Post by jettechfsr on 2010-08-10
> **drs305 said:**
> If you are using the newer versions of Grub 2 the way to include a splash image has been greatly simplified.

Look at line 10 of /etc/grub.d/05_debian_theme.

If it looks something like this:

you can edit it to point to your own image, wherever it may be. For instance, if you placed it in /boot/grub and it was called "yourimage.png":


Save the file, then "sudo update-grub".

If you have an older version of Grub 2, it may have a line which starts:

If so, post that line and also tell us the path and name of the image you want to use.

You can also reference the "GRUB2" link in my signature line for more information on splash images.

Thanks so much was having problems tell I saw this and did sudo update-grub then everything worked

---

