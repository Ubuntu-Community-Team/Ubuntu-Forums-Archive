---
title: "my script to rsync files in a graphical way"
date: 2012-07-30
forum: General Help
---

### Post by HiImTye on 2012-07-30
I wrote a bash script that uses rsync in a graphical way. it does the following:


[LIST=1]
[*]pops up a zenity folder selection to choose the destination (a folder on a pen drive, etc)
[*]pops up a zenity file selection to choose a file to transfer
[*]offers to rename the file before it's moved
[*]makes a link to that file in a 'temp' folder so that it can retain any name changes
[*]repeat steps 2-4 until the user chooses 'cancel' on the file selection popup
[*]opens a gnome-terminal and rsyncs the files to the destination inside of it (this means you don't have to 'run in terminal' to actually see the rsync progress)
[/LIST]
there are some variables at the top of the script that you might want to change for your needs. I have done my best effort to notate the script and have notated each of these settings as well.

rsyncVideos.sh
```
#!/bin/bash

# our temp folder
rsync_temp=$HOME/Videos/.rsync-temp
# our default destination folder
rsync_dest=/media/storage/
# our default folder to copy from
rsync_target=$HOME/Videos/

# make our temp folder
mkdir $rsync_temp
# get our destination folder
eval rsync_dest=$(zenity --file-selection --directory --title="destination folder" --filename="$rsync_dest")

# make soft links to our target files to make rsyncing them easier
while :
do
 rsync_file=$(zenity --file-selection --title="input file" --filename="$rsync_target")
 if [ -n "$rsync_file" ]; then
   # offer to rename the soft link to rename the output file
   rsync_name=$(echo "$rsync_file" | sed 's|.*/\(.*\)$|\1|')
   rsync_shortname=$(zenity --entry --title="output filename" --text="output filename" --entry-text="$rsync_name")
   # only make a link if we have a file name
   if [ -n "$rsync_name" ]; then
     ln -s "$rsync_file" "$rsync_temp"/"$rsync_shortname"
   fi
 # if we don't have an input file, exit our loop
 else
   break
 fi
done

# rsync all of our files onto our pen drive
gnome-terminal -x rsync -PL "$rsync_temp"/* "$rsync_dest"

# delete our temp files and exit
rm -fR $rsync_temp
exit
```

---

