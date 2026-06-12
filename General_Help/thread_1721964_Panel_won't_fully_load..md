---
title: "Panel won't fully load."
date: 2011-04-05
forum: General Help
---

### Post by irv on 2011-04-05
First I am running 10.10 since it was released and it was running great. But this morning it does not fully boot. It freezes at the point of loading the panel. At that point I can do nothing but reboot. I tried safe mode and ran a repair on the apps, The problem is still there. I can't get to a terminal only a prompt in safe mode. It must have been an update I did yesterday.
When I go to shut down (hit the power button) I get a warning saying the panel is not fully loaded and I have the option to not force a shut down or shutdown.
Any idea what I can try? I am dead in the water at this point.

---

### Post by irv on 2011-04-05
OK, here are all the things I tried: First I can get to the desktop with a part of the gnome-panel loaded. If I press the Ctrl + Alt + T keys I get to a terminal window. from there I entered 

```
gksudo synaptic &
``` 
to run the package manager.
I tried re-installing and completely removing and re-installing the gnome-panel package, but none of these things help. I am still sitting with a part of the panel loading at boot up. Is there a way I can go back to an older version of the panel? I believe the updated panel is not working right.
Or is there some configuration file somewhere that need to be remove and then re-install the panel?
I am lost for things to try.
Is there anyone that could help me with this?
Thanks.

---

### Post by searchfgold6789 on 2011-04-05
Now I thought you could remove the panel just by right clicking it.
Actually, try 

[LIST]
[*]right clicking it and click properties, or customize panel. Make sure everything is set the way you want it, remove and reinstall the panel.
[/LIST]

[LIST]
[*]You can run the panel using the command [FONT=Courier New]gnome-panel[/FONT].
[/LIST]

[LIST]
[*]I have also seen the panel fail on machines that have faulty memory. All panels I have seen seem very sensitive to the memory. Try a memtest.
[/LIST]

---

### Post by stinkeye on 2011-04-05
To get your panel back to default try from tty1(ctrl+alt+F1) or terminal
```
gconftool-2 --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
```
and reboot.

**PS If you remove gnome-panel it will also remove ubuntu-desktop.**

---

### Post by irv on 2011-04-05
> **stinkeye said:**
> To get your panel back to default try from tty1(ctrl+alt+F1) or terminal
```
gconftool-2 --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
```
and reboot.

**PS If you remove gnome-panel it will also remove ubuntu-desktop.**
OK this worked, I got the panel back. I did have one error that popped up 
[ATTACH]188161[/ATTACH]
I deleted it from the panel and now it should work.
Thanks for your help.

Just for the record I couldn't even right mouse click on the panel nothing happen.
Thanks for the help

---

### Post by stinkeye on 2011-04-05
No problem.
If your interested this script will save your panel settings once
you have set them up again how you like it.
It is able to
# save current settings
# restore from the saved file
# restore panel to default.

Save as PanelRestore.sh

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

### Post by irv on 2011-04-05
> **stinkeye said:**
> No problem.
If your interested this script will save your panel settings once
you have set them up again how you like it.
It is able to
# save current settings
# restore from the saved file
# restore panel to default.

Save as PanelRestore.sh

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
Great and thanks again. I setup the scrip and saved my panelsettings so if this happens again I can recover quickly. It's things like this that makes Ubuntu Linux great. Not only the help but the things you can do with it. Much better than Windows. 
This morning I was thinking I might have to use Windows again even for a little while, and it made me feel funny inside. You could say I felt sick to the point I wanted to up-chuck. You know what I mean.
Thanks
Irv

---

