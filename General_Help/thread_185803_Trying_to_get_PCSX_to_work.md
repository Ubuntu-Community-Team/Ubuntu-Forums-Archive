---
title: "Trying to get PCSX to work"
date: 2006-06-01
forum: General Help
---

### Post by Stex on 2006-06-01
I got the error that lndir is not a command. I've looked around for how to get lndir but am quite stumped as to where my "xc" directory is. Any pointers? I guess it's not that neccisary but missing a function seems wrong to me.

---

### Post by InsaneBeast on 2006-06-04
[QUOTE=Stex]I got the error that lndir is not a command. I've looked around for how to get lndir but am quite stumped as to where my "xc" directory is. Any pointers? I guess it's not that neccisary but missing a function seems wrong to me.[/QUOTE]


Hi Stex, You may be able to fix the problem like I did.  Open /usr/games/pcsx with a text editor, and then replace the text with the following (of course, you'll probably want to make a backup copy of the file first):

```
#!/bin/bash

# Mostly (C) fbriere.net
# Some parts (C) 2005 Ryan Schultz

# PCSX expects to be installed in the user's home directory, so we build
# a nice little doghouse under ~/.pcsx for it to live in.
#
# This script will populate ~/.pcsx with symlinks to the plugins
# installed on the machine.  You can add other files in there, but do not
# meddle with the symlinks; if you replace a symlink with a file, it will
# eventually get overwritten.  See README.Debian for more details.

set -e

# Store keyboard repeat settings that PCSX may break
# will equal 'on' or 'off'
REPEAT=`xset q | grep 'auto repeat' | head -n 1 | awk '{print $3}'`

# Create the doghouse
mkdir --parents ~/.pcsx
cd ~/.pcsx
mkdir --parents Bios Langs cfg memcards Plugin sstates .pixmaps

# Flush dangling symlinks
find Bios Plugin cfg .pixmaps -type l -exec test ! -r '{}' \; \
	-exec echo Deleting '{}' \; \
	-exec rm -f '{}' \;

# Populate the doghouse
ln -s -f -t Plugin/ /usr/lib/games/psemu/lib/*
ln -s -f -t cfg/ /usr/lib/games/psemu/config/*

#lndir -silent /usr/lib/games/psemu/lib		Plugin
#lndir -silent /usr/lib/games/psemu/config	cfg

# Add any local plugins
[ -d /usr/local/share/games/psx-bios ] && \
	ln -s -f -t Bios/ /usr/local/share/games/psc-bios/*
[ -d /usr/local/lib/games/psemu/lib ] && \
	ln -s -f -t Plugin/ /usr/local/lib/games/psemu/lib/* 
[ -d /usr/local/lib/games/psemu-plugins/config ] && \
	ln -s -f -t cfg/ /usr/local/lib/games/psemu/config/*

#[ -d /usr/local/share/games/psx-bios ] && \
#	lndir -silent /usr/local/share/games/psx-bios		Bios
#[ -d /usr/local/lib/games/psemu/lib ] && \
#	lndir -silent /usr/local/lib/games/psemu/lib	Plugin
#[ -d /usr/local/lib/games/psemu-plugins/config ] && \
#	lndir -silent /usr/local/lib/games/psemu/config	cfg

# Copy the pixmaps in the About dialog
ln -s -f -t .pixmaps/ /usr/share/games/pcsx/pixmaps/*
#lndir -silent /usr/share/games/pcsx/pixmaps	.pixmaps

# Copy the languages for the Language menu
ln -s -f -t Langs/ /usr/share/games/pcsx/langs/*
#lndir -silent /usr/share/games/pcsx/langs	Langs

# Now we're ready to launch PCSX
/usr/games/pcsx.real "$@"

# Restore keyboard repeat settings
if [[ "$REPEAT"=="on" ]]; then
	xset r on
else
	xset r off
fi


```

I hope that helps.  Good luck.

---

### Post by mbm1980 on 2006-06-07
I had this problem too and your solution worked out great.
Thanks alot! =D>

---

### Post by Sheco on 2006-06-07
Now, how can I configure pcsx to use a keyboard, the two controller plugins only let me configure a joystick, omnijoy says you can use a keyboard, but when I mark the checkbox, it tells me to reconfigure, I save and open the dialog again, but I still cant choose keyboard keys for the buttons :-k

---

### Post by InsaneBeast on 2006-06-08
Hi Scheco, you may have some luck by changing the input Device file to "/dev/input/ts0" and the Emulation to "PCSX".. I've atttached a screenshot of my configuration settings.

---

### Post by squinter on 2006-07-29
Hi, this thread solved a lot of my problem! but still have a problem. I have created a bin/cue files for this game that I have (Harvest Moon back to nature), but it won't load, and no error.

I got the sc001 ps bios thing (it works in my winXP machine), and I think its working because I can see the PS opening splash.

This is what the console text looks like:

> (<unknown>:30705): Gtk-WARNING **: Locale not supported by C library. Using the fallback 'C' locale.
padJoy: pad already initialised

Then the program just hung like that. (I have disabled multithreading for the pad).

Anyidea?

---

### Post by rastilin on 2006-09-05
I should thank you as well, I had the same problem and your /usr/games/pcsx solved it perfectly.

---

### Post by JustAboutRealJAR on 2007-11-21
> **squinter said:**
> Hi, this thread solved a lot of my problem! but still have a problem. I have created a bin/cue files for this game that I have (Harvest Moon back to nature), but it won't load, and no error.

I got the sc001 ps bios thing (it works in my winXP machine), and I think its working because I can see the PS opening splash.

Anyidea?

you have to manually edit the config file:
```
$ gedit ~/.pcsx/pcsx.cfg
```

and change the first line from 'Bios = HLE' to 'Bios = (insert name of your Bios File)'

also make sure the BiosDir is set to the proper directory (the one where your bios file is)

---

