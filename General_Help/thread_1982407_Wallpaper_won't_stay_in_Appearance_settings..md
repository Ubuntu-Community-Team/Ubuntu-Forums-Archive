---
title: "Wallpaper won't stay in Appearance settings."
date: 2012-05-18
forum: General Help
---

### Post by twodogs on 2012-05-18
I can select a new wallpaper but the wallpaper won't appear in the 'Appearance' settings box the next time I open it.

I don't like the new 'Appearance' box.  It's buggy and doesn't work.

I installed Nitrogen but it won't apply the selected wallpaper to my desktop.

Anyone use something better than this?

---

### Post by tecknomage on 2012-08-02
**REF:** Ubuntu 12.04, GNOME Desktop

I have the same problem.

**Nitrogen's [Apply]** button does not work.

I wanted something better than Ubuntu's 'Wallpaper Manager' (*aka Appearance*) because it only shows a limited list of wallpapers, and having to navigate to "MyWallpapers" folder to choose wallpapers is cumbersome, especially since it does NOT memorize the wallpapers there.

Nitrogen would do the job IF [Apply] would work :-?

Ubuntu's 'Wallpaper Manager' needs what other Linux distributions have for wallpaper managers, **[Add Wallpaper] & [Add Theme] buttons**.

**ALSO** it would be nice if **Software Center** had a special section for getting themes and wallpapers.

---

### Post by twodogs on 2012-08-02
I found a script that will apply an image as wallpaper and it works with Gnome 3 too!
reference this page --> [https://github.com/gracca/Set-background-in-Gnome-3/blob/master/set-background-gnome3](https://github.com/gracca/Set-background-in-Gnome-3/blob/master/set-background-gnome3)

Create a new 'shell script' and put it in ~/.gnome2/nautilus-scripts/ and make it executable.

This is the code...

#!/bin/bash

#-----------------------------------------------------------------------#
# Nautilus script to change background in Gnome 3 #
# You need to install Zenity to run this script #
# #
# Copyright (C) 2011 Germán A. Racca - gracca[AT]gmail[DOT]com #
# #
# This program is free software: you can redistribute it and/or modify #
# it under the terms of the GNU General Public License as published by #
# the Free Software Foundation, either version 3 of the License, or #
# (at your option) any later version. #
# #
# This program is distributed in the hope that it will be useful, #
# but WITHOUT ANY WARRANTY; without even the implied warranty of #
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the #
# GNU General Public License for more details. #
# #
# You should have received a copy of the GNU General Public License #
# along with this program. If not, see <http://www.gnu.org/licenses/>. #
#-----------------------------------------------------------------------#

# Define version of script
VERSION=0.1

# Define some variables
## guess correct paths
GS=`which gsettings`
ZNTY=`which zenity`

## remove new line in Nautilus env variables
URIS=`echo $NAUTILUS_SCRIPT_SELECTED_URIS | sed 's/\\n//g'`
PATHS=`echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS | sed 's/\\n//g'`

## gsettings keys to change
PIC_URI="org.gnome.desktop.background picture-uri"
PIC_OPT="org.gnome.desktop.background picture-options"

## guess file tipe
FILE=`file $PATHS | grep image`

#------------------------------------------------#
# Function to test if an image file was selected #
#------------------------------------------------#

function test_file() {
if [ -z $URIS ]; then
$ZNTY --error --no-wrap --text="You need to select an image file first\!"
exit 1
elif [ -z $FILE ]; then
$ZNTY --error --no-wrap --text="This is not an image file\!"
exit 1
else
return 0
fi

}

#--------------------------------------#
# Function to select a rendering opion #
#--------------------------------------#
function select_option() {

RENDER_OPT=`$ZNTY --list \
--title="How to render the wallpaper" \
--text="Select an option from the list below:" \
--width="300" --height="350" \
--radiolist --column "" --column "" \
TRUE "wallpaper" \
FALSE "centered" \
FALSE "scaled" \
FALSE "stretched" \
FALSE "zoom" \
FALSE "spanned" \
FALSE "none" \
FALSE "About"`

}

#-------------------------------#
# Function to set the wallpaper #
#-------------------------------#
function set_wallpaper() {

case "$RENDER_OPT" in
About)
$ZNTY --info --no-wrap --text="Set background in Gnome 3.\n\nVersion $VERSION."
;;
*)
$GS set $PIC_URI "$URIS"
$GS set $PIC_OPT "$RENDER_OPT"
$ZNTY --info --no-wrap --text="Your new wallpaper is:\n\n$PATHS \($RENDER_OPT\)\n\nCongrats\!"
;;
esac

}

#------------------------------------#
# Function to show a warning message #
#------------------------------------#
function warning_message() {

$ZNTY --warning --no-wrap --text="Nothing was changed."

}


#+++++++++++++++++++++++++++++++++++++++++++++#
#++ Run the functions to set the wallpaper ++#
#+++++++++++++++++++++++++++++++++++++++++++++#

test_file

select_option

case $? in
0)
set_wallpaper
;;
1|-1)
warning_message
;;
esac

---

### Post by uRock on 2012-08-02
WHen you open the appearance menu, click the scroll menu to the right and select Pictures Folder where you should see every photo you've used. That has been my experience with 12.04

---

### Post by tecknomage on 2012-08-03
> **uRock said:**
> WHen you open the appearance menu, click the scroll menu to the right and select Pictures Folder where you should see every photo you've used. That has been my experience with 12.04

Not on my system. All it shows is the wallpaper set for the Theme selected. I have to use the [+], navigate to "MyWallpapers" folder in my Pictures, and manually highlight all wallpapers there for them to show on the "Pictures Folders" list.


This is why I trying to get [**Nitrogen**]("https://wiki.archlinux.org/index.php/Nitrogen") to work (*[Add] button does not work*) it does show all wallpapers in my "MyWallpapers."

---

