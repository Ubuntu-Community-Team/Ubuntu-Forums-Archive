---
title: "No splash image on GRUB2"
date: 2009-10-30
forum: General Help
---

### Post by Fibonacci on 2009-10-30
I've just installed Karmic and noticed there is no splash image on GRUB2. Even after installing grub2-splashimages, changing /etc/grub.d/05_debian_theme accordingly and running update-grub AND update-grub2, no image is displayed.

Any help would be appreciated.

---

### Post by Fibonacci on 2009-10-30
Here's the relevant section of /etc/grub.d/05_debian_theme:
```
# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub/}/Plasma-lamp.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)          reader=png ;;
        *.tga)          reader=tga ;;
        *.jpg|*.jpeg)   reader=jpeg ;;
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

And yes, the file /usr/share/images/grub/Plasma-lamp.tga does exist.
This is the output upon running update-grub (as root, of course):

```
Generating grub.cfg ...
Found Debian background: Plasma-lamp.tga
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done
```

and this is the relevant section of /boot/grub/grub.cfg:

```
### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 092586b6-f367-48c1-a979-0014ea02ed0e
insmod tga
if background_image /usr/share/images/grub/Plasma-lamp.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###
```

Yet I still see no image.

---

### Post by Uncle Spellbinder on 2009-10-30
Yep. Fresh install, different computer, never had an Ubuntu install or Grub. I still see the same ol' grub boot.  Seems grub 2 is all hype and NO substance.

---

### Post by Fibonacci on 2009-10-31
Actually, that would mean GRUB2 is actually **worse**, because on the old GRUB I could always change the splash image.
It does look slightly different from GRUB, though.

---

### Post by Zoot7 on 2009-10-31
You've to do a bit more jumping through hoops this time sadly.

Here's a good guide I found earlier today about changing the splash image on Grub 2.
**[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html]("http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html")**

---

### Post by Fibonacci on 2009-10-31
> **Zoot7 said:**
> You've to do a bit more jumping through hoops this time sadly.

Here's a good guide I found earlier today about changing the splash image on Grub 2.
**[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html]("http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html")**

That is exactly what I did the first time. It didn't work this time either.

---

### Post by Zoot7 on 2009-10-31
> **Fibonacci said:**
> That is exactly what I did the first time. It didn't work this time either.
Try moving your image to /boot/grub if you haven't already.
It's what sorted the problem for me.

---

### Post by djuliette on 2009-10-31
is it this maybe:

/usr/share/images/grub**/**}**/**Plasma-lamp.{png,tga}

a double /?

I was able to get mine working without a hitch, I just did what you did, edit the 05_debian_theme file and add the directory and filename and update-grub

---

### Post by Fibonacci on 2009-10-31
> **Zoot7 said:**
> Try moving your image to /boot/grub if you haven't already.
It's what sorted the problem for me.

Still nothing.

> **djuliette said:**
> is it this maybe:

/usr/share/images/grub**/**}**/**Plasma-lamp.{png,tga}

a double /?

I was able to get mine working without a hitch, I just did what you did, edit the 05_debian_theme file and add the directory and filename and update-grub

Didn't work, and this time update-grub didn't print a line about a Debian background having been found.

---

### Post by Fibonacci on 2009-10-31
Update: when running "background_image /usr/share/images/grub/Plasma-lamp.tga" on the GRUB2 console I get the following error message:
Error: no video mode activated

I found that this exact bug had been reported on Debian, but apparently it was fixed on June 27th: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522128](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522128)

---

### Post by Fibonacci on 2009-11-07
Apparently it had been reported on Launchpad too: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/410653](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/410653)

---

### Post by rockdj on 2009-11-22
> **Zoot7 said:**
> You've to do a bit more jumping through hoops this time sadly.

Here's a good guide I found earlier today about changing the splash image on Grub 2.
**[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html]("http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html")**

Thanks for the guide; my custom splash image works perfectly with those instructions.

---

### Post by Zoot7 on 2009-11-22
> **rockdj said:**
> Thanks for the guide; my custom splash image works perfectly with those instructions.
No problem! :)

---

### Post by hal8000 on 2009-11-22
I don't want to hijack this thread but are there any differences between grub1 and grub2 splash screen?
Can grub2 splash support higher video resolutions more colours than grub legacy?
The grub wiki  [http://grub.enbug.org/TodoList](http://grub.enbug.org/TodoList)
still lists a fancy menu with many eye candies as work in progress.

---

### Post by Zoot7 on 2009-11-22
> **hal8000 said:**
> I don't want to hijack this thread but are there any differences between grub1 and grub2 splash screen?
Can grub2 splash support higher video resolutions more colours than grub legacy?
The grub wiki  [http://grub.enbug.org/TodoList](http://grub.enbug.org/TodoList)
still lists a fancy menu with many eye candies as work in progress.
I'm not sure on resolutions but, apparently the theming support is vastly better. Of course it's still yet to mature yet, so there's no real example of it's "full power" out yet.

---

### Post by Fibonacci on 2009-11-22
> **hal8000 said:**
> I don't want to hijack this thread but are there any differences between grub1 and grub2 splash screen?
Can grub2 splash support higher video resolutions more colours than grub legacy?
The grub wiki  [http://grub.enbug.org/TodoList](http://grub.enbug.org/TodoList)
still lists a fancy menu with many eye candies as work in progress.

Apparently the difference is that the GRUB1 splash screen can actually display images.

---

### Post by lordskid on 2009-11-23
I followed the instructions and everything works fine for me. Here are things you might want to check...

1. check your /etc/default/grub if GRUB_TIMEOUT is 0... change it to GRUB_TIMEOUT="10"

or

2. check the image size in pixels.... resize it to a resolution that your screen can accomodate. (I believe the default is 640x480)

I am trying to compile an older grub2 version 1.96 that has gfxmenu installed. I have made some progress... check it out [click here]("http://karmic-koala.totalh.com/index.php?p=1_4_Grub2-1-96-with-gfxmenu")

---

### Post by Fibonacci on 2009-11-23
> **lordskid said:**
> I followed the instructions and everything works fine for me. Here are things you might want to check...

1. check your /etc/default/grub if GRUB_TIMEOUT is 0... change it to GRUB_TIMEOUT="10"

or

2. check the image size in pixels.... resize it to a resolution that your screen can accomodate. (I believe the default is 640x480)

I am trying to compile an older grub2 version 1.96 that has gfxmenu installed. I have made some progress... check it out [click here]("http://karmic-koala.totalh.com/index.php?p=1_4_Grub2-1-96-with-gfxmenu")

Already done both of those things. They make no difference at all.

---

### Post by anksush on 2010-03-19
I have detailed with screenshots blog entry for KUBUNTU here but in theory it should work for GNOME by replacing kdesudo with gksudo and dolphin to nautilus:

[http://makegadgetswork.blogspot.com/2010/03/kubuntu-blog-entry.html]("http://makegadgetswork.blogspot.com/2010/03/kubuntu-blog-entry.html")

6. How I managed to change the Log-in Screen (KDM Screen)

This one was rather flaky solution. I could not find anything that could change the initial background screen where we enter user credentials and password. This is called KDM Theme as I learnt while finding out how to do it. Several searches on google talked about something called KDM Theme Manager but they are all old mails and for new KDE 4+ it comes pre-installed and I did not know what to do. So I downloaded one of the KDM themes from [http://kde-look.org](http://kde-look.org) and unzipped it into the following location as root.

kdesudo dolphin /usr/share/kde4/apps/kdm/themes/

Next, I renamed the folder “oxygen-air” as “oxygen-air_old” and the downloaded and unzipped folder as “oxygen-air”.

This is it. When I restarted I had the brand new KDM Theme to my satisfaction.:)

7. Finally, This is how I changed my boot splash screen:

I tried many suggestions but only after going through the whole GRUB2 entries as explained on this link I got the result I was looking for. However, I did have to do a little bit of trial and error so I will put the steps that finally worked for me. These may also come handy if you do not want to know in depth about all GRUB 2 stuff.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

In GIMP, open the image you want to show as the background when GRUB shows choices to select which OS you want to load at start-up
Now goto Image -> Scale and then enter height as 640, press tab.
Now save the image as a .png file.
in the terminal type - kdesudo dolphin /usr/share/images/desktop-base
Copy the image saved in step 3 and paste it in the desktop-base folder


Now in the terminal type - kdesudo kate /etc/grub.d/05_debian_theme
This will open 05_debian_theme file with kate text editor.
Go to line 16 and find the following line and edit the highlighted area, replacing it with the name of image copied into desktop-base folder in Step 5
for i in {/boot/grub,/usr/share/images/desktop-base}/ moreblue-orbit-grub.{png,tga} ; do

Save the file and in the terminal type: sudo update-grub2
sudo reboot

This is it. Now once the system boots you should be able to see the image as background.

---

### Post by Fibonacci on 2010-03-19
> **anksush said:**
> I have detailed with screenshots blog entry for KUBUNTU here but in theory it should work for GNOME by replacing kdesudo with gksudo and dolphin to nautilus:

[http://makegadgetswork.blogspot.com/2010/03/kubuntu-blog-entry.html]("http://makegadgetswork.blogspot.com/2010/03/kubuntu-blog-entry.html")

6. How I managed to change the Log-in Screen (KDM Screen)

This one was rather flaky solution. I could not find anything that could change the initial background screen where we enter user credentials and password. This is called KDM Theme as I learnt while finding out how to do it. Several searches on google talked about something called KDM Theme Manager but they are all old mails and for new KDE 4+ it comes pre-installed and I did not know what to do. So I downloaded one of the KDM themes from [http://kde-look.org](http://kde-look.org) and unzipped it into the following location as root.

kdesudo dolphin /usr/share/kde4/apps/kdm/themes/

Next, I renamed the folder “oxygen-air” as “oxygen-air_old” and the downloaded and unzipped folder as “oxygen-air”.

This is it. When I restarted I had the brand new KDM Theme to my satisfaction.:)

7. Finally, This is how I changed my boot splash screen:

I tried many suggestions but only after going through the whole GRUB2 entries as explained on this link I got the result I was looking for. However, I did have to do a little bit of trial and error so I will put the steps that finally worked for me. These may also come handy if you do not want to know in depth about all GRUB 2 stuff.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

In GIMP, open the image you want to show as the background when GRUB shows choices to select which OS you want to load at start-up
Now goto Image -> Scale and then enter height as 640, press tab.
Now save the image as a .png file.
in the terminal type - kdesudo dolphin /usr/share/images/desktop-base
Copy the image saved in step 3 and paste it in the desktop-base folder


Now in the terminal type - kdesudo kate /etc/grub.d/05_debian_theme
This will open 05_debian_theme file with kate text editor.
Go to line 16 and find the following line and edit the highlighted area, replacing it with the name of image copied into desktop-base folder in Step 5
for i in {/boot/grub,/usr/share/images/desktop-base}/ moreblue-orbit-grub.{png,tga} ; do

Save the file and in the terminal type: sudo update-grub2
sudo reboot

This is it. Now once the system boots you should be able to see the image as background.

Didn't work. I'm still getting a completely black background on GRUB.

---

### Post by anksush on 2010-03-19
what version is ur GRUB...I remember reading that this will work on GRUB V1.9x beta4...

---

### Post by Fibonacci on 2010-03-19
> **anksush said:**
> what version is ur GRUB...I remember reading that this will work on GRUB V1.9x beta4...

1.97~beta4-1ubuntu3

---

### Post by anksush on 2010-03-20
I can't think of why it may not be working...if all steps are followed. Have you placed the image in desktop-base folder after creating the folder or was it already there...?

---

### Post by NHclimber on 2010-03-20
@Fibonacci

The error you received from the console generally indicates one of the following errors:

[LIST]
[*]the video module failed to load the vbe module
[*]there was a mode set error in the vbe module
[*]the vbe module was never set to load from the config file (/boot/grub/grub.cfg)
[/LIST]
To troubleshoot, go back to the console and do the following:
```
insmod vbeinfo
vbeinfo
```This should list a bunch of video mode specs in the form "mode #    mode description string".  Set a video mode you **know** should work, like 1024x768x32", with the following right in the console:
```
set gfxmode=1024x768x32
insmod vbe
rmmod gfxterm
```When you 'rmmod gfxterm', the display won't refresh with a prompt or your typing.  Type **slowly**:
```
insmod gfxterm
terminal_output gfxterm
```Confirm that this did mode set to 1024x768x32. Now,
```
background_image /usr/.....
```Did the mode set happen?  Did the background load?  If yes to both, then look over your /etc/grub.d/00_header file.  If no, respond here with what happened and your entire /boot/grub/grub.cfg and we'll investigate further.

Btw, did you upgrade to karmic or fresh install?  Also please confirm the title of the Grub2 version at the top of the menu page.

---

### Post by Keen_eye on 2010-03-28
I have the same problem as @Fibonacci.  No matter what I do I can only see the black and white version of Grub.

I'm running Karmic on an older Dell Inspiron notebook.  I've run every distro of Ubuntu starting with Dapper on it. Upgraded to Karmic (not a fresh install) then upgraded to Grub2. Top of Grub2 says, "1.97~beta 4"

The image is one of the standard images from the grub2-splashimages package. I have not modified it in any way. And Grub2 sees it during update-grub:

john@localhost:~$ sudo update-grub
[sudo] password for john: 
Generating grub.cfg ...
Found Debian background: Plasma-lamp.tga
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.27-11-generic
Found initrd image: /boot/initrd.img-2.6.27-11-generic
Found linux image: /boot/vmlinuz-2.6.24-23-generic
Found initrd image: /boot/initrd.img-2.6.24-23-generic
Found linux image: /boot/vmlinuz-2.6.22-14-generic
Found initrd image: /boot/initrd.img-2.6.22-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
john@localhost:~$ 


I did the full "set gfxmode=" routine as you described, NHclimber.  vbeinfo produced 9 different display resolutions: 1024x768, 800x600, and 640x480, each at 8, 16, and 32 bits.  I tried all of them at the Grub2 command line using your 5 step routine starting with "set gfxmode=" to "terminal_output gfxterm". Each time my output from "terminal_output gfxterm" was "error: No suitable mode found."

Here's the relevant sections of /boot/grub/grub.cfg:

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 87b0f595-a135-4af1-bbd6-4d5fae733048
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 87b0f595-a135-4af1-bbd6-4d5fae733048
insmod tga
if background_image /boot/grub/Plasma-lamp.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###
________________________________________________________________
Here's /etc/grub.d/05_debian_theme:
(Note: I moved the images into /boot/grub/ after trying them in their default installation directory - and making the necessary path entry - because that didn't work either.)

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
  for i in {/boot/grub,/usr/share/images/desktop-base}/Plasma-lamp.{png,tga} ; do
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
____________________________________________________________
And, for completeness, here's my /etc/default/grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

I tried unhashing GRUB_GFXMODE= and setting it to 1024x768 too.  It had no effect.

I'm at whits end and thinking this might be a hardware issue with my machine.  Any ideas would be appreciated.  Meantime I'll enjoy the black and white...

Thanks.

---

### Post by Fibonacci on 2010-03-30
> **Keen_eye said:**
> I have the same problem as @Fibonacci.  No matter what I do I can only see the black and white version of Grub.

I'm running Karmic on an older Dell Inspiron notebook.  I've run every distro of Ubuntu starting with Dapper on it. Upgraded to Karmic (not a fresh install) then upgraded to Grub2. Top of Grub2 says, "1.97~beta 4"

The image is one of the standard images from the grub2-splashimages package. I have not modified it in any way. And Grub2 sees it during update-grub:

john@localhost:~$ sudo update-grub
[sudo] password for john: 
Generating grub.cfg ...
Found Debian background: Plasma-lamp.tga
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.27-11-generic
Found initrd image: /boot/initrd.img-2.6.27-11-generic
Found linux image: /boot/vmlinuz-2.6.24-23-generic
Found initrd image: /boot/initrd.img-2.6.24-23-generic
Found linux image: /boot/vmlinuz-2.6.22-14-generic
Found initrd image: /boot/initrd.img-2.6.22-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
john@localhost:~$ 


I did the full "set gfxmode=" routine as you described, NHclimber.  vbeinfo produced 9 different display resolutions: 1024x768, 800x600, and 640x480, each at 8, 16, and 32 bits.  I tried all of them at the Grub2 command line using your 5 step routine starting with "set gfxmode=" to "terminal_output gfxterm". Each time my output from "terminal_output gfxterm" was "error: No suitable mode found."

Here's the relevant sections of /boot/grub/grub.cfg:

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 87b0f595-a135-4af1-bbd6-4d5fae733048
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 87b0f595-a135-4af1-bbd6-4d5fae733048
insmod tga
if background_image /boot/grub/Plasma-lamp.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###
________________________________________________________________
Here's /etc/grub.d/05_debian_theme:
(Note: I moved the images into /boot/grub/ after trying them in their default installation directory - and making the necessary path entry - because that didn't work either.)

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
  for i in {/boot/grub,/usr/share/images/desktop-base}/Plasma-lamp.{png,tga} ; do
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
____________________________________________________________
And, for completeness, here's my /etc/default/grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

I tried unhashing GRUB_GFXMODE= and setting it to 1024x768 too.  It had no effect.

I'm at whits end and thinking this might be a hardware issue with my machine.  Any ideas would be appreciated.  Meantime I'll enjoy the black and white...

Thanks.

I'm seeing exactly the same results.

---

