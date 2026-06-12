---
title: "A Bash Script to Organize Music"
date: 2010-10-16
forum: General Help
---

### Post by secretformula on 2010-10-16
I currently I have ton of music mp3 that are all sitting in one directory. They are all ID3 tagger properly. I want to put all those mp3's into folders based on {artist}/{album}/song.mp3 using the data from the ID3 tag. I made the following bash script.
```
#!/bin/bash

#Renames and organizes your music data.
#Provide the full path of your source music folder as an argument.
#Renames music files according to its metadata  in format "Track - Title - Album - Artist". 
#Creates a directory in the target folder with Artist name and stores file in it.


if [ -z "$1" ];then #setting default directory
	cd /media/CrossOS/Media/Music
else	
	cd "$1"
fi

target_dir='/media/CrossOS/Media/Music'

for F in ./*.mp3 #change this line to 'for F in ./*' if you have files other than mp3 format
do
	if [ -f "$F" ];then
		# Get metadata
		track=`mminfo "$F"|grep track|awk -F: '{print $2}'`
		track=${track:1}	
		artist=`mminfo "$F"|grep artist|awk -F: '{print $2}'`
		artist=${artist:1}
		title=`mminfo "$F"|grep title|awk -F: '{print $2}'`
		title=${title:1}
		album=`mminfo "$F"|grep album|awk -F: '{print $2}'`
		album=${album:1}
			if [  -n "$artist"  ] && [  -n "$title"  ] && [ -n "$album" ];then
				filename="$track - $title - $album - $artist.mp3";echo $filename
				cp "$F" "$filename"  #renaming the file(copy)
					if [ -d "$target_dir/$artist/$album" ];then    #moving file to the artist folder
						mv "$filename" "$target_dir/$artist/$album"  
					else 
						if [ -d "$target_dir/$artist" ];then
							mkdir "$target_dir/$artist/$album"
							mv "$filename" "$target_dir/$artist/$album"
						else
							mkdir "$target_dir/$artist"
							mkdir "$target_dir/$artist/$album"
							mv "$filename" "$target_dir/$artist/$album"
						fi
					fi
			else
				echo -e "Skipping b/c insufficient metadata: $F \n"
			fi
	fi
done
```
It works OK but when I start with 1509 songs when im finished the script ends up with ~1300. I'm thinking I have some sort of logic error however I cant find it. Can anybody recommend how to fix the script or an alternative program that does what I want?

---

### Post by cinohpa on 2010-10-16
That's a cool idea. I am a big fan. Don't throw away your homegrown script! Debug it!

So... my first questions are how did you get those numbers of 1500~ -> 1300~?

Also, are you capturing the script output anywhere? Are you getting any errors? 

Are you 100% sure there are no duplicates in your collection and no way your script would try to create distinct files that would end up with the same name?

---

### Post by secretformula on 2010-10-16
Yea i'm 100% sure I have no duplicates. Capturing output would probably be a good idea. Right now the method i'm using to get the data from the mp3's says its depreciated but it still works...

---

### Post by shingalated on 2010-12-27
It seems like it may not be working on files which have certain characters in the ID3 tags that are not allowed in file names.

---

### Post by thewump on 2011-01-29
Hey Secretformula, I took your code and messed with it and then messed with it some more and now I have what I think is a pretty good script!

I've packaged it up so it works as a post processing script for sabnzbd, but you can use it for anything.

1) It assumes your music is in ~/Music but you can change it
2) By default it makes a COPY of music, but you can change that

So.. save this as ~/mp3organizer
chmod +x mp3organizer

If you want to reogranize all your music collection, then best thing to do is:

```

move ~/Music ~/old_music
./mp3organizer ~/old_music

```

This will create a new ~/Music directory but you'll still have your "old_music" as is with no risk of loss.

For general use, when you get new music:
1) In the file change from mode="copy" to mode="move"
2) Put new music in ~/new_music
3) run ./mp3organizer ~/new_music

As a bonus, this removes duplicates.

```

#!/bin/bash


# Where is your music collection?  Where should all music be organized to?
music_collection="$HOME/Music" 


# SABNZBD usage
# 1) Edit music_collection setting above if your music isn't in the "normal" place
# 2) Set this up as an SABNZBD Post Processing script

# GENERAL usage
# 1) Edit music_collection setting above if your music isn't in the "normal" place
# 2) run in a terminal as: ./mp3organizer /path_to/where_the_new_music_files/are 
# Note that the path can't have any spaces.

# NOTES AND ADVANCED USAGE
# File with bad tags are stored to /[Your_music_collection]/unknown

# See the Advanced Options settings if you want to:
# a) Make backup copies
# b) Move instead of copy file from the new music location

# =============================================================================================
# ADVANCED / OPTIONAL SETTINGS
# Want all the files copied somewhere else too? 
#backup_dir="$HOME/mp3organizer_backups"

# Set to "copy" or "move" to make the script either copy files to your music collection and leave
# the originals where they were or move them to your music collection.
mode="copy"

# If you want the unknown files to be saved somewhere else, or to change where this script
# keeps temporary files, change these:
unknown_dir="$music_collection/unknown" 
working_dir="$HOME/.mp3organizer_temporary_files"


# =============================================================================================
# EVERYTHING BELOW HERE IS AS IT SHOULD BE. DONT MESS WITH IT

# Make sure that a folder has been passed to the script
if [ -z "$1" ];then
  echo "Doh!  You have to pass a directory where the music is you want to organize!"
  exit
else	
  echo "Working from supplied directory"
  echo "$1"
	new_music="$1"
fi

# Make sure if a folder has been passed that it actuall exists
if [ ! -d "$new_music" ];then    
  echo "Can't find the search directory $new_music"
  echo "For SABNZBD, in the admin go to Settings > Switches and set REPLACE SPACES WITH UNDERSCORSES"
  exit
fi

# Check other folders exist and make them if necessary
if [ ! -d "$working_dir" ];then    
  echo "Creating $working_dir"
  mkdir $working_dir
fi

if [ ! -d "$music_collection" ];then    
  echo "Creating $music_collection"
  mkdir $music_collection
fi

if [ ! -d "$unknown_dir" ];then    
  echo "Creating $unknown_dir"
  mkdir $unknown_dir
fi

if [ ! -d "$backup_dir" ];then    
  echo "Creating $backup_dir"
  mkdir $backup_dir
fi

# Copy or Move the new music files to our temporary working area to be processed
if [ "$mode" = 'move' ]; then
  find $new_music -iname "*.mp3" -exec mv {} $working_dir \;
else
  find $new_music -iname "*.mp3" -exec cp {} $working_dir \;
fi

cd $working_dir

# Work on each file one at a time
for F in ./*
do
	if [ -f "$F" ];then				
    # use mminfo to get the track info
    # LOTS of stuff going on here. Have to remove leading space, special chars and pad track to 0x etc.
    # Someone smart could do this a lot more elegantly than this!
		artist=`mminfo "$F"|grep artist|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_]//g'`
		title=`mminfo "$F"|grep title|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_]//g'`
		album=`mminfo "$F"|grep album|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_]//g'`
		trackno=`mminfo "$F"|grep trackno|awk -F: '{print $2}'|sed 's/^ *//g'| awk '{printf "%02d\n", $1;}'`

	  echo "============================"
		echo "artist:" $artist
		echo "title:" $title
		echo "album:" $album
		echo "trackno:" $trackno

      # If we have an artist, album and title then we know where to nicely put this file
			if [  -n "$artist"  ] && [ -n "$album" ] && [  -n "$title"  ];then
          # This is what we are going to call the file
  				filename="$trackno - $title.mp3"; 
			  	if [ -n  "$backup_dir" ];then
			          cp "$F" "$backup_dir/"
				  fi
  				# If the right directory structure exists - awesome. Move the file.
					if [ -d "$music_collection/$artist/$album" ];then    
						mv "$F" "$music_collection/$artist/$album/$filename"  
					else
					  # If not, build the whole file structure. Won't do any harm to try and create an artist directory that
					  # is already there - so not even checking for that.
						mkdir "$music_collection/$artist"
						mkdir "$music_collection/$artist/$album"
						mv "$F" "$music_collection/$artist/$album/$filename"
					fi
			else
        # Don't know who it's by, what album, or what track, so moving it to UNKNOWN
  			mv "$F" "$unknown_dir/"
				echo -e "UNKNOWN: $F \n"
			fi
	fi
done

```

Anyone know GUI work?  Would be cool to have this as a simple application.  I can't believe it doesn't exist as a feature outside of music players.

K

---

### Post by carleton on 2012-07-29
Huge kudos, TheWump. Your script is exactly what I've wanted to have for awhile. It's really clean and concise and gets the job done. :guitar:

I don't know if you're still working on it at all, but would it be possible to modify the script so that:

1. It worked with non-MP3s (FLAC, etc)
2. The music source path was able to contain spaces

Regardless, thanks again.

---

### Post by Vaphell on 2012-07-29
2. should be easy - just find and double-quote all path related variables, there are few unquoted instances, eg
```
mkdir [COLOR="Blue"]"[/COLOR]$music_collection[COLOR="Blue"]"[/COLOR]
```

1. is trivial, you just need to find a program that can read flac metadata and add little *if then else* to the script. I don't have a single flac so i can't investigate it further.

---

### Post by wildmanne39 on 2012-07-30
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

