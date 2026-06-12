---
title: "Create new user with same rights + docs, just diff desktop for switching screen size"
date: 2010-10-06
forum: General Help
---

### Post by finny388 on 2010-10-06
my netbook is usually hooked up to my lcdtv at 1360x768

but when I unhook and go mobile, I want to continue using the reg gnome desktop but need a profile that has a tidier panel as res on the netbook is 1024x600.

How can I create a profile (or user) where the only difference is the desktop setup? I'd want to use the same home directory, have the same rights, basically be the same admin user but load a different desktop/panels/wallpaper

If there are alternatives I'd lean towards a solution that uses the least amount of storage.

thanks

---

### Post by realzippy on 2010-10-06
[Howtocloneuser]("http://ubuntuforums.org/showthread.php?t=365440") see post #5


...there is a tool:

[disper]("http://willem.engen.nl/projects/disper/")

that does exactly what you want (change resolution automatically depending on plugged panel),without a new user....

---

### Post by finny388 on 2010-10-07
> disper

that does exactly what you want (change resolution automatically depending on plugged panel),without a new user....

That looks cool but I have no problem rebooting between displays.

What I want is a different desktop for the same user between displays.

e.g.
[LIST]
[*]At 1360x768 the panel with have 10 icon links
[*]At 1024x600 the panel with have 5 icon links because with 10 they get crowded and some are pushed off the screen
[/LIST]

Different wallpaper would be nice to easily know what mode I'm in but changing which panel loads is the rub.

Thanks

---

### Post by realzippy on 2010-10-07
Ok,so you have to clone your user,see post #5 in given link.

---

### Post by finny388 on 2010-10-07
How about a startup script that prompts for Mobile or Desktop, then sets wallpaper and loads a panel.

It just occurred to me that I have a script I [**_downloaded_**]("http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/") that backs up and restores panels.

I could change the prompt, have it load the appropriate panel from back up.

The icing would be to change the wallpaper. How to do that?

```
#!/bin/sh
#
# GNOME Panel Save / Restore
# Writen by PhrankDaChicken
#
# http://ubuntu.online02.com
#
#
# Updated to add restore defaults by jimjimovich
# http://www.starryhope.com
#
#


DIR=$(pwd)
TITLE="PanelRestore"

Main () {
	CHOICE=$(zenity --list --title "$TITLE" --hide-column 1 --text "What do you want to do?" --column "" --column "" \
"0" "Save Panel Settings" \
"1" "Restore Panel Settings" \
"2" "Restore Default Panel Settings")
	if [ $CHOICE = 0 ]; then
		Panel_Save
	fi
	if [ $CHOICE = 1 ]; then
		Panel_Restore
	fi
	if [ $CHOICE = 2 ]; then
		Panel_Defaults
	fi	
}

Panel_Restore () {
	FILE=$(zenity --title "$TITLE: Open File" --file-selection --file-filter "*.xml" )
	if [ -n "$FILE" ]; then 
		gconftool-2 --load "$FILE"
		killall gnome-panel
	fi
	Main
}

Panel_Save () {
	FILE=$(zenity --title "$TITLE: Save File" --file-selection --save --confirm-overwrite --filename "Gnome_Panel.xml" --file-filter "*.xml" )
	if [ -n "$FILE" ]; then 
		EXT=$(echo "$FILE" | grep "xml")
		if [ "$EXT" = "" ]; then
			FILE="$FILE.xml"
		fi
		gconftool-2 --dump /apps/panel > $FILE
		zenity --info --title "$TITLE: File Saved" --text "File saved as: \n $FILE"
	fi
	Main
}

Panel_Defaults () {
	zenity --question --text="Are you sure you want to restore the default top and bottom panels?"
	gconftool-2 --recursive-unset /apps/panel
	rm -rf ~/.gconf/apps/panel
	pkill gnome-panel
	exit
}

Main

# END OF Script
```

---

