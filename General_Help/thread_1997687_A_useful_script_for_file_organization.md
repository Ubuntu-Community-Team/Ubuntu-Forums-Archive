---
title: "A useful script for file organization"
date: 2012-06-05
forum: General Help
---

### Post by luigifgr on 2012-06-05
Hey,

I was wondering how hard would it be to create a small script that will move files based on keywords into their corresponding folder:

e.g.

you have 5 files in your Home folder:

ubuntu.12.04.iso
kubuntu.12.04.iso
edubuntu.12.04.iso
lubuntu.12.04.iso
xubuntu.12.04.iso

the script then looks for certain keywords;
if it finds "ubuntu", it'll move that iso to a folder called "Ubuntu" (same for kubuntu, xubuntu, etc)

```

#!/bin/bash

#script to find and move files

src_dir="/path/to/source/directory"
des_dir_ubuntu="/path/to/destination/directory/for/ubuntu"
des_dir_kubuntu="/path/to/destination/directory/for/kubuntu"
des_dir_xubuntu="/path/to/destination/directory/for/xubuntu"
des_dir_lubuntu="/path/to/destination/directory/for/lubuntu"
des_dir_edubuntu="/path/to/destination/directory/for/edubuntu"

find "$src_dir" -regex ".*\(*ubuntu*)$" -type f -exec mv '{}' "$des_dir_ubuntu" ';'
find "$src_dir" -regex ".*\(*kubuntu*)$" -type f -exec mv '{}' "$des_dir_kubuntu" ';'
find "$src_dir" -regex ".*\(*xubuntu*)$" -type f -exec mv '{}' "$des_dir_xubuntu" ';'
find "$src_dir" -regex ".*\(*lubuntu*)$" -type f -exec mv '{}' "$des_dir_lubuntu" ';'
find "$src_dir" -regex ".*\(*edubuntu*)$" -type f -exec mv '{}' "$des_dir_edubuntu" ';'

```
Also, can we automate the script to work every hour/day/week? Or can we simply make it a startup app?
Any imput would be very appreciated, considering I have strictly no idea what I'm doing here. :lolflag:

Thanks!

---

### Post by zero2xiii on 2012-06-05
Hay,

A simple "For In" loop should do the trick. About the timing thing I am not to sure though... Making it a script running at boot, I would not recommend, since it will slow down booting A LOT if it has to move large files.

Rather make it activate when the computer was inactive, an easy way to do this would be running the script on invoking of the screen saver - See the following links for tips and a nudge in the direction I am thinking in:

[http://blog.troyastle.com/2011/06/run-scripts-when-gnome-screensaver.html](http://blog.troyastle.com/2011/06/run-scripts-when-gnome-screensaver.html)
[http://superuser.com/questions/205334/how-do-you-get-ubuntu-to-automatically-run-a-program-every-time-the-screen-is-un](http://superuser.com/questions/205334/how-do-you-get-ubuntu-to-automatically-run-a-program-every-time-the-screen-is-un)

This should cause the script to be a more background-ish process and not interfere with normal opperation.

Just a random stone or two in the bush. Good luck, but I think you are on the right path. The code should be optimizable a lot, but, then again of its a background thing, I doubt that will be of a big concern... 

Cherz

---

### Post by traditionalist on 2012-06-05
> **luigifgr said:**
> Hey,

I was wondering how hard would it be to create a small script that will move files based on keywords into their corresponding folder:

e.g.

you have 5 files in your Home folder:

ubuntu.12.04.iso
kubuntu.12.04.iso
edubuntu.12.04.iso
lubuntu.12.04.iso
xubuntu.12.04.iso

the script then looks for certain keywords;
if it finds "ubuntu", it'll move that iso to a folder called "Ubuntu" (same for kubuntu, xubuntu, etc)

```

#!/bin/bash

#script to find and move files

src_dir="/path/to/source/directory"
des_dir_ubuntu="/path/to/destination/directory/for/ubuntu"
des_dir_kubuntu="/path/to/destination/directory/for/kubuntu"
des_dir_xubuntu="/path/to/destination/directory/for/xubuntu"
des_dir_lubuntu="/path/to/destination/directory/for/lubuntu"
des_dir_edubuntu="/path/to/destination/directory/for/edubuntu"

find "$src_dir" -regex ".*\(*ubuntu*)$" -type f -exec mv '{}' "$des_dir_ubuntu" ';'
find "$src_dir" -regex ".*\(*kubuntu*)$" -type f -exec mv '{}' "$des_dir_kubuntu" ';'
find "$src_dir" -regex ".*\(*xubuntu*)$" -type f -exec mv '{}' "$des_dir_xubuntu" ';'
find "$src_dir" -regex ".*\(*lubuntu*)$" -type f -exec mv '{}' "$des_dir_lubuntu" ';'
find "$src_dir" -regex ".*\(*edubuntu*)$" -type f -exec mv '{}' "$des_dir_edubuntu" ';'

```Also, can we automate the script to work every hour/day/week? Or can we simply make it a startup app?
Any imput would be very appreciated, considering I have strictly no idea what I'm doing here. :lolflag:

Thanks!

You might find these useful;

[http://linux.about.com/library/gnome/blgnome6n13a.htm](http://linux.about.com/library/gnome/blgnome6n13a.htm)

[http://saravananthirumuruganathan.wordpress.com/2010/08/29/extending-nautilus-context-menus-using-nautilus-actions-scripts-and-python-extensions/](http://saravananthirumuruganathan.wordpress.com/2010/08/29/extending-nautilus-context-menus-using-nautilus-actions-scripts-and-python-extensions/)

Group into new folder ( Shell script);

```

#!/bin/bash

# Nautilus-Action script: Group files into new folder
# Create a new folder then move selected items into it.

# Author: soleilpqd@gmail.com
# License: GNU GPL

# INSTALL:
#    Copy into ~/.gnome2/nautilus-scripts, add executable permission (if needed).

if [ "$NAUTILUS_SCRIPT_SELECTED_URIS" == "" ]; then exit 1; fi
target=$( zenity --entry --title="Create new folder" --text="Enter new folder name:" )
if [ -z "$target" ]; then exit 0; fi
while [ -e "$target" ]; do
    target=$( zenity --entry --title="Create new folder" --text="\"$target\" existed. Enter other name:" )
    if [ -z "$target" ]; then exit 0; fi
done
mkdir "$target"
if [ ! -e "$target" ]; then
    zenity --error --text="Failed to create folder \"$target\"!"
    exit 1
fi
gvfs-move $NAUTILUS_SCRIPT_SELECTED_URIS "$target"

```

---

### Post by Vaphell on 2012-06-05
OP, your approach will put everything in ubuntu destination dir and it's rather easy to figure out why ;-) your regexes also seem off.

---

