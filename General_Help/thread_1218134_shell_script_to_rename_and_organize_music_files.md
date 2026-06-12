---
title: "shell script to rename and organize music files"
date: 2009-07-20
forum: General Help
---

### Post by abhigyan91 on 2009-07-20
hey every1.. plz look at the following code i wrote for organizing music files(the way itunes does in windows)

```

#!/bin/bash -x


#Renames and organizes your music data.
#Provide the full path of your music folder as an argument.
#Renames music files according to its metadata  in format "Artist - Title". 
#Creates a folder with Artist name and stores file in it.


if [ -z $1 ];then #setting default directory
	cd /home/abhigyan/Desktop/testing
else	
	cd $1
fi

for F in ./*
do
	if [ -f "$F" ];then
		artist=`mminfo $F|grep artist|awk -F: '{print $2}'` #getting metadata
		chkartist=$? ;echo $artist
		title=`mminfo $F|grep title|awk -F: '{print $2}'`
		chktitle=$? ;echo $title
			if [  $chkartist -eq 0  ] || [  $chktitle -eq 0  ];then
				filename="$artist - $title"
				mv "$F" /tmp/"$filename"
					if [ -d $artist ];then #moving file to the artist folder
						mv /tmp/"$filename" "./$artist"  
					else
						mkdir $artist
						mv /tmp/"$filename" "./$artist"
					fi
			else
				echo -e "Skipping b/c insufficient metadata: $F \n"
			fi
	fi
done

```

this code deletes all files in the directory except the last file.. which is renamed "-". I don' tknow what the problem is but i think it is a logical error. I had tried to write a python script (which renames the files not organizes them into folders) and i get the same exact problem
so it must be a logical error.. If you want to look at the python code plz refer to [this page]("http://www.unix.com/shell-programming-scripting/114736-downsizing-strings-returned-grep-3.html#post302335582")

plz help me understand what the problem is. Thanks in advance!!

---

### Post by abhigyan91 on 2009-07-22
ok guys the prob was that i was changing the files in the folder itself so the loop was getting messed up.. i reworte it using a souce dir and a target dir and it worked like a charm..w00t

```

#!/bin/bash -x


#Renames and organizes your music data.
#Provide the full path of your source music folder as an argument.
#Renames music files according to its metadata  in format "Artist - Title". 
#Creates a directory in the target folder with Artist name and stores file in it.


if [ -z "$1" ];then #setting default directory
	cd /home/abhigyan/Desktop/source
else	
	cd "$1"
fi

target_dir='/home/abhigyan/Desktop/target'

for F in ./*.mp3 #change this line to 'for F in ./*' if you have files other than mp3 format
do
	if [ -f "$F" ];then				
		artist=`mminfo "$F"|grep artist|awk -F: '{print $2}'` #getting metadata
		title=`mminfo "$F"|grep title|awk -F: '{print $2}'`
			if [  -n "$artist"  ] && [  -n "$title"  ];then
				filename="$artist - $title.mp3";#echo $filename
				cp "$F" "$filename"  #renaming the file(copy)
					if [ -d "$target_dir/$artist" ];then    #moving file to the artist folder
						mv "$filename" "$target_dir/$artist"  
					else
						mkdir "$target_dir/$artist"
						mv "$filename" "$target_dir/$artist"
					fi
			else
				echo -e "Skipping b/c insufficient metadata: $F \n"
			fi
	fi
done

```

---

### Post by eaidoido on 2009-12-25
*bump 

your script works well. it does exactly what I had hoped. however, one minor irritating detail is that it puts a space character before each file name and it's enclosing folder. 

you haven't specified any space character. I'm not sure why this is happening? any ideas?

---

### Post by swaroopkumar on 2010-11-15
Hi abhigyan91,
There is no mminfo command in my system, I couldn't find it in synaptic too. Can you please let me know where i can get that package.

Thanks in advance.
Swaroop

---

### Post by thewump on 2011-01-15
Hey,

I took your script as a starting point and here it is taken to the next level. I'm not a bash script genius so I'm sure there are parts of this that are clunky, but it works well.

Enhancments include:

- removal of leading space in variable names
- removed all but alphanumeric, space, - and _ from text
- variablized so it's more generic.
- added (padded) track number to the file name.
- any mp3 that doesn't have usable md5 info it puts in a directory called "unknown"
- checks for / autocreates direcorties as needed

So now you get:

/artist/album/## - title.mp3

I ran this on 100gigs of music and it worked perfectly. The reason I built it though is to automatically run it on new music I get, and add add that in to the library.  

```
#!/bin/bash

# OVERVIEW
# Takes all the mp3 files it can find in a specified search directory then
# moves or copies them to a working directory, then using the embedded file tags
# moves them to the target directory in the structure /artist/album/## - trackname
#
# Unrecognized files are stored in an "unknown" directory.
# This is completely MP3 specific.. Will ignore other music files, but easy to modify to support them.

# version 1.0

# First setup some directory variables
working_dir="$HOME/tmp" # Somewhere that the script is going to collect the files before processing them
target_dir="$HOME/New_Music" # Don't make it the same as search_dir or things could get messy
unknown_dir="$target_dir/unknown" # Where to put files that don't have good meta data. 

# Allow a search directory to be passed in the command line
if [ -z "$1" ];then
  search_dir="$HOME/Music" # DEFAULT. Change this to match where you want to look for music files.
else	
	search_dir=$1
fi


# Make sure directories exist and create if necessary
if [ ! -d "$search_dir" ];then    
  echo "Can't find the search directory $search_dir"
  exit
fi

if [ ! -d "$working_dir" ];then    
  echo "Creating $working_dir"
  mkdir $working_dir
fi

if [ ! -d "$target_dir" ];then    
  echo "Creating $target_dir"
  mkdir $target_dir
fi

if [ ! -d "$unknown_dir" ];then    
  echo "Creating $unknown_dir"
  mkdir $unknown_dir
fi


# COPY OR MOVE FILES???
# COPY ALL FILES!!!! Uncomment this one. It will leave the original files in place. SAFE OPTION
find $search_dir -iname "*.mp3" -exec cp {} $working_dir \;

# MOVE FROM SEARCH DIRECTORY!!!! Uncomment this one. IF THINGS GO WRONG YOUR ORIGINAL FILES ARE GONE!!!
#find $search_dir -iname "*.mp3" -exec mv {} $working_dir \;


# Are you NERVOUS?  Uncomment the exit below, and all the script will do is move or copy all your music files 
# to the working directory allowing you to take a breath
# exit



cd $working_dir
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
  				# If the right directory structure exists - awesome. Move the file.
					if [ -d "$target_dir/$artist/$album" ];then    
						mv "$F" "$target_dir/$artist/$album/$filename"  
					else
					  # If not, build the whole file structure. Won't do any harm to try and create an artist directory that
					  # is already there - so not even checking for that.
						mkdir "$target_dir/$artist"
						mkdir "$target_dir/$artist/$album"
						mv "$F" "$target_dir/$artist/$album/$filename"
					fi
			else
        # Don't know who it's by, what album, or what track, so moving it to UNKNOWN
  			mv "$F" "$unknown_dir/"
				echo -e "UNKNOWN: $F \n"
			fi
	fi
done
```

If you run it unmodified,  it will:

- take all the music in $HOME/Music
- COPY them to $HOME/tmp
- take them one by one from there and move them to New_Music

This is a good undestructive way to see if it works for you.

Hope this is useful to someone. I'm loving it.  

K

---

### Post by sean.bailey00 on 2011-02-02
That bash script is incredibly useful.  I've been looking for one for a while, but have always been too lazy to write it myself.  Thanks!

Also, to answer swaroopkumar, type "mminfo" into a terminal.  If a message pops up and tells you that it is not installed, that is why it is not working.  Copy the command that it gives you to install the most recent package (should begin with "sudo apt-get install"), and once the installation completes you should be good to go.

---

### Post by marm0tte on 2011-12-20
Thanks folks!

In my case I was searching for an app in order to organize my 80 gigs of mp3 files into "genre" folders! But that doesn't exist!!! ](*,)

With quick modifications of the script of thewump, I manage to do it :)
Here is the modified script:


```
#!/bin/bash

# OVERVIEW
# Takes all the mp3 files it can find in a specified search directory then
# moves or copies them to a working directory, then using the embedded file tags
# moves them to the target directory in the structure /genre/artist - trackname
#
# Unrecognized files are stored in an "unknown" directory.
# This is completely MP3 specific.. Will ignore other music files, but easy to modify to support them.

# version 1.0

# First setup some directory variables
working_dir="/media/DATAS/temp" # Somewhere that the script is going to collect the files before processing them
target_dir="/media/DATAS/musics" # Don't make it the same as search_dir or things could get messy
unknown_dir="$target_dir/unknown" # Where to put files that don't have good meta data.

# Allow a search directory to be passed in the command line
if [ -z "$1" ];then
search_dir="/media/music2sort" # DEFAULT. Change this to match where you want to look for music files.
else
search_dir=$1
fi


# Make sure directories exist and create if necessary
if [ ! -d "$search_dir" ];then
echo "Can't find the search directory $search_dir"
exit
fi

if [ ! -d "$working_dir" ];then
echo "Creating $working_dir"
mkdir $working_dir
fi

if [ ! -d "$target_dir" ];then
echo "Creating $target_dir"
mkdir $target_dir
fi

if [ ! -d "$unknown_dir" ];then
echo "Creating $unknown_dir"
mkdir $unknown_dir
fi


# COPY OR MOVE FILES???
# COPY ALL FILES!!!! Uncomment this one. It will leave the original files in place. SAFE OPTION
find $search_dir -iname "*.mp3" -exec cp {} $working_dir \;

# MOVE FROM SEARCH DIRECTORY!!!! Uncomment this one. IF THINGS GO WRONG YOUR ORIGINAL FILES ARE GONE!!!
#find $search_dir -iname "*.mp3" -exec mv {} $working_dir \;

# Are you NERVOUS? Uncomment the exit below, and all the script will do is move or copy all your music files
# to the working directory allowing you to take a breath
# exit

cd $working_dir
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
genre=`mminfo "$F"|grep genre|awk -F: '{print $2}'|sed 's/^ *//g'|sed 's/[^a-zA-Z0-9\ \-\_\&]//g'`

echo "============================"
echo "artist:" $artist
echo "title:" $title
echo "album:" $album
echo "trackno:" $trackno
echo "genre:" $genre

# If we have the genre, then we know where to nicely put this file
if [ -n "$genre" ];then
# If the right directory structure exists - awesome. Move the file.
if [ -d "$target_dir/$genre" ];then
mv "$F" "$target_dir/$genre/$F"
else
# If not, build the whole file structure
mkdir "$target_dir/$genre"
mv "$F" "$target_dir/$genre/$F"
fi
else
# If the genre is unknown, so moving it to UNKNOWN
mv "$F" "$unknown_dir/"
echo -e "UNKNOWN: $F \n"
fi
fi
done
```

---

### Post by thewump on 2011-12-20
Great to see this get some use.  It's been working hard every day for me since I wrote it, and still going strong. I use it to auto-sort stuff coming in from Usenet.

Keith (thewump)

---

