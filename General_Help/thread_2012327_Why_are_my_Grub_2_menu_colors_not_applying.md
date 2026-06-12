---
title: "Why are my Grub 2 menu colors not applying"
date: 2012-06-28
forum: General Help
---

### Post by josephellengar on 2012-06-28
Hi. I'm trying to change grub 2 menu settings and it's just not working for some reason. I am changing the 05_debian_theme file in the /etc/grub.d file. I am updating grub every time I make a change and I have also tested my changes within the grub command prompt (by pressing "c" at grub load) and they work there.

The problem is that I have white text on a light background and my highlight is black/white, which makes it very difficult to see. I am trying to change color_normal to black/black and menu_color_highlight to blue/black.

This is my 05_debian_theme file:

```

#!/bin/sh
set -e

. /usr/lib/grub/grub-mkconfig_lib

# We want to work in /boot/grub/ only.
test -d "${GRUB_PREFIX}"; cd "${GRUB_PREFIX}"

# Set the location of a possibly necessary cache file for the background image.
# NOTE: This MUST BE A DOTFILE to avoid confusing it with user-defined images.
BACKGROUND_CACHE=".background_cache"

set_default_theme(){
	# Set a monochromatic theme for Ubuntu.
	echo "${1}set color_normal=black/black"
	echo "${1}set menu_color_normal=black/black"
	echo "${1}set menu_color_highlight=blue/black"

	if [ -e /lib/plymouth/themes/default.grub ]; then
		sed "s/^/${1}/" /lib/plymouth/themes/default.grub
	fi
}

set_background_image(){
	# Step #1: Search all available output modes ...
	local output
	for output in ${GRUB_TERMINAL_OUTPUT}; do
		if [ "x$output" = "xgfxterm" ]; then
			break
		fi
	done

	# ... and check if we are able to display a background image at all.
	if ! [ "x${output}" = "xgfxterm" ]; then
		return 1
	fi

	# Step #2: Check if the specified background image exists.
	if ! [ -f "${1}" ]; then
		return 2
	fi

	# Step #3: Search the correct GRUB module for our background image.
	local reader
	case "${1}" in
		*.jpg|*.JPG|*.jpeg|*.JPEG) reader="jpeg";;
		*.png|*.PNG) reader="png";;
		*.tga|*.TGA) reader="tga";;
		*) return 3;; # Unknown image type.
	esac

	# Step #4: Check if the necessary GRUB module is available.
	if ! [ -f "${reader}.mod" ]; then
		return 4
	fi

	# Step #5: Check if GRUB can read the background image directly.
	# If so, we can remove the cache file (if any). Otherwise the backgound
	# image needs to be cached under /boot/grub/.
	if is_path_readable_by_grub "${1}"; then
		rm --force "${BACKGROUND_CACHE}.jpeg" \
			"${BACKGROUND_CACHE}.png" "${BACKGROUND_CACHE}.tga"
	elif cp "${1}" "${BACKGROUND_CACHE}.${reader}"; then
		set -- "${BACKGROUND_CACHE}.${reader}" "${2}" "${3}"
	else
		return 5
	fi

	# Step #6: Prepare GRUB to read the background image.
	if ! prepare_grub_to_access_device "`${grub_probe} --target=device "${1}"`"; then
		return 6
	fi

	# Step #7: Everything went fine, print out a message to stderr ...
	echo "Found background image: ${1}" >&2

	# ... and write our configuration snippet to stdout. Use the colors
	# desktop-base specified. If we're using a user-defined background, use
	# the default colors since we've got no idea how the image looks like.
	# If loading the background image fails, use the default theme.
	echo "insmod ${reader}"
	echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
	if [ -n "${2}" ]; then
		echo "  set color_normal=black/black"
	fi
	if [ -n "${3}" ]; then
		echo "  set color_highlight=blue/black"
	fi
	if [ -z "${2}" ] && [ -z "${3}" ]; then
		echo "  true"
	fi
	echo "else"
	set_default_theme "  "
	echo "fi"
}

# Earlier versions of grub-pc copied the default background image to /boot/grub
# during postinst. Remove those obsolete images if they haven't been touched by
# the user. They are still available under /usr/share/images/desktop-base/ if
# desktop-base is installed.
while read checksum background; do
	if [ -f "${background}" ] && [ "x`sha1sum "${background}"`" = "x${checksum}  ${background}" ]; then
		echo "Removing old background image: ${background}" >&2
		rm "${background}"
	fi
done <<EOF
648ee65dd0c157a69b019a5372cbcfea4fc754a5  debian-blueish-wallpaper-640x480.png
0431e97a6c661084c59676c4baeeb8c2f602edb8  debian-blueish-wallpaper-640x480.png
968ecf6696c5638cfe80e8e70aba239526270864  debian-blueish-wallpaper-640x480.tga
11143e8c92a073401de0b0fd42d0c052af4ccd9b  moreblue-orbit-grub.png
d00d5e505ab63f2d53fa880bfac447e2d3bb197c  moreblue-orbit-grub.png
f5b12c1009ec0a3b029185f6b66cd0d7e5611019  moreblue-orbit-grub.png
EOF

# Include the configuration of desktop-base if available.
if [ -f "/usr/share/desktop-base/grub_background.sh" ]; then
	. "/usr/share/desktop-base/grub_background.sh"
fi

# First check whether the user has specified a background image explicitly.
# If so, try to use it. Don't try the other possibilities in that case
# (#608263).
if [ -n "${GRUB_BACKGROUND+x}" ]; then
	set_background_image "${GRUB_BACKGROUND}" || set_default_theme
	exit 0
fi

# Next search for pictures the user put into /boot/grub/ and use the first one.
for background in *.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga *.TGA; do
	if set_background_image "${background}"; then
		exit 0
	fi
done

# Next try to use the background image and colors specified by desktop-base.
if set_background_image "${WALLPAPER}" "${COLOR_NORMAL}" "${COLOR_HIGHLIGHT}"; then
	exit 0
fi

# If we haven't found a background image yet, use the default from desktop-base.
if set_background_image "/usr/share/images/grub/linux-windows.png"; then
	exit 0
fi

# Finally, if all of the above fails, use the default theme.
set_default_theme

```

---

### Post by josephellengar on 2012-06-29
bump

---

### Post by josephellengar on 2012-06-30
bump

---

### Post by bogan on 2012-06-30
Hi!, **Josephellengar,**

I cannot tell you why your choice of Grub menu colors is not working, but can suggest you try Grub Customizer, which will do it for you, and a lot else, much easier than editing the files yourself.
[http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub+customizer&page=29](http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub+customizer&page=29)

Chao!, **bogan.**

---

### Post by josephellengar on 2012-06-30
> **bogan said:**
> Hi!, **Josephellengar,**

I cannot tell you why your choice of Grub menu colors is not working, but can suggest you try Grub Customizer, which will do it for you, and a lot else, much easier than editing the files yourself.
[http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub+customizer&page=29](http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub+customizer&page=29)

Chao!, **bogan.**

Broke my grub.

---

### Post by drs305 on 2012-06-30
I haven't gone through every line of your file, but one thing to keep in mind is that with */black, the black is not a color but a code meaning "transparent". The background will be whatever your background image or color is.

There is a hierarchy of where GRUB draws it's colors from, and they may not be coming from the default theme.

Here is a guide I wrote about backgrounds and colors which might shed some light on your problem.

[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by josephellengar on 2012-06-30
> **drs305 said:**
> I haven't gone through every line of your file, but one thing to keep in mind is that with */black, the black is not a color but a code meaning "transparent". The background will be whatever your background image or color is.

There is a hierarchy of where GRUB draws it's colors from, and they may not be coming from the default theme.

Here is a guide I wrote about backgrounds and colors which might shed some light on your problem.

[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

Actually, I had been using your guide. It's very well written. What I want is all of the text to be black by default, except for when it is highlighted, and then it is blue, with no background. So I have this:

	echo "${1}set color_normal=black/black"
	echo "${1}set menu_color_normal=black/black"
	echo "${1}set menu_color_highlight=blue/black"

But for some reason, everything is white/black, with a black/white highlight.

---

### Post by drs305 on 2012-06-30
> **josephellengar said:**
> Actually, I had been using your guide. It's very well written. What I want is all of the text to be black by default, except for when it is highlighted, and then it is blue, with no background. So I have this:

	echo "${1}set color_normal=black/black"
	echo "${1}set menu_color_normal=black/black"
	echo "${1}set menu_color_highlight=blue/black"

But for some reason, everything is white/black, with a black/white highlight.

OK, I'll go through your file and see if I can pick out anything.

Which Grub version are you using?  (grub-install -v)  
What color is your background (purple, etc?)

EDIT - Added.
In the past when I wanted a black background I found the easiest thing to do was just create a black jpg or png file and stick it in /boot/grub. Then */black gave me the black background as long as the image was used by Grub as the background image. Of course in this case you wouldn't want the color_normal to be black, unless you don't want to see it unless it's highlighted.

If you use an all-black background image I'm pretty sure Grub is going to use the default settings, so you should just be able to set the colors in the default theme section and they should work as long as they are compatible with a 'true' black background.

Also, the default Pangolin Grub background is usually dark purple. Do you have a background image already in /boot/grub or one designated in /etc/default/grub?

---

### Post by josephellengar on 2012-06-30
> **drs305 said:**
> OK, I'll go through your file and see if I can pick out anything.

Which Grub version are you using?  (grub-install -v)  
What color is your background (purple, etc?)

EDIT - Added.
In the past when I wanted a black background I found the easiest thing to do was just create a black jpg or png file and stick it in /boot/grub. Then */black gave me the black background as long as the image was used by Grub as the background image. Of course in this case you wouldn't want the color_normal to be black, unless you don't want to see it unless it's highlighted.

If you use an all-black background image I'm pretty sure Grub is going to use the default settings, so you should just be able to set the colors in the default theme section and they should work as long as they are compatible with a 'true' black background.

Also, the default Pangolin Grub background is usually dark purple. Do you have a background image already in /boot/grub or one designated in /etc/default/grub?

I have an image in /usr/share/images/grub. I attached it to this message. It shows up, so I know the reference to it in the 05_debian_theme file is correct. (You can see from the image why getting white text is irritating)

---

### Post by drs305 on 2012-06-30
[COLOR="DarkRed"]Edit: See next post.[/COLOR]

I'll investigate this further tomorrow, but my initial observations.

What you current describe sounds like it matches the default 05_debian_theme standards for the default theme:


> set_default_theme(){
	# Set a monochromatic theme for Ubuntu.
	echo "${1}set menu_color_normal=white/black"
	echo "${1}set menu_color_highlight=black/light-gray"

[COLOR="DarkRed"]Edit. After testing, I see that is what the system is using.
[/COLOR]
Here is what my /boot/grub/grub.cfg file looks like with your image and desired colors [COLOR="DarkRed"](and I get the same result as you do)[/COLOR]:
> 
### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set=root dbd69ed2-530c-4409-8f5a-a3f1ea41fc60
insmod png
if background_image /boot/grub/linux-windows.png; then
  true
else
  set menu_color_normal=black/black
  set menu_color_highlight=blue/black
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

I'm going to reboot and edit this based on what I see. [COLOR="DarkRed"]See next post for findings.[/COLOR]

---

### Post by drs305 on 2012-06-30
I had the same results as you did.

I was supposed to log off about half an hour ago, so I'll give you the condensed version now and will come back tomorrow when I have time to see why they apparently have changed the logic somewhat.

The short story, copy the two lines in red which initially followed **else** above that line, save the file and you will get the expected result. I'd leave leave the same lines below the **else** line - they won't affect what you are trying to do.

```
### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set=root dbd69ed2-530c-4409-8f5a-a3f1ea41fc60
insmod png
if background_image /boot/grub/linux-windows.png; then
true
[COLOR="Red"]set menu_color_normal=black/black
set menu_color_highlight=blue/black[/COLOR]
else
set menu_color_normal=black/black
set menu_color_highlight=blue/black
if background_color 44,0,30; then
clear
fi
fi
### END /etc/grub.d/05_debian_theme ### 
```

---

### Post by josephellengar on 2012-06-30
> **drs305 said:**
> I had the same results as you did.

I was supposed to log off about half an hour ago, so I'll give you the condensed version now and will come back tomorrow when I have time to see why they apparently have changed the logic somewhat.

The short story, copy the two lines in red which initially followed **else** above that line, save the file and you will get the expected result. I'd leave leave the same lines below the **else** line - they won't affect what you are trying to do.


Thank you very much for the help!

I'm not sure that working with entirely the same file. I only have two "else"s in my file:

```

	if is_path_readable_by_grub "${1}"; then
		rm --force "${BACKGROUND_CACHE}.jpeg" \
			"${BACKGROUND_CACHE}.png" "${BACKGROUND_CACHE}.tga"
	elif cp "${1}" "${BACKGROUND_CACHE}.${reader}"; then
		set -- "${BACKGROUND_CACHE}.${reader}" "${2}" "${3}"
	**else**
		return 5
	fi

	# Step #6: Prepare GRUB to read the background image.
	if ! prepare_grub_to_access_device "`${grub_probe} --target=device "${1}"`"; then
		return 6
	fi

```

and

```

	if [ -n "${2}" ]; then
		echo "  set color_normal=black/black"
	fi
	if [ -n "${3}" ]; then
		echo "  set color_highlight=blue/black"
	fi
	if [ -z "${2}" ] && [ -z "${3}" ]; then
		echo "  true"
	fi
	**echo "else"**
	set_default_theme "  "
	echo "fi"
}

```

Neither one of these has those two lines that you mentioned nearby.

---

### Post by drs305 on 2012-07-01
Sorry for the confusion. I my third post I identified the text as coming from the grub.cfg file. Although I copied the same into in my last post I didn't repeat that it was from the /boot/grub/grub.cfg file and not the 05 file. 

I was providing the 'quick' fix of editing grub.cfg directly until I could spend more time determining how the 05_debian_theme file or grub-mkconfig command had changed.

If you added those 2 lines to your grub.cfg file, save it and DO NOT run update-grub I think you will get the effect you desire.

I'll provide the way to edit the 05 file to make it permanent in my next post.

---

### Post by drs305 on 2012-07-01
In /etc/grub.d/05_debian_theme, add the following lines (around line 105):

> 
	if [ -z "${2}" ] && [ -z "${3}" ]; then
[COLOR="DarkRed"]
		echo " set color_normal=black/black"
		echo " set menu_color_normal=black/black"
		echo " set menu_color_highlight=blue/black"[/COLOR]
		echo "  true"
	fi
	echo "else"
	set_default_theme "  "


Save the file and update-grub.

---

### Post by josephellengar on 2012-07-01
> **drs305 said:**
> In /etc/grub.d/05_debian_theme, add the following lines (around line 105):

Save the file and update-grub.

Thank you! It works! I can finally read my grub menu!

---

