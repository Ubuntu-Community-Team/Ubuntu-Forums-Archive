---
title: "Script to randomly play music in my music folder?"
date: 2010-06-16
forum: General Help
---

### Post by inameiname on 2010-06-16
I have a basic script to play music in my music folder, but the problem is it will only play music in ~/Music and not in any of the subfolders in my Music folder:

#! /bin/bash
cd ~/Music
totem *.mp3

How can I include mp3s in subfolders?

Also, what can I add to this script to include .wav, .ogg, and other audio formats as well?

---

### Post by gzarkadas on 2010-06-17
Use `locate ~/Music/*.mp3' to find your files (you can append additional files as extra arguments, like `locate ~/Music/*.mp3 ~/Music/*.wav ~/Music/*.ogg'):

```

totem $(locate ~/Music/*.mp3 ~/Music/*.wav ~/Music/*.ogg)

```To shuffle files, pipe the output of locate to the `shuf' command. 
```

totem $(locate ~/Music/*.mp3 ~/Music/*.wav ~/Music/*.ogg | shuf)

```

---

### Post by inameiname on 2010-06-23
Thanks for the suggestion, but unfortunately it doesn't seem to work for me.

---

### Post by wilee-nilee on 2010-06-23
If you want it to just happen use a player like rhythmbox. If your just trying to figure out scripts then carry on.

---

### Post by inameiname on 2010-06-23
Rhythmbox works, but I was hopefully to make it as easy as right clicking, going to nautilus-scripts, and then clicking a script that'll automatically open the movie player and randomly play something in that folder. No muss, no fuss.

---

### Post by dino99 on 2010-06-23
maybe you might discover "radio tray" :p

---

### Post by inameiname on 2010-06-24
Oh I have. I love Radiotray. Even have a souped up list with hundreds of stations. It was actually Radiotray that prompted my idea of something similar with music in a local folder.

---

### Post by gzarkadas on 2010-06-24
> **inameiname said:**
> Rhythmbox works, but I was hopefully to make it as easy as right clicking, going to nautilus-scripts, and then clicking a script that'll automatically open the movie player and randomly play something in that folder. No muss, no fuss.

This is a bit different than the first post's specs :). Try this one; it plays a list of all files with wanted formats in a selection of directories (at the top level only).  
```

#!/bin/bash
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
totem $(ls ${PLAYLIST} | ${SHUFCMD})

```Copy the code in a file somewhere, set its x bit and then in `nautilus-actions' settings dialog you should set specific values in the following key-fields:

Tab `Action', Field `Path': <the-path-to-the-script>
Tab `Action', Field `Parameters': `100 %M'
(you can adjust the 100 which is the size of the playlist to any number you like, or '' for unlimited)
Tab `Conditions', Field `Filenames': `*'
Tab `Conditions', Field `Appears if Selection Contains': `Folders Only'
Tab `Conditions', Field `Appears if Selection has Multiple...': checked

---

### Post by inameiname on 2010-06-24
Oh wow, thanks a lot for all of that. I'll check it out and get back with you. :) If it works I think I'll just stick it in my nautilus-scripts folder instead of using nautilus-actions, as that's where I have all of my user-made scripts that I use on occasion and whatnot. Plus, it won't clutter my right click's main menu. But thanks for how.

---

### Post by inameiname on 2010-06-24
Ok, so using your script, I noticed a few things:

...it works great, however, as it is  now, it only seems to work if it was in the very folder (or in  nautilus-scripts and I right clicked it from the very folder) it was  looking for the music, such as in ~/Music, and then what it did was read  all of the subfolders on the first tier in there, and then all the  subfolders in those for music. 

I figured out that by adding, cd ~/Music, it enables it to be  right clicked anywhere and opens music only from the ~/Music folder it  can be used. 

However, one thing that's odd  is if the subfolder in ~/Music folder has a 'space' in it's title, (ie,  ~/Music/Green Day), it would fail. This is not the case for subfolders  of the first tier subfolders in ~/Music though, (ie, ~/Music/Jazz/Simply  Red). 

Anybody know how to fix this?
 
Also, another issue that this script does is that while the folders are  played at random, (ie  ~/Music/Jazz/Simply Red plays first, then ~/Music/Jazz/Astronaut Jives  plays second, ~/Music/Jazz/Cornholio third, ~/Music/Jazz/Beck fourth,  and etc.), the tracks/songs within each folder is played in order, (ie.,  1.mp3, 2.mp3, 3.mp3, 4.mp3, and etc.).                                                                                                                   

Is there a way to randomize the order of the songs within the folders  too?

---

### Post by inameiname on 2010-06-25
Ok so getting another similar script by another user on here, I was able to make another script that seems to work which I'll share here:

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

```

(I spent waaaaayyy too much time on this :P) 

Anyway, I decided to just add the directory for my external hard drive as a way  to get around the inability of this script to be able to merely right click and read all the music  that's in the current folder. It works, good enough. However, I'll have  to tweak this and add new directories if and when I try another hard  drive, and/or the path changes for my external hard drive. 

Basically, yours was much simpler, but this works and has a nifty little menu and gives you lots of info while playing that's kind of cool.

Also, there is a cool thing that this does which automatically lists all the songs in the directory in a text format. Very nice if you want to do a quick search for an artist or song or something. And while I have it set to delete that after closing the script, I just copied and pasted it from the main directory and saved it elsewhere for later perusal. Mine's like 5.7 mb! Lots of music. Hehe. 

I'm gonna mark this as solved because I figure if I spent this much time  on it, and it works well enough, I'm not gonna want to find something  else. :P Nah, I mean if you know of how to tweak yours that's be great too. Then I'll have to see which is best for me. 

Thanks again.

---

