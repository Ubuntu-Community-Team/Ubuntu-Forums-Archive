---
title: "Random Music bash script help"
date: 2010-06-24
forum: General Help
---

### Post by inameiname on 2010-06-24
A wonderful gentleman on here gave me this script:

> #!/bin/bash
#Licence: GPL v3 or (at your option) any later as published by FSF.

# add as much as wanted; include the dot before the extension
FORMATS=( .mp3 .wav .ogg )

PLAYLIST=""
PLAYLIST_SIZE=""
SHUFCMD=shuf

# $1 if exists is maximum playlist size (defaults to all)
# $2... are directories to scan for files with formats

[ $# -ge 1 ] && PLAYLIST_SIZE=${1}
shift
if [ -n "${PLAYLIST_SIZE}" ] ; then
    SHUFCMD+=" --head-count=${PLAYLIST_SIZE}"
fi
for dir in $@; do
    PLAYLIST+=${FORMATS[@]/#\./${dir}\/\*\.}
done
totem $(ls ${PLAYLIST} | ${SHUFCMD})...it works great, however, as it is  now, it only seems to work if it was in the very folder (or in  nautilus-scripts and I right clicked it from the very folder) it was  looking for the music, such as in ~/Music, and then what it did was read  all of the subfolders on the first tier in there, and then all the  subfolders in those for music. 

I figured out that by adding, cd ~/Music, it enables it to be  right clicked anywhere and opens music only from the ~/Music folder it can be used.

However, one thing that's odd  is if the subfolder in ~/Music folder has a 'space' in it's title, (ie,  ~/Music/Green Day), it would fail. This is not the case for subfolders  of the first tier subfolders in ~/Music though, (ie, ~/Music/Jazz/Simply  Red). 

Anybody know how to fix this?

Also, another issue that this script does is that while the folders are played at random, (ie  ~/Music/Jazz/Simply Red plays first, then ~/Music/Jazz/Astronaut Jives  plays second, ~/Music/Jazz/Cornholio third, ~/Music/Jazz/Beck fourth,  and etc.), the tracks/songs within each folder is played in order, (ie.,  1.mp3, 2.mp3, 3.mp3, 4.mp3, and etc.).                                                                                                                   

Is there a way to randomize the order of the songs within the folders too?

---

### Post by inameiname on 2010-06-24
I found this script, but I'm not sure how I can adapt it or use parts of it to work with mine. Maybe somebody else could, idk:

> 
#!/usr/bin/python

import glob
import random
import os.path
import os
import sys
import time

def play_random(dir):
files = glob.glob(os.path.join(dir, "*.mp3"))
if len(files) == 0:
return
random.shuffle(files)
#Only way to clear the playlist is to start xmms with a file to play.
print files[0]
os.system('xmms "%s" 2> /dev/null &' % files[0])
#Add the rest of the songs to the queue.
#I found I needed to pause a second or so first to make this work.
time.sleep(1)
for i, file in enumerate(files):
if i > 0:
print file
os.system('xmms -e "%s" 2> /dev/null &' % file)
os.system("xmms -p 2> /dev/null")

if __name__ == "__main__":
if len(sys.argv) < 2:
folder = os.environ["NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"]
else:
folder = sys.argv[1]
play_random(folder)


---

### Post by VH-BIL on 2010-06-24
Here  is a script i made to shuffle video, it should work for music as well

```
#!/bin/bash
# ================================================================================
#    Project      : TV Shuffle
#    Author       : VH-BIL
#    Date         : 10th Nov 2009
#    Info         :
# The "DestPath" variable holds the path of where to write all the
# playlists.
#
# The variable "MixedDestPath" holds the path and filename for the playlist
# of the mixed tv.
#
# The "TV_Count" variable is then number of individual tv shows to be
# displayed in the menu.
#
# Arrays "TV_Name" and "TV_Path" hold information about the tv shows in
# the menu. "TV_Name" is the name of the TV show and "TV_Path" is the path
# to where all the tv episodes are stored. The number of tv episodes must
# be recorded in "TV_Count"
#
# The "Mixed_Count" variable is the number of tv shows to be put combined
# into the mixed TV playlist.
#
# Just like the "TV_Name" and "TV_Path" variables the "Mixed_Name" and
# Mixed_Path hold the name and file path of the TV shows to be in the
# mixed TV playlist.
#
# This is one of the first scripts I have made. I work as a programmer
# but as a C# programmer. I wanted an easy way of playing my TV shows shuffled
# while not having to update playlists when adding new episodes. 
# ================================================================================

# The Destination Path Of All The Playlists
DestPath="/home/bill/playlists/"
# The Path And Filename Of The Mixed TV Playlist
MixedDestPath="/home/bill/playlists/MixedTV.plist"

# Colour Codes
black='\E[30;40m'
red='\E[31;40m'
green='\E[32;40m'
yellow='\E[33;40m'
blue='\E[34;40m'
magenta='\E[35;40m'
cyan='\E[36;40m'
white='\E[37;40m'

# TV Shows
TV_Count=17
TV_Name[0]="That '70s Show"
TV_Path[0]="/Repository/Media/Movies/TV/That '70s Show"
TV_Name[1]="American Dad"
TV_Path[1]="/Repository/Media/TV/American Dad"
TV_Name[2]="How I Met Your Mother"
TV_Path[2]="/Repository/Media/TV/How I Met Your Mother"
TV_Name[3]="Family Guy"
TV_Path[3]="/Repository/Media/Movies/TV/Family Guy Seasons 1-8"
TV_Name[4]="Kenny vs Spenny"
TV_Path[4]="/Repository/Media/TV/Kenny vs Spenny"
TV_Name[5]="My Name Is Earl"
TV_Path[5]="/Repository/Media/TV/My Name Is Earl"
TV_Name[6]="MythBusters"
TV_Path[6]="/Repository/Media/TV/MythBusters"
TV_Name[7]="Drew Carey"
TV_Path[7]="/Repository/Media/Movies/TV/Drew Carey"
TV_Name[8]="The Big Bang Theory"
TV_Path[8]="/Repository/Media/TV/The Big Bang Theory"
TV_Name[9]="Scrubs"
TV_Path[9]="/Repository/Media/TV/Scrubs"
TV_Name[10]="Seinfeild"
TV_Path[10]="/Repository/Media/TV/Seinfeild"
TV_Name[11]="South Park"
TV_Path[11]="/Repository/Media/TV/South Park"
TV_Name[12]="The Simpsons"
TV_Path[12]="/Repository/Media/TV/The Simpsons"
TV_Name[13]="The Universe"
TV_Path[13]="/Repository/Media/TV/The Universe"
TV_Name[14]="Trailer Park Boys"
TV_Path[14]="/Repository/Media/TV/Trailer Park Boys"
TV_Name[15]="Two And A Half Men"
TV_Path[15]="/Repository/Media/TV/Two And A Half Men"
TV_Name[16]="XFiles"
TV_Path[16]="/Repository/Media/TV/XFiles"

# Mixed TV
Mixed_Count=8
Mixed_Name[0]="How I Met Your Mother"
Mixed_Path[0]="/Repository/Media/TV/How I Met Your Mother"
Mixed_Name[1]="Seinfeild"
Mixed_Path[1]="/Repository/Media/TV/Seinfeild"
Mixed_Name[2]="South Park"
Mixed_Path[2]="/Repository/Media/TV/South Park"
Mixed_Name[3]="The Simpsons"
Mixed_Path[3]="/Repository/Media/TV/The Simpsons"
Mixed_Name[4]="Trailer Park Boys"
Mixed_Path[4]="/Repository/Media/TV/Trailer Park Boys"
Mixed_Name[5]="Two And A Half Men"
Mixed_Path[5]="/Repository/Media/TV/Two And A Half Men"
Mixed_Name[6]="X-Files"
Mixed_Path[6]="/Repository/Media/TV/XFiles"
Mixed_Name[7]="The Big Bang Theory"
Mixed_Path[7]="/Repository/Media/TV/The Big Bang Theory"


DisplayMenu()
{
  echo -en $white
  clear
  echo -en $white
  echo "TV Shuffle Script"
  echo -en $red
  echo "================="
  echo
  for ((cnt=0 ; cnt<=TV_Count-1 ; cnt++))
  do
    if [ $cnt -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo ${TV_Name[cnt]}
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo ${TV_Name[cnt]}
    fi
  done
    if [ $TV_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Mixed TV"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Mixed TV"
    fi
    let "TV_Count += 1"
    if [ $TV_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Display Mixed TV"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Display Mixed TV"
    fi
    let "TV_Count -= 1"
  echo
  echo -n "Make A Selection :"
}

DisplayMixedTV()
{
  echo  
  for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    echo -en $white
    echo ${Mixed_Name[cnt]}
  done
  echo
}

ShuffleEpisode()
{
  cd /
  find "${TV_Path[$1]}" > "$DestPath${TV_Name[$1]}.plist"
  mplayer -playlist "$DestPath${TV_Name[$1]}.plist" -shuffle
}

MixedTV()
{
  echo "" > $MixedDestPath
  cd /
    for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    find "${Mixed_Path[$cnt]}" > "$DestPath${Mixed_Name[$cnt]}.plist"
    echo "" > $MixedDestPath"_cat"
    cat "$DestPath${Mixed_Name[$cnt]}.plist" $MixedDestPath > $MixedDestPath"_cat"
    rm $MixedDestPath
    mv $MixedDestPath"_cat" $MixedDestPath
  done
  mplayer -playlist $MixedDestPath -shuffle
}

DisplayMenu
read input

if [ $input -eq $TV_Count ]
then
  MixedTV
fi

let "TV_Count += 1"
if [ $input -eq $TV_Count ]
then
  DisplayMixedTV
fi
let "TV_Count -= 1"

if [ $input -lt $TV_Count ]
then
  ShuffleEpisode $input
fi
```

---

### Post by inameiname on 2010-06-24
That is a very cool script, but I'm not sure how it'd work for me for what I want. I'd like my scirpt to be able to look through thousands of songs in hundreds of folders, and randomly play one. Seems like for yours, I'd have to add to the list all of the paths for every single song, idk. Forgive me if I'm mistaken.

---

### Post by VH-BIL on 2010-06-24
You can use the script i made to set a playlist and/or your whole library. The reason I made the script is I wanted the shuffled playlist to be created every time I ran the script just in case I added new files. The script will add files to the playlist recursively so it doesn't matter if they are in different folders. Just add the root folder of your music library. 

You can use the script in this way:
```
#!/bin/bash
# ================================================================================
#    Project      : TV Shuffle
#    Author       : VH-BIL
#    Date         : 10th Nov 2009
#    Info         :
# The "DestPath" variable holds the path of where to write all the
# playlists.
#
# The variable "MixedDestPath" holds the path and filename for the playlist
# of the mixed tv.
#
# The "TV_Count" variable is then number of individual tv shows to be
# displayed in the menu.
#
# Arrays "TV_Name" and "TV_Path" hold information about the tv shows in
# the menu. "TV_Name" is the name of the TV show and "TV_Path" is the path
# to where all the tv episodes are stored. The number of tv episodes must
# be recorded in "TV_Count"
#
# The "Mixed_Count" variable is the number of tv shows to be put combined
# into the mixed TV playlist.
#
# Just like the "TV_Name" and "TV_Path" variables the "Mixed_Name" and
# Mixed_Path hold the name and file path of the TV shows to be in the
# mixed TV playlist.
#
# This is one of the first scripts I have made. I work as a programmer
# but as a C# programmer. I wanted an easy way of playing my TV shows shuffled
# while not having to update playlists when adding new episodes. 
# ================================================================================

# The Destination Path Of All The Playlists
DestPath="/home/bill/playlists/"
# The Path And Filename Of The Mixed TV Playlist
MixedDestPath="/home/bill/playlists/MixedTV.plist"

# Colour Codes
black='\E[30;40m'
red='\E[31;40m'
green='\E[32;40m'
yellow='\E[33;40m'
blue='\E[34;40m'
magenta='\E[35;40m'
cyan='\E[36;40m'
white='\E[37;40m'

# TV Shows
TV_Count=1
TV_Name[0]="My Music Library"
TV_Path[0]="/Repository/Media/Music/"

# Mixed TV
Mixed_Count=2
Mixed_Name[0]="Techno"
Mixed_Path[0]="/Repository/Media/Music/Techno"
Mixed_Name[1]="Hip Hop"
Mixed_Path[1]="/Repository/Media/Music/HipHop"


DisplayMenu()
{
  echo -en $white
  clear
  echo -en $white
  echo "TV Shuffle Script"
  echo -en $red
  echo "================="
  echo
  for ((cnt=0 ; cnt<=TV_Count-1 ; cnt++))
  do
    if [ $cnt -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo ${TV_Name[cnt]}
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo ${TV_Name[cnt]}
    fi
  done
    if [ $TV_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Mixed TV"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Mixed TV"
    fi
    let "TV_Count += 1"
    if [ $TV_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Display Mixed TV"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Display Mixed TV"
    fi
    let "TV_Count -= 1"
  echo
  echo -n "Make A Selection :"
}

DisplayMixedTV()
{
  echo  
  for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    echo -en $white
    echo ${Mixed_Name[cnt]}
  done
  echo
}

ShuffleEpisode()
{
  cd /
  find "${TV_Path[$1]}" > "$DestPath${TV_Name[$1]}.plist"
  mplayer -playlist "$DestPath${TV_Name[$1]}.plist" -shuffle
}

MixedTV()
{
  echo "" > $MixedDestPath
  cd /
    for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    find "${Mixed_Path[$cnt]}" > "$DestPath${Mixed_Name[$cnt]}.plist"
    echo "" > $MixedDestPath"_cat"
    cat "$DestPath${Mixed_Name[$cnt]}.plist" $MixedDestPath > $MixedDestPath"_cat"
    rm $MixedDestPath
    mv $MixedDestPath"_cat" $MixedDestPath
  done
  mplayer -playlist $MixedDestPath -shuffle
}

DisplayMenu
read input

if [ $input -eq $TV_Count ]
then
  MixedTV
fi

let "TV_Count += 1"
if [ $input -eq $TV_Count ]
then
  DisplayMixedTV
fi
let "TV_Count -= 1"

if [ $input -lt $TV_Count ]
then
  ShuffleEpisode $input
fi
```

Edit these lines to change where the playlist file will be created
```
# The Destination Path Of All The Playlists
DestPath="/home/bill/playlists/"
# The Path And Filename Of The Mixed TV Playlist
MixedDestPath="/home/bill/playlists/MixedTV.plist"
```

Edit this line to your music library
```
TV_Path[0]="/Repository/Media/Music/"
```

Edit these lines if you want to create a shuffled playlist
```
# Mixed TV
Mixed_Count=2
Mixed_Name[0]="Techno"
Mixed_Path[0]="/Repository/Media/Music/Techno"
Mixed_Name[1]="Hip Hop"
Mixed_Path[1]="/Repository/Media/Music/HipHop"
```

---

### Post by inameiname on 2010-06-24
Oh wow, thanks for the step-by-step. I'll check it out now and get back with you.

---

### Post by VH-BIL on 2010-06-25
No problems :)
Let me know if you have any problems.

---

### Post by inameiname on 2010-06-25
Alright, so I tried this, and it seems to work. Perhaps your script is a little more fancy than I was needing, but it seems to do the job. I'll play around with it more to ensure it'll work just as I was hoping my original script did, including the two issues I was having which was why I posted this posting.

Oh, and here is my tweaked version of your script (it's rough, but whatever):

```
#!/bin/bash
# ================================================================================
#    Project      : TV Shuffle
#    Author       : VH-BIL
#    Date         : 10th Nov 2009
#    Info         :
# The "DestPath" variable holds the path of where to write all the
# playlists.
#
# The variable "MixedDestPath" holds the path and filename for the playlist
# of the mixed tv.
#
# The "TV_Count" variable is then number of individual tv shows to be
# displayed in the menu.
#
# Arrays "TV_Name" and "TV_Path" hold information about the tv shows in
# the menu. "TV_Name" is the name of the TV show and "TV_Path" is the path
# to where all the tv episodes are stored. The number of tv episodes must
# be recorded in "TV_Count"
#
# The "Mixed_Count" variable is the number of tv shows to be put combined
# into the mixed TV playlist.
#
# Just like the "TV_Name" and "TV_Path" variables the "Mixed_Name" and
# Mixed_Path hold the name and file path of the TV shows to be in the
# mixed TV playlist.
#
# This is one of the first scripts I have made. I work as a programmer
# but as a C# programmer. I wanted an easy way of playing my TV shows shuffled
# while not having to update playlists when adding new episodes.
# ================================================================================

tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi

mkdir /home/me/Music/.playlists
touch /home/me/Music/.playlists/MixedTV.plist
touch /home/me/Music/.playlists/"My Music Library".plist


# The Destination Path Of All The Playlists
DestPath="/home/me/Music/.playlists/"
# The Path And Filename Of The Mixed TV Playlist
MixedDestPath="/home/me/Music/.playlists/MixedTV.plist/"

# Colour Codes
black='\E[30;40m'
red='\E[31;40m'
green='\E[32;40m'
yellow='\E[33;40m'
blue='\E[34;40m'
magenta='\E[35;40m'
cyan='\E[36;40m'
white='\E[37;40m'

# TV Shows
TV_Count=1
TV_Name[0]="My Music Library"
TV_Path[0]="/home/me/Music/"

# Mixed TV
Mixed_Count=2
Mixed_Name[0]="Techno"
Mixed_Path[0]="/home/me/Music/Techno/"
Mixed_Name[1]="Hip Hop"
Mixed_Path[1]="/home/me/Music/HipHop/"


DisplayMenu()
{
  echo -en $white
  clear
  echo -en $white
  echo "TV Shuffle Script"
  echo -en $red
  echo "================="
  echo
  for ((cnt=0 ; cnt<=TV_Count-1 ; cnt++))
  do
    if [ $cnt -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo ${TV_Name[cnt]}
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo ${TV_Name[cnt]}
    fi
  done
    if [ $TV_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Mixed TV"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Mixed TV"
    fi
    let "TV_Count += 1"
    if [ $TV_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Display Mixed TV"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Display Mixed TV"
    fi
    let "TV_Count -= 1"
  echo
  echo -n "Make A Selection :"
}

DisplayMixedTV()
{
  echo
  for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    echo -en $white
    echo ${Mixed_Name[cnt]}
  done
  echo
}

ShuffleEpisode()
{
  cd /
  find "${TV_Path[$1]}" > "$DestPath${TV_Name[$1]}.plist"
  mplayer -playlist "$DestPath${TV_Name[$1]}.plist" -shuffle
}

MixedTV()
{
  echo "" > $MixedDestPath
  cd /
    for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    find "${Mixed_Path[$cnt]}" > "$DestPath${Mixed_Name[$cnt]}.plist"
    echo "" > $MixedDestPath"_cat"
    cat "$DestPath${Mixed_Name[$cnt]}.plist" $MixedDestPath > $MixedDestPath"_cat"
    rm $MixedDestPath
    mv $MixedDestPath"_cat" $MixedDestPath
  done
  mplayer -playlist $MixedDestPath -shuffle
}

DisplayMenu
read input

if [ $input -eq $TV_Count ]
then
  MixedTV
fi

let "TV_Count += 1"
if [ $input -eq $TV_Count ]
then
  DisplayMixedTV
fi
let "TV_Count -= 1"

if [ $input -lt $TV_Count ]
then
  ShuffleEpisode $input
fi

```Two things though I'd like to do is:

1. Figure out how to remove the '.playlists' folder at the end of this script, so each time I use it it'll make a new one, and remove it on exit.

  mkdir /home/me/Music/.playlists
  touch /home/me/Music/.playlists/MixedTV.plist
  touch /home/me/Music/.playlists/"My Music Library".plist
...but where to put...
  rmdir /home/me/Music/.playlists

2. How can I make another version of this which I can also put in my nautilus-scripts, just as where this one will go, and have it look inside whatever directory I want, such as my Music folder on an external hard drive?

---

### Post by VH-BIL on 2010-06-25
Changed the Mixed TV section to folders of specific folders of artists or genres for a playlist to be shuffled I only gave you an example in the previous script.

Use like this:
```
# Mixed TV
Mixed_Count=2
Mixed_Name[0]="Artist 1"
Mixed_Path[0]="/home/me/Music/Artist1Folder/"
Mixed_Name[1]="Artist 2"
Mixed_Path[1]="/home/me/Music/Artist2Folder/"
```

You can add another folder to the mixed list like this:

```
# Mixed TV
Mixed_Count=3
Mixed_Name[0]="Artist 1"
Mixed_Path[0]="/home/me/Music/Artist1Folder/"
Mixed_Name[1]="Artist 2"
Mixed_Path[1]="/home/me/Music/Artist2Folder/"
Mixed_Name[2]="Artist 3"
Mixed_Path[2]="/home/me/Music/Artist3Folder/"
```
Notice that the number in Mixed_Name[x] and Mixed_Path[x] on the new entry is 2 and the next one would be 3 etc.. Also Mixed_Count is now 3 as there are 3 entries now. The same goes for TV_Name[x], TV_Path[x], and TV_Count. But for your purposes you only need one (your song library) in non mixed TV.

Are you understanding this?

EDIT: Also when you get it working the way you want you can change all the TV references to Music if you like :)

---

### Post by inameiname on 2010-06-25
Yeah, I figured that out just fine. I noticed the 'Mixed TV' section wasn't really necessary for me, as I just wanted a random playing of everything in a folder, and it's subfolders. However, it could be handy if ever I want to focus on specific things and folders to play at random.

And I do plan on changing all the 'TV' references to 'Music' or something, I've just been trying to tweak it a little further to remove that '/home/me/Music/.playlists' folder, which I have figured out can be done this way: by opening your script through another script, which includes it and the following after '&&' :

rm -f /home/me/Music/.playlists/MixedTV.plist && rm -f /home/me/Music/.playlists/"My Music Library".plist && rmdir /home/me/Music/.playlists

It'd be cool to implement that in with the tweaked script I gave, but oh well.

I'm still trying to figure out how to be able to right click this script and have it automatically look at whatever folder I randomly right click in, not necessarily the already designated Music folder, such as on an external drive.

---

### Post by VH-BIL on 2010-06-25
you can use zenity to open a GUI file dialog in the bash script and ask where to look for music. Not useful for me in that script but I have sued it in others. Here are some examples:
[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

I looked at removing the playlists but when they are created the write over the old ones so I didn't think it was that much of a problem. Also when someone asks what music you have you can give them that file! (If you don't delete it.

Let me know how you go...

---

### Post by inameiname on 2010-06-25
Oh I just like not having any extra files on my computer if unnecessary. That's why the desire to remove it. I'm a clean freak I guess. hehe.

As for your examples, that is really neat. I'm not sure how that would apply with this script and such, but I could find those examples handy for other things. Thanks. Basically I think finding a folder that way would take too long and be an extra step. If you notice my first posting on this thread, that script does just that, minus the ability to open and handle directories with spaces in it's filename. With it, I can just right click inside whatever folder I want, and voila, it looks for music there, which works great for as a said, I folder on an external hard drive. Whatever, it's cool. 

Thanks again for your assistance tonight. :)

---

### Post by VH-BIL on 2010-06-25
Not a problem glad i could help.

---

### Post by inameiname on 2010-06-25
Here is my good enough version of your script (I spent waaayyyy too much time on it :P):

```

#!/bin/bash
# ================================================================================
#    Project      : Music Shuffle
#    Author       : VH-BIL
#    Date         : 10th Nov 2009
#    Info         :
# The "DestPath" variable holds the path of where to write all the
# playlists.
#
# The variable "MixedDestPath" holds the path and filename for the playlist
# of the mixed Music.
#
# The "Music_Count" variable is then number of individual Music shows to be
# displayed in the menu.
#
# Arrays "Music_Name" and "Music_Path" hold information about the Music shows in
# the menu. "Music_Name" is the name of the Music show and "Music_Path" is the path
# to where all the Music are stored. The number of Music files must
# be recorded in "Music_Count"
#
# The "Mixed_Count" variable is the number of Music files to be put combined
# into the mixed Music playlist.
#
# Just like the "Music_Name" and "Music_Path" variables the "Mixed_Name" and
# Mixed_Path hold the name and file path of the Music files to be in the
# mixed Music playlist.
#
# This is one of the first scripts I have made. I work as a programmer
# but as a C# programmer. I wanted an easy way of playing my Music files shuffled
# while not having to update playlists when adding new .
# ================================================================================

tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; rm -R /home/me/.gnome2/nautilus-scripts/My_Scripts/.playlists/; exit; fi

mkdir /home/me/.gnome2/nautilus-scripts/My_Scripts/.playlists/ && touch /home/me/.gnome2/nautilus-scripts/My_Scripts/.playlists/MixedMusic.plist && touch /home/me/.gnome2/nautilus-scripts/My_Scripts/.playlists/"My Music Library (on PC)".plist && touch /home/me/.gnome2/nautilus-scripts/My_Scripts/.playlists/"My Music Library (on external hard drive)".plist

# The Destination Path Of All The Playlists
DestPath="/home/me/.gnome2/nautilus-scripts/My_Scripts/.playlists/"
# The Path And Filename Of The Mixed Music Playlist
MixedDestPath="/home/me/.gnome2/nautilus-scripts/My_Scripts/.playlists/MixedMusic.plist"

# Colour Codes
black='\E[30;40m'
red='\E[31;40m'
green='\E[32;40m'
yellow='\E[33;40m'
blue='\E[34;40m'
magenta='\E[35;40m'
cyan='\E[36;40m'
white='\E[37;40m'

# My Music Libraries
Music_Count=16
Music_Name[0]="My Music Library (on PC)"
Music_Path[0]="/home/me/Music/"
Music_Name[1]="My Music Library (on external hard drive)"
Music_Path[1]="/media/4B8C73F1515664C1/Backups/Audio/Music/"
Music_Name[2]="80's Collection"
Music_Path[2]="/media/4B8C73F1515664C1/Backups/Audio/Music/80s Collection/"
Music_Name[3]="90's Dance Collection"
Music_Path[3]="/media/4B8C73F1515664C1/Backups/Audio/Music/90's Dance Collection/"
Music_Name[4]="Disney"
Music_Path[4]="/media/4B8C73F1515664C1/Backups/Audio/Music/Disney/"
Music_Name[5]="Rayblac Ultimate Soul Collection"
Music_Path[5]="/media/4B8C73F1515664C1/Backups/Audio/Music/Rayblac Ultimate Soul Collection/"
Music_Name[6]="Ringtones"
Music_Path[6]="/media/4B8C73F1515664C1/Backups/Audio/Music/Ringtones/"
Music_Name[7]="Seth Ellsworth"
Music_Path[7]="/media/4B8C73F1515664C1/Backups/Audio/Music/Seth Ellsworth/"
Music_Name[8]="Seth's Hits"
Music_Path[8]="/media/4B8C73F1515664C1/Backups/Audio/Music/Seth Hits/"
Music_Name[9]="Soundtracks"
Music_Path[9]="/media/4B8C73F1515664C1/Backups/Audio/Music/Soundtracks/"
Music_Name[10]="Thailand Music"
Music_Path[10]="/media/4B8C73F1515664C1/Backups/Audio/Music/Thailand Music/"
Music_Name[11]="The Best Ever Collection"
Music_Path[11]="/media/4B8C73F1515664C1/Backups/Audio/Music/The Best Ever Collection/"
Music_Name[12]="Theme Songs"
Music_Path[12]="/media/4B8C73F1515664C1/Backups/Audio/Music/Theme Songs/"
Music_Name[13]="Travis's Hits"
Music_Path[13]="/media/4B8C73F1515664C1/Backups/Audio/Music/Travis Hits/"
Music_Name[14]="Unknown Artist"
Music_Path[14]="/media/4B8C73F1515664C1/Backups/Audio/Music/Unknown Artist/"
Music_Name[15]="Various Artists"
Music_Path[15]="/media/4B8C73F1515664C1/Backups/Audio/Music/Various Artists/"


# Mixed Music
Mixed_Count=2
Mixed_Name[0]="My Music Library (on PC)"
Mixed_Path[0]="/home/me/Music/"
Mixed_Name[1]="My Music Library (on external hard drive)"
Mixed_Path[1]="/media/4B8C73F1515664C1/Backups/Audio/Music/"


DisplayMenu()
{
  echo -en $white
  clear
  echo -en $white
  echo "Music Shuffle Script"
  echo -en $red
  echo "================="
  echo
  for ((cnt=0 ; cnt<=Music_Count-1 ; cnt++))
  do
    if [ $cnt -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo ${Music_Name[cnt]}
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo ${Music_Name[cnt]}
    fi
  done
    if [ $Music_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $Music_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Mixed Music"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $Music_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Mixed Music"
    fi
    let "Music_Count += 1"
    if [ $Music_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $Music_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Display Mixed Music"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $Music_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Display Mixed Music"
    fi
    let "Music_Count -= 1"
  echo
  echo -n "Make A Selection :"
}

DisplayMixedMusic()
{
  echo
  for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    echo -en $white
    echo ${Mixed_Name[cnt]}
  done
  echo
}

ShuffleEpisode()
{
  cd /
  find "${Music_Path[$1]}" > "$DestPath${Music_Name[$1]}.plist"
  mplayer -playlist "$DestPath${Music_Name[$1]}.plist" -shuffle
}

MixedMusic()
{
  echo "" > $MixedDestPath
  cd /
    for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    find "${Mixed_Path[$cnt]}" > "$DestPath${Mixed_Name[$cnt]}.plist"
    echo "" > $MixedDestPath"_cat"
    cat "$DestPath${Mixed_Name[$cnt]}.plist" $MixedDestPath > $MixedDestPath"_cat"
    rm $MixedDestPath
    mv $MixedDestPath"_cat" $MixedDestPath
  done
  mplayer -playlist $MixedDestPath -shuffle
}

DisplayMenu
read input

if [ $input -eq $Music_Count ]
then
  MixedMusic
fi

let "Music_Count += 1"
if [ $input -eq $Music_Count ]
then
  DisplayMixedMusic
fi
let "Music_Count -= 1"

if [ $input -lt $Music_Count ]
then
  ShuffleEpisode $input
fi

```I decided to just add the directory for my external hard drive as a way to get around the inability to merely right click and read all the music that's in the current folder. It works, good enough. However, I'll have to tweak this and add new directories if and when I try another hard drive, and/or the path changes for my external hard drive. 

I also figured out where to put that 'rm' function to rid myself of that '/.playlists/' folder, which I put where I added that little bit of script to enable it to open directly in the terminal.

Also, I did notice how cool it is to have that '/.playlists/' document that tells me all the files (music files) under the choice I choose in the menu. I just copied and pasted my external hard drive's main directory file list elsewhere just to save it once, so I can check it out if need be and not have to have it delete itself every time I close it, since that's what I set it up to do. Mine's like 5.7 mb! Lots of music. Hehe. Plus, a benefit of it is I can do a search through gedit for a song to see if I have it. That's pretty easy.

I'm gonna mark this as solved because I figure if I spent this much time on it, and it works well enough, I'm not gonna want to find something else. Thanks again.

---

### Post by VH-BIL on 2010-06-25
Im glad my script came in handy. You should add a new line under Author and call it Edited By: or something as you have done well!

Is there a reason you wanted a script and not use a program like songbird? I was just wondering...

---

### Post by Binns on 2011-06-27
ok so this thread is old but im using the "Music Shuffle" script and it wont put music in the playlist.
everything else works because iv made a different playlist and inserted it in the text instead.
and @ op i used your original script along with the shuffle input script from "Music Shuffle"
it works like it should.
im going to use it on a flash drive, with tiny core, set to autostart.

iv changed a lot of the Music Shuffle script btw.
i don't know how to add the scroll box for post and don't want to paste it all here. id like to use the "Music shuffle" script on my desktop, linux mint so hopefully one of you can help out

:guitar:

---

### Post by nothingspecial on 2011-06-27
You click the # at the top of the post box and paste the text in between.

By the way, if I want my Music to play randomly I just go

```
mplayer -quiet -shuffle -playlist <(find -L ~/Music -type f)
```

Don't worry about the -quiet option, that just suppresses the error message when mplayer encounters an artwork file.

---

### Post by inameiname on 2011-06-28
To VH-BIL:

> **VH-BIL said:**
> Im glad my script came in handy. You should add a new line under Author and call it Edited By: or something as you have done well!

Is there a reason you wanted a script and not use a program like songbird? I was just wondering...


I'm a bit late on responding to you here, but I just wanted to say I've used this script for a year now and it all works fine. Thanks again. And as for not using a program like songbird, I figure a simple script in my nautilus-scripts folder is good enough for the times I want to do this as opposed to installing an entire program solely for this.


To Binns:

When you get your script all finished to your liking, could you post it here? I'm just curious what sort of things you have changed, as you never know what might be better or worse as far as updating mine.


To nothingspecial:

Nice command. I tweaked it a small bit so it works as a nautilus script. Technically, yours is what I initially wanted when I created this thread; the other is very cool, but it does force you to have preset paths in it before you run it. Anyway, what it does now is let you right click a folder and have it randomly play anything Mplayer can handle (video/audio) found inside that folder (including stuff inside subfolders):

```

#!/bin/bash

# Random-Music-In-Mplayer.sh
# Creator: Inameiname
# Initial Command Creator: nothingspecial
# Version: 1.0
#
# Requires mplayer: sudo apt-get install mplayer
#
# Directions:
# - Put this script inside your ~/.gnome/nautilus-scripts folder
# - Once inside your nautilus-scripts folder, it can be run one of two ways:
# - 1. - right click any folder and it will automatically randomly play any music/video inside it
# - 2. - open a terminal window and enter: ./path/to/Random-Music-In-Mplayer.sh /path/to/main/music/folder


# Set IFS so that it won't consider spaces as entry separators.
# Without this, spaces in file/folder names can make the loop go wacky.
IFS=$'\n'

# See if the Nautilus environment variable is empty
if [ -z $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
    # If it's blank, set it equal to $1
    NAUTILUS_SCRIPT_SELECTED_FILE_PATHS=$1
fi

# Loop through the list (from either Nautilus or the command line)
for ARCHIVE_FULLPATH in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*}
    FILENAME=${ARCHIVE_FULLPATH##*/}
    NAME=${ARCHIVE_FULLPATH##*/.*}

    # open a terminal window and run the important stuff
    tty -s; if [ $? -ne 0 ] ; then gnome-terminal -e "$0"; exit; fi
    mplayer -loop 0 -quiet -shuffle -playlist <(find -L $ARCHIVE_FULLPATH -type f | egrep -i '(\.mp3|\.wav|\.flac|\.ogg|\.m4a|\.aac|\.mpa|\.mid|\.aif|\.iff|\.m3u|\.ra)')

done

```

I do have one question regarding that command you gave.....could you exclude it from playing certain file types and/or have it only play certain file types (for instance, if you have a folder with both '.avi' and '.mp3' files, can you exclude the '.avi' ones)?

UPDATE: 

Playing around with things, you can technically combine the two scripts, and make one that will work for any folder you want thats selected OR if no folder is selected, default to the presets and the menu from the first script:

```

#!/bin/bash

# Random-Music.sh
# Creator: Inameiname
# Initial Command Creator: nothingspecial
# Original 'Music Shuffle' Creator: VH-BIL & Me
# Version: 1.0
#
# Requires mplayer: sudo apt-get install mplayer
#
# Directions:
# - Put this script inside your ~/.gnome/nautilus-scripts folder
# - Once inside your nautilus-scripts folder, it can be run one of two ways:
# - 1. - right click any folder and it will automatically randomly play any music/video inside it
# - 2. - if nothing is selected when running the script, it will default to this script's preset locations


# Set IFS so that it won't consider spaces as entry separators.
# Without this, spaces in file/folder names can make the loop go wacky.
IFS=$'\n'

# See if the Nautilus environment variable is empty
if [ -z $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS ]; then
    # ================================================================================
    #    Project      : Music Shuffle
    #    Author       : VH-BIL & Me
    #    Date         : 10th Nov 2009 & 9th Sep 2010
    #    Info         :
    # The "DestPath" variable holds the path of where to write all the
    # playlists.
    #
    # The variable "MixedDestPath" holds the path and filename for the playlist
    # of the mixed Music.
    #
    # The "Music_Count" variable is then number of individual Music files to be
    # displayed in the menu.
    #
    # Arrays "Music_Name" and "Music_Path" hold information about the Music files in
    # the menu. "Music_Name" is the name of the Music file and "Music_Path" is the path
    # to where all the Music is stored. The number of Music files must
    # be recorded in "Music_Count"
    #
    # The "Mixed_Count" variable is the number of Music files to be put combined
    # into the mixed Music playlist.
    #
    # Just like the "Music_Name" and "Music_Path" variables the "Mixed_Name" and
    # Mixed_Path hold the name and file path of the Music files to be in the
    # mixed Music playlist.
    #
    # This is one of the first scripts I have made. I work as a programmer
    # but as a C# programmer. I wanted an easy way of playing my Music files shuffled
    # while not having to update playlists when adding new .
    # ================================================================================

    tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; rm -R $HOME/.gnome2/nautilus-scripts/My_Scripts/.playlists/; exit; fi

    # The Destination Path Of All The Playlists
    DestPath="$HOME/.gnome2/nautilus-scripts/My_Scripts/.playlists/"
    # The Path And Filename Of The Mixed Music Playlist
    MixedDestPath="$HOME/.gnome2/nautilus-scripts/My_Scripts/.playlists/MixedMusic.plist"

    mkdir $DestPath && touch $HOME/.gnome2/nautilus-scripts/My_Scripts/.playlists/MixedMusic.plist && touch $HOME/.gnome2/nautilus-scripts/My_Scripts/.playlists/"My Music Library (on PC)".plist && touch $HOME/.gnome2/nautilus-scripts/My_Scripts/.playlists/"My Music Library (on external hard drive)".plist

    # Colour Codes
    black='\E[30;40m'
    red='\E[31;40m'
    green='\E[32;40m'
    yellow='\E[33;40m'
    blue='\E[34;40m'
    magenta='\E[35;40m'
    cyan='\E[36;40m'
    white='\E[37;40m'

    # My Music Libraries
    Music_Count=16
    Music_Name[0]="My Music Library (on PC)"
    Music_Path[0]="$HOME/Music/"
    Music_Name[1]="My Music Library (on external hard drive)"
    Music_Path[1]="/media/5DE90B7115F542AE/Backups/Audio/Music/"
    Music_Name[2]="80's Collection"
    Music_Path[2]="/media/5DE90B7115F542AE/Backups/Audio/Music/80s Collection/"
    Music_Name[3]="90's Dance Collection"
    Music_Path[3]="/media/5DE90B7115F542AE/Backups/Audio/Music/90's Dance Collection/"
    Music_Name[4]="Disney"
    Music_Path[4]="/media/5DE90B7115F542AE/Backups/Audio/Music/Disney/"
    Music_Name[5]="Rayblac Ultimate Soul Collection"
    Music_Path[5]="/media/5DE90B7115F542AE/Backups/Audio/Music/Rayblac Ultimate Soul Collection/"
    Music_Name[6]="Ringtones"
    Music_Path[6]="/media/5DE90B7115F542AE/Backups/Audio/Music/Ringtones/"
    Music_Name[7]="Seth Ellsworth"
    Music_Path[7]="/media/5DE90B7115F542AE/Backups/Audio/Music/Seth Ellsworth/"
    Music_Name[8]="Seth's Hits"
    Music_Path[8]="/media/5DE90B7115F542AE/Backups/Audio/Music/Seth Hits/"
    Music_Name[9]="Soundtracks"
    Music_Path[9]="/media/5DE90B7115F542AE/Backups/Audio/Music/Soundtracks/"
    Music_Name[10]="Thailand Music"
    Music_Path[10]="/media/5DE90B7115F542AE/Backups/Audio/Music/Thailand Music/"
    Music_Name[11]="The Best Ever Collection"
    Music_Path[11]="/media/5DE90B7115F542AE/Backups/Audio/Music/The Best Ever Collection/"
    Music_Name[12]="Theme Songs"
    Music_Path[12]="/media/5DE90B7115F542AE/Backups/Audio/Music/Theme Songs/"
    Music_Name[13]="Travis's Hits"
    Music_Path[13]="/media/5DE90B7115F542AE/Backups/Audio/Music/Travis Hits/"
    Music_Name[14]="Unknown Artist"
    Music_Path[14]="/media/5DE90B7115F542AE/Backups/Audio/Music/Unknown Artist/"
    Music_Name[15]="Various Artists"
    Music_Path[15]="/media/5DE90B7115F542AE/Backups/Audio/Music/Various Artists/"


    # Mixed Music
    Mixed_Count=2
    Mixed_Name[0]="My Music Library (on PC)"
    Mixed_Path[0]="$HOME/Music/"
    Mixed_Name[1]="My Music Library (on external hard drive)"
    Mixed_Path[1]="/media/5DE90B7115F542AE/Backups/Audio/Music/"


    DisplayMenu()
    {
      echo -en $white
      clear
      echo -en $white
      echo "Music Shuffle Script"
      echo -en $red
      echo "================="
      echo
      for ((cnt=0 ; cnt<=Music_Count-1 ; cnt++))
      do
        if [ $cnt -lt 10 ]
        then
          echo -en $cyan
          echo -n "("
          echo -en $blue
          echo -n $cnt
          echo -en $cyan
          echo -n ")  "
          echo -en $white
          echo ${Music_Name[cnt]}
        else
          echo -en $cyan
          echo -n "("
          echo -en $blue
          echo -n $cnt
          echo -en $cyan
          echo -n ") "
          echo -en $white
          echo ${Music_Name[cnt]}
        fi
      done
        if [ $Music_Count -lt 10 ]
        then
          echo -en $cyan
          echo -n "("
          echo -en $blue
          echo -n $Music_Count
          echo -en $cyan
          echo -n ")  "
          echo -en $white
          echo "Mixed Music"
        else
          echo -en $cyan
          echo -n "("
          echo -en $blue
          echo -n $Music_Count
          echo -en $cyan
          echo -n ") "
          echo -en $white
          echo "Mixed Music"
        fi
        let "Music_Count += 1"
        if [ $Music_Count -lt 10 ]
        then
          echo -en $cyan
          echo -n "("
          echo -en $blue
          echo -n $Music_Count
          echo -en $cyan
          echo -n ")  "
          echo -en $white
          echo "Display Mixed Music"
        else
          echo -en $cyan
          echo -n "("
          echo -en $blue
          echo -n $Music_Count
          echo -en $cyan
          echo -n ") "
          echo -en $white
          echo "Display Mixed Music"
        fi
        let "Music_Count -= 1"
      echo
      echo -n "Make A Selection :"
    }

    DisplayMixedMusic()
    {
      echo
      for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
      do
        echo -en $white
        echo ${Mixed_Name[cnt]}
      done
      echo
    }

    ShuffleEpisode()
    {
      cd /
      find "${Music_Path[$1]}" > "$DestPath${Music_Name[$1]}.plist"
      mplayer -playlist "$DestPath${Music_Name[$1]}.plist" -shuffle
    }

    MixedMusic()
    {
      echo "" > $MixedDestPath
      cd /
        for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
      do
        find "${Mixed_Path[$cnt]}" > "$DestPath${Mixed_Name[$cnt]}.plist"
        echo "" > $MixedDestPath"_cat"
        cat "$DestPath${Mixed_Name[$cnt]}.plist" $MixedDestPath > $MixedDestPath"_cat"
        rm $MixedDestPath
        mv $MixedDestPath"_cat" $MixedDestPath
      done
      mplayer -playlist $MixedDestPath -shuffle
    }

    DisplayMenu
    read input

    if [ $input -eq $Music_Count ]
    then
      MixedMusic
    fi

    let "Music_Count += 1"
    if [ $input -eq $Music_Count ]
    then
      DisplayMixedMusic
    fi
    let "Music_Count -= 1"

    if [ $input -lt $Music_Count ]
    then
      ShuffleEpisode $input
    fi
fi

# Loop through the list (from either Nautilus or the command line)
for ARCHIVE_FULLPATH in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    NEWDIRNAME=${ARCHIVE_FULLPATH%.*}
    FILENAME=${ARCHIVE_FULLPATH##*/}
    NAME=${ARCHIVE_FULLPATH##*/.*}

    # open a terminal window and run the important stuff
    tty -s; if [ $? -ne 0 ] ; then gnome-terminal -e "$0"; exit; fi
    mplayer -loop 0 -quiet -shuffle -playlist <(find -L $ARCHIVE_FULLPATH -type f | egrep -i '(\.mp3|\.wav|\.flac|\.ogg|\.m4a|\.aac|\.mpa|\.mid|\.aif|\.iff|\.m3u|\.ra)')

done

```

UPDATE 2:

I updated the scripts to reflect the changes below.

---

### Post by nothingspecial on 2011-06-28
> **inameiname said:**
> ]I do have one question regarding that command you gave.....could you exclude it from playing certain file types and/or have it only play certain file types (for instance, if you have a folder with both '.avi' and '.mp3' files, can you exclude the '.avi' ones)?

Sure,

```
mplayer -quiet -shuffle -playlist <(find -L ~/Music -type f -name *.mp3)
```

And you can do it more simply if your Music folder is properley organised (which mine is not). If your Music folder is strictly ~/Music/Artist/Album/song.mp3 , then this will do

```
mplayer -shuffle Music/*/*/*.mp3
``` 

No need to use find.

---

### Post by inameiname on 2011-06-28
True. Your last method would be the easiest, but requires a highly organized folder. You'd also have to ensure each and every time you set folder as the main one its the right one; otherwise you'd be off a folder and wouldn't have the correct path. No matter. the first method works just fine. Thank you.

Using what I know of the 'find' command, I figured out that you can further tweak it to look for more than just '.mp3' file types (also added was a loop option):

```

mplayer -loop 0 -quiet -shuffle -playlist <(find -L ~/Music -type f | egrep -i '(\.mp3|\.wav|\.flac|\.ogg|\.m4a|\.aac|\.mpa|\.mid|\.aif|\.iff|\.m3u|\.ra)')

```

Using this, I updated the scripts above, and everything seems to work perfectly. Again, thanks.

---

