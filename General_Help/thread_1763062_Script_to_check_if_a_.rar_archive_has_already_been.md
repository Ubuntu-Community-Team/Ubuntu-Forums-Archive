---
title: "Script to check if a .rar archive has already been extracted?"
date: 2011-05-19
forum: General Help
---

### Post by Error07 on 2011-05-19
> trying to run a script every 30 minutes that checks a directory recursively and extracts any archives that have yet to be extracted.     

I tried the unrar o- option which does not overwrite, but it still goes through the motions of extracting the files, then just skips the overwrite so its wasting cycles and HDD life (especially if running every 15-30 minutes).      

What are my options?   

I really just want:    

if (archive has already been extracted)  
then (skip extraction)  
else (extract archive)     

is there any simple way to accomplish this?   Thanks.


My formatting kept getting jumbled into one big paragraph so I tossed it in a quote tag =/

---

### Post by Telengard C64 on 2011-05-20
Depending on the filesystem and mountflags, it is possible on Linux systems to determine the last time a file was accessed.

[http://en.wikipedia.org/wiki/Atime_%28Unix%29#atime](http://en.wikipedia.org/wiki/Atime_%28Unix%29#atime)

That doesn't tell you whether then archive was extracted, only that it was accessed. I don't think it's going to be a solution for you.

---

### Post by DaithiF on 2011-05-20
Hi,
have your script create a marker file whose timestamp can be used to compare vs. the modification times of the rar files next time the script runs.  Any rar file which has been modified since the last time the script run you extract, otherwise you ignore it.

something like this:

```
#!/bin/bash
marker_file=/path/to/marker
find /start/dir -type f -iname '*.rar' -print0 | while read -r -d '' file
do
    [[ ! -e "$marker_file" || "$file" -nt "$marker_file" ]] && echo unrar "$file" 
done
touch "$marker_file"

```

the conditional expression will be true if either the marker file doesn't exist (first time the script runs), or if a particular file has been modified since the marker file.  Replace the echo unrar ...etc command above with whatever the actual extract command should be.

---

### Post by Error07 on 2011-05-20
Okay its a little clunky (not too bad though) but its working pretty flawlessly. 

What I do is call a script that starts at the folder where my completed torrent files are stored, and checks recursively into each sub-directory checking 2 deep - in each directory it runs a second script which checks if the marker file has been created indicating the files have already been extracted or if no archive exists. 

First script (to run from cron on a regular interval): 

```
#!/bin/bash
scanLoc="/home/user/torrents/completed"
extractScriptLoc="/home/user/scripts/extractRar.sh"

find $scanLoc -maxdepth 2 -type d -exec $extractScriptLoc $1 '{}' \;
```Second script to do the work:

```

#!/bin/bash
markerFile="extractOK"
extractLoc="/home/user/torrents/extracted"


if [ -e "$1/$markerFile" ] || [ ! -e "$1"/*.rar ]; then
     echo "Marker file exists or contains no rar archive."
else 
    echo "marker file not found, extracting."
    unrar x "$1"/*.rar $extractLoc
    > $1/extractOK
fi
```Hope someone else gets use out of this - might not be the cleanest way to do it but it works!  :guitar:

edit: nice timing [DaithiF]("http://ubuntuforums.org/member.php?u=867532")! I had just finished it up with some help in the IRC chan - now its time to pass out!! lots of helpful people, I appreciate it a lot =D  __[]("http://ubuntuforums.org/member.php?u=867532")[]("http://ubuntuforums.org/member.php?u=867532")

---

