---
title: "Gkrellm Background Changer"
date: 2009-09-08
forum: General Help
---

### Post by Mark76 on 2009-09-08
Can anyone tell me why I can't set the path to my wallpapers?

> GKrellMBgChg is a GKrellM plugin which periodically changes
your desktop background. It also allows you to monitor the time
between the updates in various ways. It is possible, to force a
change by clicking on the panel.

Configuration:

- Format String
	The text output format is controlled by this string (default: $s).
	$s are the seconds that are remaining to the next update
	$S are the seconds that passed since the last change
	$m are the minutes that are remaining to the next update
	$M are the minutes that passed since the last change
	$t is the time remaining to the next update, displayed as '-mm:ss'
	$T is the time that passed since the last change, displayed as 'mm:ss'.

- Background Change Command
	Program to use to set the desktop background image (including args).
	If the command has exactly one '%s' it will be replaced by the
	properly quoted background file name.
	Common cases are:
	for plain X11: xsetbg -fullscreen
	using Eterm's Esetroot: Esetroot -f
	for Gnome2 set it to:
		gconftool-2 --type=string --set /desktop/gnome/background/picture_filename
	and for KDE 3.x:
		dcop kdesktop KBackgroundIface setWallpaper %s 6
	default: Esetroot -f

- Parse Background Change Command output
	Whether to parse output of Background Change Command. This allows
	setting such information as tooltip and timeout from the command.
	See README: Tips and Tricks for info about output format
	and some ideas. This option is experimental.
	default: off

- Image Database
	Full path to a file containing all the images (full path/line) to be
	used by the plugin. (e.g. the output from: find / -name *.jpg | sort)
	Entries starting with a '#' will be ignored.
	default: ~/images.idb

- Auto update image list
	Select whether the image list should be automatically updated 
	when the image database file is modified.
	default: off

- Ignore not found images
	Ignore image files that could not be found.
	default: off

- Randomise images
	Select whether the image list should be randomised or not.
	Note: If it is not set, it will always start at the first image in the list.
	default: on

- Reset timer on "lock" release
	Reset the timer to the initial value when the "image lock" is released.
	default: off

- Reset timer on config changes
	Reset the timer on config changes, i.e. when you hit "apply" button.
	default: off

- Change wallpaper on load
	Changes the wallpaper when the plugin loads.
	default: off

- Change wallpaper on config changes
	Changes the wallpaper when the config changes.
	default: off

- Remember "locked" state from last run
	Remembers whether the current wallpaper was "locked"
	or not when GKrellM last shut down. Use with change-on-load
	option off to load a new wallpaper only on request.
	default: off

- Remember image number from last run
	Remembers the image number from the database that was
	shown when GKrellM last shut down. It starts the next time with
	this image if the image list didn't change.
	default: off

- Center text
	Centers the displayed text.
	default: on

- Display text
	Toggles the text on or off.
	default: on

- Display krell/slider
	Toggles the krell on or off.
	default: on

- Mouse wheel adjusts timer
	When selected, scrolling the mouse wheel adjusts the time
	rather than "lock" the image. Otherwise the adjustment
	works in combination with the <Shift>-key.
	default: off

- Mouse wheel adjusts the timer by nnn seconds
	This is the amount of seconds by which the timer is adjusted
	when scrolling the mouse wheel while holding the <Shift>-key.
	See also "Mouse wheel adjusts timer."
	default: 60


The background change command is set to xsetbg -fullscreen, but in the image database text box ~/Choices/Wallpaper/Centred/*.jpg does nothing.  Is the only way to get it to work to make a duplicate of my wallpapers in .idb format and have them scattered all over my home folder?

---

