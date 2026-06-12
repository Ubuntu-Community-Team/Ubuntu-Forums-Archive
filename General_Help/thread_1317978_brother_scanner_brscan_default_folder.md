---
title: "brother scanner brscan default folder"
date: 2009-11-07
forum: General Help
---

### Post by vzhen on 2009-11-07
I just done my brother dcp-150c printer + scanner. Everythings OK but the scanned picture always save in default folder /home/brscan.

How do i change the default folder. 

I have been searching for hours but can't get it.

I use gimp and all the drivers, scan_key_tool from solution brother website.

I didn't use xsane because it doesn't work to me.

---

### Post by KeyserSoze93 on 2009-11-07
I don't know offhand, since I don't have a brother scanner, however if it looks like to much bother to change, you could try doing what I did with KDE's kooka scanning tool.

I couldn't find any output options in Kooka, however what I did was the delete the folder it defaulted to (~/.kde/share/kooka or something), and replace it with a symlink to the folder I wanted the pictures to go in (ln -s ~/Pictures/scans ~/.kde/share/kooka)

It's not ideal, but it worked, and should work in your case too if there's no more elegant solution.

---

### Post by randyr505 on 2009-11-13
I was looking for this exact solution. Here is what I found:
[http://solutions.brother.com/linux/sol/printer/linux/scankey_install.html#2](http://solutions.brother.com/linux/sol/printer/linux/scankey_install.html#2)

Basically it says you can edit a script to change the location (among other things)
/usr/local/Brother/sane/script/scantofile-0.2.0-1.sh

There is a line in that script that tells it where to save your file
output_file=`mktemp ~/brscan/brscan.XXXXXX`

Beware though there is also a line above that line that creates the directory ~/brscan.

I simply did this:
Add this line:
dir=~/MyScans
Change 2 lines to look like the following
mkdir -p $dir
output_file=`mktemp $dir/brscan.XXXXXX`


Here is information from the url above that shows how to save as pdf instead of an image which is what I prefer. My version of this script is 2.1-3 so it doesn't look exactly like the following (yes it seems odd the original line has .pdf already).

Change the line:
scanimage --device-name "$device" --resolution $resolution > "$output_file".pdf
to:
scanimage --device-name "$device" --resolution $resolution \
| pnmtops | gs -q -dNOPAUSE -sDEVICE=pdfwrite \
-sOutputFile=- - > "$output_file".pdf

---

