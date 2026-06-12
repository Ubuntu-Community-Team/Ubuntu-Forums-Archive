---
title: "Cannot change font colours in GRUB (Ubuntu 11.04)"
date: 2011-05-23
forum: General Help
---

### Post by silkworm2.5 on 2011-05-23
Hello!

I'm trying to change the colour of my GRUB screens font to be black and transparent. This is because I have a wallpaper for it which I dont want the text to overlay.

The problem is, then when I change the font colours, it wont accept the changes. I have tried using the Grub Customizer tool, and manually modifying /boot/grub/grub.cfg.
After running sudo update-grub the changes will simply disappear. Gedit tells me the file has been externally altered and asks to reload it.

Here's the code I am modifying:

What I want it to be
```
if background_image /boot/grub/Splash.jpg; then
  true
else
  set menu_color_normal=black/black
  set menu_color_highlight=black/black
```What it ends up as
```
if background_image /boot/grub/Splash.jpg; then
  true
else
  set menu_color_normal=_white_/black
  set menu_color_highlight=black/_light-gray_
```Can anyone help me please?

EDIT: Image removed as per Moderators request :)

Thanks in advance!

---

### Post by silkworm2.5 on 2011-05-29
bump

---

### Post by linuxinstalledfromhdd on 2011-05-29
Did you try grub customizer?

---

### Post by silkworm2.5 on 2011-05-29
Just tried it now. No change in the font colours, but it did manage to change the names of the items it shows (shortened Ubuntu with linux x.x.x.x to Ubuntu 11.04) The customizer reports that the font should be black on black, but grub doesn't display it that way.

Also, When I boot Ubuntu it gives me a message "error: environment block too small" I don't know if this is related or not.

---

### Post by linuxinstalledfromhdd on 2011-05-29
I think you need to have the wallpaper enabled or something in Grub Customizer first before you can have colored fonts enabled at the same time. I know, that's strange, but that's how it worked for me the last time.

---

### Post by silkworm2.5 on 2011-05-29
It is activated in grub customizer. I copied it manually to the /boot/grub directory, and pointed grub customizer to it. It shows the thumbnail for it in the appearance tab.

Although after some googling I found [this]("https://help.ubuntu.com/community/Grub2#Set menu font and highlight colors"):

> If a background image is in use:
Locate the "else" clause following "if test -e ${f}; then" and edit the following entry to the path of the desired image already selected in the GRUB_BACKGROUND option.

WALLPAPER=/usr/share/images/desktop-base/moreblue-orbit-grub.png
Failure to do so would indeed allow the selected background in the GRUB_BACKGROUND option to be displayed when Grub2 loads, but not the color changes (see below) from taking effect on account of the conflict.

Unfortunately I don't understand it. And I couldn't find a mention of "if test -e ${f}; then" in either /boot/grub/grub.config or /etc/grub.d/debian_theme
](*,)

---

### Post by linuxinstalledfromhdd on 2011-05-29
I don't get it either. But I was able to make it work, so it is possible through that application.  It was mostly trial and error for me.

---

### Post by silkworm2.5 on 2011-05-29
Hmm, it says in your profile you are on Ubuntu 10.10? I remember reading somewhere that 10.10 and 11.04 have different versions of GRUB bundled.
But I'll keep trying like you said anyway. Thanks ;)

---

### Post by linuxinstalledfromhdd on 2011-05-29
They both use the same application version of Grub Customizer though. That's the only thing I used to do this.

---

### Post by silkworm2.5 on 2011-05-29
They use the same version of Grub Customizer, but if Grub 1.99 and 1.98 have separate methods for changing font colours, then the application simply wont do the job right because its changing the wrong thing.

I'm pretty sure the Customizer changed the settings in /boot/grub.cfg to alter font colours. I changed the colours there manually, and ran sudo update-grub. Gedit reported the file had been altered on disk, so I reloaded, and it had been changed back to the default colours.

I might actually downgrade to Ubuntu 10.10 after this... I like unity, but the resources, bugs and fixes needed after installation are a bit overwhelming.

---

### Post by linuxinstalledfromhdd on 2011-05-29
I love Ubuntu. I don't like having to always upgrade to the latest buggest version available like everyone else here. I'm not a developer, and I've got a life..  Just kidding. ;)

---

### Post by silkworm2.5 on 2011-05-29
XD I love Ubuntu too. I also like how it's not overly simplified, and how when you fix a problem you get some sense of achievement, even if it's only from copying someone's online guide.
I wish it were the same for windows. When I fix a problem in Windows, I usually just think "why does it do that? that's just dumb" I feel like I know Ubuntu better, even though I have only used it a couple of years now. 

Heh, I'm just rambling now :P I'll give 10.10 a go on my USB HDD and see if I can fix the wireless problem I had, and see if the intel graphics drivers PPA is stable with it. If it does, maybe I'll set up AWN to resemble Unity XD

Thanks for your help dude! :)

---

### Post by drs305 on 2011-05-29
First, I appreciate the warning about the image contents, but please remove the thumbnail before someone reports the post...  Thank you.

Taking off the moderator hat... I am not sure why Grub isn't letting you do what you want, but it may be good that it isn't. Unless I'm missing something, you would end up with black text on a black background - i.e. you wouldn't see any entries.

Although I've done this on occasion just to mess about, you probably have something else in mind.

I wrote a guide recently about Grub 1.99 drop in backgrounds and expanded it quite a bit to include fonts. Perhaps that will provide some answers.
[Grub 2 Drop-In Backgrounds & Font Selection]("http://ubuntuforums.org/showthread.php?t=1739412")


In the meantime, I'll re-read this thread and see if I can come up with something.

**[COLOR="DarkRed"]ADDED:[/COLOR]** In the first post, you say you tried manually editing grub.cfg and then ran update-grub. Doing so will remove any changes you have made to grub.cfg. To make the changes permanent with a manual edit, you would edit the /etc/grub.d/05_debian_theme file.

---

### Post by silkworm2.5 on 2011-05-29
Hi Drs.
I removed the image as you asked. I'll keep in mind to keep that kind of thing completely off the forum.
And yes I was after invisible text. I wanted it so that if someone else accessed my laptop, all they would get is the message in the image. I would know that Ubuntu was the first entry in the list, and that Windows was third, so I would have no troubles.

I'll give what you mentioned about /etc/grub.d/debian_theme another go, but I think last time I altered it, the changes appeared in grub.cfg but still didn't appear in the bootloader.
Still, I'll try it again. Thanks for the advice. :)

---

### Post by drs305 on 2011-05-29
> **silkworm2.5 said:**
> Hi Drs.
I removed the image as you asked. I'll keep in mind to keep that kind of thing completely off the forum.
And yes I was after invisible text. I wanted it so that if someone else accessed my laptop, all they would get is the message in the image. I would know that Ubuntu was the first entry in the list, and that Windows was third, so I would have no troubles.

I'll give what you mentioned about /etc/grub.d/debian_theme another go, but I think last time I altered it, the changes appeared in grub.cfg but still didn't appear in the bootloader.
Still, I'll try it again. Thanks for the advice. :)

I just tried the black/black setting at the grub prompt and it accepted it, so it should accept it in the menu as well (I would suspect). I keep the rescue mode invisible on my setup, but I do it by just leaving the name entry a single 'space'.

If you run into problems and it still won't keep it when you make the change in 05... post back and I'll play with it some more. 

And thanks for the other matter.  ;-)

---

### Post by silkworm2.5 on 2011-05-29
Ok, I tried modifying 05_debian_theme, and the changes appeared in grub.cfg, but they weren't actually used in the GRUB screen. Even though I ran sudo update-grub. any other ideas? I'm stuck. :confused:

---

### Post by drs305 on 2011-05-29
> **silkworm2.5 said:**
> Ok, I tried modifying 05_debian_theme, and the changes appeared in grub.cfg, but they weren't actually used in the GRUB screen. Even though I ran sudo update-grub. any other ideas? I'm stuck. :confused:

If you will post your grub.cfg contents perhaps I can figure out what is happening. What exactly did you see on the grub menu, and what did you want to see?

---

### Post by silkworm2.5 on 2011-05-29
At the grub Menu I see the standard GRUB layout (version at the top, list in a box) with unselected text in grey, and selected text black, with the selection bar in grey.
3 Entries in the boot list; Ubuntu 11.04. Ubuntu 11.04 (Recovery Mode), and Windows 7.
The wallpaper works just fine.
The screen resolution automatically set itself to use the dimension 1366x768 which is the default for my monitor.

This _is_ what I wanted to see, except for the font colour.

Here is the contents of my Grub.cfg:

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 8c4c051f-a077-4439-9c8c-383c2b5ce6d4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 8c4c051f-a077-4439-9c8c-383c2b5ce6d4
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 8c4c051f-a077-4439-9c8c-383c2b5ce6d4
insmod jpeg
if background_image /boot/grub/splash.jpg; then
  true
else
  set menu_color_normal=black/black
  set menu_color_highlight=black/black
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu 11.04" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c4c051f-a077-4439-9c8c-383c2b5ce6d4
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=8c4c051f-a077-4439-9c8c-383c2b5ce6d4 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry "Ubuntu 11.04 (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 8c4c051f-a077-4439-9c8c-383c2b5ce6d4
	echo	'Loading Linux 2.6.38-9-generic ...'
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=8c4c051f-a077-4439-9c8c-383c2b5ce6d4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root FACE9B0BCE9ABF77
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

---

### Post by drs305 on 2011-05-29
Here is the defining section of grub.cfg:
> 
if background_image /boot/grub/splash.jpg; [B][COLOR="DarkRed"]then
  true
else[/COLOR][/B]
  set menu_color_normal=black/black
  set menu_color_highlight=black/black
  if background_color 44,0,30; then
    clear
  fi
fi


I'll assume splash.jpg is the image you want. What the section says is only to use your color theme *if* it doesn't use the splash.jpg image.

I believe the dev's rationale was that if you are picking an image, they don't know what the background color is going to be so they wanted to be sure the user would see the menu items. Actually, I believe they included this rationale in the script itself.

So they are protecting you from yourself. Fortunately, they also let you change it if you want, although it takes a bit of tinkering.

In Natty, open 05_debian_theme for editing:
```
gksu gedit +98 /etc/grub.d/05_debian_theme
```

> 	echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
	if [ -n "${2}" ]; then
		echo "  set color_normal=${2}"
	fi

Add your two lines, save the file, and update grub.
> echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
[B][COLOR="DarkRed"]echo " set color_normal=black/black"
echo " set color_highlight=black/black"[/COLOR][/B]
if [ -n "${2}" ]; then 

grub.cfg should now look something like:
> 
if background_image /boot/grub/splash.jpg; then
  set menu_color_normal=black/black
  set menu_color_highlight=black/black 
else
  set menu_color_normal=black/black
  set menu_color_highlight=black/black
  if background_color 44,0,30; then
    clear
  fi
fi


---

### Post by silkworm2.5 on 2011-05-29
That solved my problem! Thanks Drs!

---

### Post by HTDx64 on 2011-06-21
Maybe it solved the problem, but in an ugly way.
Here's solution if /etc/grub.d/05_debian_theme works with image, but not with the colors:

```

sudo gedit /etc/grub.d/05_debian_theme

```

Find:
```

	if [ -n "${2}" ]; then
		echo "  set color_normal=${2}"
	fi
	if [ -n "${3}" ]; then
		echo "  set color_highlight=${3}"
	fi
	if [ -z "${2}" ] && [ -z "${3}" ]; then
		echo "  true"
	fi

```
(lines 95-103 in my version)

and change them to:
```

	if [ -n "${GRUB_COLOR_NORMAL}" ]; then
		echo "  set color_normal=${GRUB_COLOR_NORMAL}"
	fi
	if [ -n "${GRUB_COLOR_HIGHLIGHT}" ]; then
		echo "  set color_highlight=${GRUB_COLOR_HIGHLIGHT}"
	fi
	if [ -z "${GRUB_COLOR_NORMAL}" ] && [ -z "${GRUB_COLOR_HIGHLIGHT}" ]; then
		echo "  true"
	fi

```

Use grub-customizer again and save the changes. From now on the changes to colors will be applied.

It works even in LMDE sid-hacked, however 06_mint_theme must be moved before using grub-customizer.

---

### Post by noahdiehl on 2011-09-10
Same issue, your fix did the trick for me (thank you!)... more color options would be nice, I am using the purple and orange Narwhal background and wanted to use the same orange for the text... but light red is close enough.

---

### Post by csc451 on 2011-09-29
I finally figured this out without having to make any changes to GRUB2 update scripts, by using desktop-base (which is a set of files, images and such, used to theme debian).

Desktop-base was already installed in my 11.04. [Click here to see to install desktop-base]("http://joysofprogramming.com/install-desktop-base-ubuntu/")

Grub2 will load */usr/share/desktop-base/grub_background.sh* which contains the wallpaper and color settings.  

Here is the default version of */usr/share/desktop-base/grub_background.sh*
```

WALLPAPER=/usr/share/images/desktop-base/desktop-grub.png 
COLOR_NORMAL=light-gray/black 
COLOR_HIGHLIGHT=white/black 
 
```
[LIST=1]
[*]Copy the background image you want to use to */usr/share/images/desktop-base* (or just change the path of WALLPAPER to your image)
[*]Edit */usr/share/desktop-base/grub_background.sh*
[*]*Change WALLPAPER, COLOR_NORMAL and COlOR_HIGHLIGHT the way you want*
[*][I]update-grub2
You will notice that update-grub2 will show it found an image file [/I]*.background_cache.jpeg. T*his is where it put the image from WALLPAPER in /boot/grub directory.
[/LIST]
When you reboot and the grub menu is displayed the background and colors will be set.

Note: if you have GRUB_BACKGROUND defined or and of the following image files in the /boot/grub directory (*.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA). The desktop-base will not be loaded.

---

