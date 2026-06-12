---
title: "Script for renaming files giving them the name of the folder they're in"
date: 2010-02-02
forum: General Help
---

### Post by Tryfon on 2010-02-02
Hi,

I have a folder where all of my movies are placed. Each movie lies in its own folder. I want to write a script which renames all the movie files and gives them the name of the folder they are in.
For example I want this file: /home/tryfon/movies/Black Irish [2007]/black.irish.dvdrip.avi to be renamed to /home/tryfon/movies/Black Irish [2007]/Black Irish [2007].avi
One issue is that the video files are of several file types (mostly avi, divx and mkv).
Another issue is that some movies consist of two parts, so if a second avi file is found I would like the two (or more) files to be named like: "Black Irish [2007] CD1" and "Black Irish [2007] CD2", or if this is not possible at least notify me of the folders that contain more than one video file.

Thanks in advance.

---

### Post by DaithiF on 2010-02-02
Something like the below may give you a start, but WARNING ... if this goes wrong its likely to overwrite files.  The line which actual performs the renaming is commented out below so that you can preview what actions the script will take first.  So please review carefully before uncommenting that line and running for real.  And taking a backup first would also be a good idea.

And as you can see below, this doesn't try to handle multiple files, it will just bail out when a directory has > 1 file.

```
find . -name '*.avi' -o -name '*.divx' -o -name '*.mkv' | while read path
do 
filename=${path##*/}
suffix=${filename##*.}
dirpath=${path%/*}
parent=${dirpath##*/}
count=$(ls "$dirpath" | wc -l)
if [[ $count > 1 ]]; then
    echo "$path -> Not renaming, more than one file in that directory"
else 
    echo "$path -> Renaming it to $dirpath/$parent.$suffix"
    #mv "$path" "$dirpath/$parent.$suffix"
fi
done

```

---

### Post by Tryfon on 2010-02-03
Ok, using ideas from DaithiF's script I wrote my own which I tested and worked fine, except one little detail which would be nice to fix, because it might lead to data loss (I lost one movie out of about 200).
Here it is:
```
clear
IFS="
"

dir=$(pwd)
echo 'dir: '$dir
for i in $( ls -d */ ); do
	path=$dir/$i
	cd $path
	count=$(find . -maxdepth 1 -name '*.avi' -o -name '*.divx' -o -name '*.mkv' -o -name '*.mp4'| wc -l)
	for j in $(find . -maxdepth 1 -name '*.avi' -o -name '*.divx' -o -name '*.mkv' -o -name '*.mp4'); do
		filename=${j##*/}
		suffix=${filename##*.}
		dirpath=${path%/*}
		parent=${dirpath##*/}
		if [ $count -eq 1 ]; then
			echo 'renaming' $filename 'to '$parent.$suffix
			mv "$path/$filename" "$parent.$suffix"
		else 
			if [ $count -gt 1 ]; then
				for k in {1..$count}
				do
					g=$(($g+1));
					echo 'renaming' $filename 'to '$parent CD$g.$suffix
					mv "$path/$filename" "$parent CD$g.$suffix"
				done
			fi
		fi
	done
done
```

The little problem is that when the video is separated in two parts, for example video.parta.avi and video.partb.avi it doesn't always rename them into video [2000] CD1.avi and video [2000] CD2.avi respectively, but it might mix them up and make the first one CD2 and the second one CD1. And that is because find command doesn't always return its results in alphabetical order. 
If there was some way to do that it would be perfect. So, until this problem is fixed, I don't recommend you using it because it might lead to data loss. Of course you can test it first using echo commands and commenting out the mv commands and then if you are happy execute it properly, but this is up to you.

---

