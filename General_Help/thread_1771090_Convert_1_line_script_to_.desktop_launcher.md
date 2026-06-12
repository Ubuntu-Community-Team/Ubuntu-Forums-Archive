---
title: "Convert 1 line script to .desktop launcher"
date: 2011-05-30
forum: General Help
---

### Post by Veazer on 2011-05-30
I thought this would be so simple...

I'm trying to create simple backup/restore launchers to fix messed up panels. The scripts are extremely simple:

Backup current panel config:
gconftool-2 --dump /apps/panel > ~/backup/panels/panel-backup.xml

Restore panel config:
gconftool-2 --load ~/backup/panels/panel-backup.xml

How can I edit the launcher, specifically the exec key i presume, so this works properly? I find the wording of the help for desktop entries to be confusing and they don't show any examples other than a super simple one.

From [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html:](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html:)
> The Exec key

The Exec key must contain a command line. A command line consists of an executable program optionally followed by one or more arguments. The executable program can either be specified with its full path or with the name of the executable only. If no full path is provided the executable is looked up in the $PATH environment variable used by the desktop environment. The name or path of the executable program may not contain the equal sign ("="). Arguments are separated by a space.

Arguments may be quoted in whole. If an argument contains a reserved character the argument must be quoted. The rules for quoting of arguments is also applicable to the executable name or path of the executable program as provided.

Quoting must be done by enclosing the argument between double quotes and escaping the double quote character, backtick character ("`"), dollar sign ("$") and backslash character ("\") by preceding it with an additional backslash character. Implementations must undo quoting before expanding field codes and before passing the argument to the executable program. Reserved characters are space (" "), tab, newline, double quote, single quote ("'"), backslash character ("\"), greater-than sign (">"), less-than sign ("<"), tilde ("~"), vertical bar ("|"), ampersand ("&"), semicolon (";"), dollar sign ("$"), asterisk ("*"), question mark ("?"), hash mark ("#"), parenthesis ("(") and (")") and backtick character ("`").

Note that the general escape rule for values of type string states that the backslash character can be escaped as ("\\") as well and that this escape rule is applied before the quoting rule. As such, to unambiguously represent a literal backslash character in a quoted argument in a desktop entry file requires the use of four successive backslash characters ("\\\\"). Likewise, a literal dollar sign in a quoted argument in a desktop entry file is unambiguously represented with ("\\$").

A number of special field codes have been defined which will be expanded by the file manager or program launcher when encountered in the command line. Field codes consist of the percentage character ("%") followed by an alpha character. Literal percentage characters must be escaped as %%. Deprecated field codes should be removed from the command line and ignored. Field codes are expanded only once, the string that is used to replace the field code should not be checked for field codes itself.


"

---

### Post by katykat on 2011-05-30
There are gnome utiltities to create launchers, and even a basic one on the desktop itself to create launchers. I can never remember them....

The way i handle simple scripts like that is simple: 
Put each one into a simple file, chmod it +755, and put it in your desktop directory. 

Anything in your home/desktop directory will show up as an icon.

---

### Post by mc4man on 2011-05-30
I'm gathering you want a Desktop or panel launcher (use unity so don't exactly use in same manner

I'd make a simple script(s) and put in path, then use the scriptname as the command for the launcher

Easiest would be to create a folder in home dir. named bin
Then restart and it will be auto added to your PATH

Then in ~/bin  use something like this in a simply named filed, Ex - backup1

```
#!/bin/bash
gconftool-2 --dump /apps/panel > ~/backup/panels/panel-backup.xml
```

Then create a Desktop launcher (.desktop) and either just use backup1 as command or browse to the script and select (full path is sometimes better but not normally need if in ~/bin or any other bin in PATH
Pick any display name and icon you want.

If you where to open the launcher in a text editor (drop the launcher into a gedit  window or use nautilus action) it  would look similar to this, icon and display name would be what you pick, ect

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Name[en_US]=test4U
Exec=backup1
Name=test4U
Icon=gnome-panel-launcher

```

The above, created by the r. click > 'Create Launcher' has a bit more than really needed - this would suffice
```
[Desktop Entry]
Version=1.0
Type=Application
Name=[COLOR="Blue"]test4U[/COLOR]
Terminal=false
Exec=backup1
Icon=[COLOR="Blue"]gnome-panel-launcher[/COLOR]
```

Where 'Name=' is the display name of the launcher, Icon= can sometimes just be the icon name, or /full/path/to/desired/iconname
(self created .desktops need to made executable if to be used as click on launchers, the actual name of the .desktop when creating doesn't matter, just keep it simple and unique

---

### Post by stinkeye on 2011-05-30
I'm assuming your not using Unity.
On 10.10 I used this script to save and restore my panel.
Also allows you to restore to default.
Save as **PanelRestore.sh**, make executable and link to it in the launcher 
by using the browse button.
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

### Post by Veazer on 2011-05-30
Wow, that script is great and helped me a lot to learn about scripting in general. I had no clue about the existence of zenity, i'm just learning my way around the OS. I think I'll adapt that for creating single / multi monitor switcher app and add some xrandr commands.

@mc4man- It is actually for use in MintMenu and i was just trying to avoid pointing to a single line script for those and just issuing the command directly, but I guess in the long run pointing to a script is better because it can have additional commands easily added.

Thanks for everyone's suggestions and quick response, solved.



> **stinkeye said:**
> I'm assuming your not using Unity.
On 10.10 I used this script to save and restore my panel.
Also allows you to restore to default.
Save as **PanelRestore.sh**, make executable and link to it in the launcher 
by using the browse button.
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

