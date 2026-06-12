---
title: "Grub 2, Login Screen &amp; Ubuntu Customization."
date: 2010-12-12
forum: General Help
---

### Post by avin7000 on 2010-12-12
1. I followed the tutorial mentioned in this link - [http://ubuntuforums.org/showthread.php?p=8082954](http://ubuntuforums.org/showthread.php?p=8082954)

& I have removed all unwanted entries from my boot menu. There are only two left, one for Ubuntu & another Windows 7. I just want to rename Ubuntu to Macbuntu, in boot menu. How to do it ? I am not able to understand the steps given in the link I mentioned above.

2. The boot menu looks so simple in black & white, is it possible to put desired background image ?

3. During system shut down, Ubuntu 10.10 splash screen appears at last. How to change it ? I have installed Macbuntu, I thought it'd change it, but it didn't.

4. How to make the windows [i.e. black background in opened window] to appear like this, I have already installed macbuntu,

[img]http://i52.tinypic.com/2gt9op1.jpg[/img]

Thanks in advance :)

---

### Post by Atamisk on 2010-12-12
Due to my limited Linux experience, I can only answer #2 for you. 

[Follow this Tutorial]("http://linuxers.org/howto/how-change-grub2-splash-images")

That should do it for you.

Hopefully ones more experienced than I can help you further!

Cheers,

---

### Post by avin7000 on 2010-12-12
Thank you, reading it now :)

---

### Post by tajiknomi on 2010-12-12
[SIZE=2]You can rename the name of ubuntu to macbuntu or whatever you want by just opening 
If you are using Grub-2,then
[/SIZE]```
[SIZE=3]sudo gedit /boot/grub/grub.cfg[/SIZE]
```[SIZE=2]
[/SIZE][SIZE=2]Make sure,it quite risky to edit it[/SIZE],[SIZE=2]so it will be much better to first make a backup of your grub.cfg.[/SIZE]

```
[SIZE=3]sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg_backup[/SIZE]
```[SIZE=2]Incase if something went wrong from you their,not problem then...:p

I had attached a screen-shot, in which i had rename "Ubuntu" to "Ubuntu-lucid"
[/SIZE]

---

### Post by avin7000 on 2010-12-12
But somewhere I had read .cfg file shouldn't be edited ! 

But still I am ready to do what you have suggested me :)

---

### Post by tajiknomi on 2010-12-12
> **avin7000 said:**
> But somewhere I had read .cfg file shouldn't be edited ! 

But still I am ready to do what you have suggested me :)

[SIZE=2]Yes, you are right, but not the case with here,.... I will not advise you in case when you are going to add new OS-Entry or some more operations are done like Time-setting within grub,Resolutions,etc etc...because it is automatically generated from[/SIZE][SIZE=2][COLOR=Black]**/etc/default/grub ** & [/COLOR][/SIZE][SIZE=2]***/etc/grub.d/40_custom, ***For more information , read out > [/SIZE][http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by avin7000 on 2010-12-12
this is my 05_debian_theme file, in which following not line is not present

> for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do

the link you guys have given, says that I need to edit this line to have customized background

```
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
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
use_bg=false
for output in ${GRUB_TERMINAL_OUTPUT}; do
  if [ "$output" = "gfxterm" ] ; then
    for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
      if is_path_readable_by_grub $i ; then 
        bg=$i
        case ${bg} in
          *.png)		reader=png ;;
          *.tga)		reader=tga ;;
          *.jpg|*.jpeg)	reader=jpeg ;;
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
```

I think I have to edit this line,

> for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do

am I right ?

---

### Post by avin7000 on 2010-12-12
@tajiknomi - okay, thank you :)

---

### Post by tajiknomi on 2010-12-12
Check out the line:-

```
[SIZE=2]WALLPAPER="[SIZE=3]/usr/share/images/[/SIZE]***[SIZE=3]desktop-base/moreblue-orbit-grub.png[/SIZE]***[/SIZE]"
```[SIZE=2]
You just has to change it with the path of folder, I means the Bold area...

For details > [/SIZE][http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Splashimages.html")

C[SIZE=2]heck out the 8th line of your 05_debian_theme & you will see it...[/SIZE]

---

### Post by avin7000 on 2010-12-12
I have successfully edited the Boot menu :D Thanks again :)

okay, now trying background image

---

### Post by avin7000 on 2010-12-12
Success ! thanks again :) :)

Any idea about splash screen which comes during shutdown ? [My 3rd question]

---

### Post by ajgreeny on 2010-12-12
Sorry, but you can not do that as simply as tajiknomi says because** grub.cfg** is read only, so it can not be edited with that command, and there is really no point doing so as the next time update-grub is run, either manually, or when a new kernel is installed in updates, any edit you have made will disappear, and the file will revert to the default.

You really need to learn to edit the files in **/etc/grub.d** to do what you want properly.  Just make sure you back up then you can always restore the original with a live CD if you need to to get back to where you started.

EDIT:
OK, I'm too late.  However I repeat that you should learn to edit the /etc/grub.d files in order to a) Learn about grub2 rather better than you do at the moment, and b) avoid having to keep re-making those edits every time update-grub is run.

---

### Post by avin7000 on 2010-12-12
Thanks for replying, I agree with what you're saying, but according to me his method is quite simple. I use ubuntu tweak to remove kernels & with his method to rename it. [And yeah, it can be bottleneck to edit it everytime we update-grub]

---

### Post by tajiknomi on 2010-12-12
> **avin7000 said:**
> Success ! thanks again :) :)

Any idea about splash screen which comes during shutdown ? [My 3rd question]

[SIZE=2]I had never done that..but i have just seen it in Configuration-Editor(Application>System-tools) or you can Open it alternatively by alt+f2 and then type their "gconfig-editor"

i had just open up a menu and see this...>check out my screen-shot.

apps >gnome-session >options
[/SIZE]

---

### Post by Quackers on 2010-12-12
ajgreeny is correct. It's easier to edit grub.cfg but the next time there is an update to grub your changes will be over-written. The correct (and permanent) way to do it is by folowing drs305's guide, as previously linked to.

---

### Post by avin7000 on 2010-12-12
Guys I am okay with his solution, because I am not able understand from that post [I had already mentioned it in my first post]. If anyone explains me, then I am ready to do it :) 

@tajikomi - I don't have Gnome-session & also after running "gnome-session" I got file not found error.

---

### Post by tajiknomi on 2010-12-12
> **ajgreeny said:**
> Sorry, but you can not do that as simply as tajiknomi says because** grub.cfg** is read only, so it can not be edited with that command, and there is really no point doing so as the next time update-grub is run, either manually, or when a new kernel is installed in updates, any edit you have made will disappear, and the file will revert to the default.

You really need to learn to edit the files in **/etc/grub.d** to do what you want properly.  Just make sure you back up then you can always restore the original with a live CD if you need to to get back to where you started.

EDIT:
OK, I'm too late.  However I repeat that you should learn to edit the /etc/grub.d files in order to a) Learn about grub2 rather better than you do at the moment, and b) avoid having to keep re-making those edits every time update-grub is run.

[SIZE=2]I Agree what you said, but can you plz post the way that someone ***Rename Os ***in Grub(other then i mentioned), so that i can also learn that way..?i think its the only way to edit the OS name >to edit grub.cfg/menu.list, may be i am wrong.....correct me for that :p, 
[/SIZE]

---

### Post by tajiknomi on 2010-12-12
> **avin7000 said:**
> I don't have Gnome-session & also after running "gnome-session" I got file not found error.

[SIZE=2]once you had open-up Configuration-Editor, Go to >apps > gnome-session >Options,

i don't know why ***gnome-session ***is missing in your ***configuration-menu***,
[/SIZE]

---

### Post by avin7000 on 2010-12-12
Actually I am not able to find configuration-editor

---

### Post by tajiknomi on 2010-12-12
> **avin7000 said:**
> Actually I am not able to find configuration-editor

[SIZE=2]press alt+f2 and type their "***gconfig-editor***" and Configuration-menu will pop-up[/SIZE]

---

### Post by Quackers on 2010-12-12
Or gconf-editor

---

### Post by avin7000 on 2010-12-12
uploaded the screenshot

---

### Post by avin7000 on 2010-12-12
Yeah, gconf-editor opened !

---

### Post by tajiknomi on 2010-12-12
[SIZE=2]Once you had open up option, u just have to tick "***Show-splash-screen***", and then select the path of your desire picture from the last option given i-e "***Splash***-***image***", am sure it will solve your problem....

I feels sleepy ;)....Keep posting , many peoples are here to help you out........


Happy ubuntu-uing...
[/SIZE]

---

### Post by avin7000 on 2010-12-12
I have edited the entry, but I see no changes :(

or else, Is it possible to change the text ? "Ubuntu 10.10" which appears ? I am okay with background

---

### Post by drs305 on 2010-12-12
avin7000,

Make a backup copy, make it un-executable, then open /etc/grub.d/10_linux

```

sudo cp /etc/grub.d/10_linux /etc/grub.d/10_linux.bak
sudo chmod -x /etc/grub.d/*.bak
gksu gedit +130 /etc/grub.d/10_linux
```

If you want to see:
[B]Macbuntu, with Linux 2.6.32-24-generic-pae
[/B]
Add **OS** to the section below.

If you want to see this:
**Macbuntu, with Linux**
Add **version**

  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
**OS="Macbuntu"**
**version=" "**

If you want to see this:
**Macbuntu**
Add the above, and find  this section:
>   if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi

and change it to:
> #  if ${recovery} ; then
#    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
#  else
#    title="$(gettext_quoted "%s, with Linux %s")"
#  fi
  if ${recovery} ; then
    title="$(gettext_quoted "%s %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s  %s")"
  fi

Update grub to make the changes after saving the file.

```
sudo update-grub
```

---

### Post by avin7000 on 2010-12-13
@drs305 - first of all thank you for such nice a tutorial :)

and success I have now renamed it to Macbuntu, exactly what I wanted !

Now, how to edit Windows 7 (loader) (on /dev/sda2) ???

I want to rename it to "Windows 7 Pro"

---

### Post by drs305 on 2010-12-13
> **avin7000 said:**
> @drs305 - first of all thank you for such nice a tutorial :)

and success I have now renamed it to Macbuntu, exactly what I wanted !

Now, how to edit Windows 7 (loader) (on /dev/sda2) ???

I want to rename it to "Windows 7 Pro"

This is approximately it. Make sure the title in [COLOR="DarkGreen"]green[/COLOR] matches exactly what is currently in the quoted section of the first line in the menuentry in /boot/grub/grub.cfg.

Open 30_os-prober for editing:
```
gksu gedit +150 /etc/grub.d/30_os-prober
```

Color Coding:
[COLOR="Navy"]Blue: Everything between # symbols is added.[/COLOR]
[COLOR="Red"]Red:  Optional. If only want the "Windows 7 Pro" to apply to a specific partition. Change "sda1" to the appropriate value. If you want to universally replace with "Windows 7 Pro" do not include this section.[/COLOR]
[COLOR="DarkGreen"]Green: Old title exactly as it appears on menu (between quotes in menuentry and without the 'on /dev/sdXX').[/COLOR]
**[COLOR="Black"]Bold Black: New Title[/COLOR]**



> if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

[COLOR="Navy"]# Added to change "Windows Recovery Environment (loader)" to "Windows Vista"[/COLOR]
if [ "$LONGNAME" = "[COLOR="DarkGreen"]Windows 7 (loader)[/COLOR]" ][COLOR="Red"] && [ "${DEVICE}" = "/dev/sda1" ][/COLOR] ; then
LONGNAME="[COLOR="Black"]**Windows 7 Pro**[/COLOR]"
fi
[COLOR="Navy"]# End Added[/COLOR]

Save the file and update grub.

---

### Post by avin7000 on 2010-12-14
thank you so much mate :)

---

