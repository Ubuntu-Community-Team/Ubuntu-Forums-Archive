---
title: "shell script to check folder contents and move accordingly"
date: 2009-12-04
forum: General Help
---

### Post by cj13579 on 2009-12-04
Hi All,

I am pretty knew to shell scripting and would like some help doing something that, at the moment, is a little out of my reach! 

The story is that all my downloads are plonked in one folder but I seperate them into music, films, pdfs etc. If I can, I would like to automate this process.

I am thinking that this would be done by checking the file extension of the files in the sub folder and if more than so many files are one type then it puts it in a folder i.e. more than 50% are .mp3 so put them in the music folder. I'm sure that i'm not the only person that has wanted to automate this process and so maybe there is someone out there who is willing to share their script with me! I'm guessing there may also a piece of software that does what I am looking for.

Any help at all would be much appreciated.

Chris

---

### Post by StuartN on 2009-12-04
> **cj13579 said:**
> I am pretty knew to shell scripting and would like some help doing something that, at the moment, is a little out of my reach!

You could have a sequence of move commands, e.g. **mv -i *.mp3 ~/Music**, where the -i option checks for existing files with the same name, and possibly include a move command for *.MP3 and other variants of each file type.

If you wanted really clever, then you could read the mp3 file tags with id3v2 and create directories for each album, maybe something like **album="$(id3v2 -l "$filename" | grep -E TALB? | sed -e 's/^.*:\ //g')"; mkdir ~/Music/$album; mv {} ~/Music/$album;** using the find command.

---

### Post by cj13579 on 2009-12-04
> **StuartN said:**
> If you wanted really clever, then you could read the mp3 file tags with id3v2 and create directories for each album, maybe something like **album="$(id3v2 -l "$filename" | grep -E TALB? | sed -e 's/^.*:\ //g')"; mkdir ~/Music/$album; mv {} ~/Music/$album;** using the find command.

I think that is a little too clever!!

I think I need to use something simmilar to this:
```
 find /source/direct/ -name '*.mp3' -exec mv '{}' /destination/ \;
``` 

How would I be able to modify this so that it moves the folders rather than just the files. Or, if i can't do that, creates the folder in the destination directory.

Many thanks for your suggestions!

---

### Post by StuartN on 2009-12-04
> **cj13579 said:**
> How would I be able to modify this so that it moves the folders rather than just the files. Or, if i can't do that, creates the folder in the destination directory.

The absolutely simplest way to copy files from one tree to another, creating the directory structure, is rsync.

```
rsync -avz --include "*/" --include "*.mp3" --exclude "*" dir1/ dir2/
```

This means search and include all directories in dir1, include all mp3 files, exclude all other files, add these to the correct path in dir2 (creating the path if required). The -avz options mean archive mode (searches recursively), verbose output and compress during copy.

You can put as many include and exclude statements as you like, for instance --include "*.mp3" --include "*.MP3" --include "*.ogg".

---

### Post by falconindy on 2009-12-04
With an inotifywait script, and they'll be automatically moved to wherever you want on creation.
```
#!/bin/bash
MUSIC="/path/to/music"
VIDEO="/path/to/video"
PICS="/path/to/images"

moveIt() {
        while [[ `lsof %f > /dev/null 2>&1` ]]; do
                sleep 5 #File might be downloading, leave it alone for now
        done
        #hands off my file, im moving it
        mv "$1" "$2"
}

inotifywait -qm --event CREATE --format %f ~/Desktop | while read file; do
        case ${file:(-3)} in
                "mp3") moveIt "$filei" "$MUSIC" ;;
                "jpg"|"png") moveIt "$file" "$PICS" ;;
                "avi"|"ogm"|"mkv") moveIt "$file" "$VIDEO" ;;
        esac
done
```
Alter the declarations at the top to your liking, as well as the extensions I'm capturing in the case statement. Throw this into a script file, `chmod +x script.sh` and execute it as `./script.sh &`

P.S. You **might** need to install the inotify-tools package. I don't know offhand if Ubuntu comes prepackaged with it.

---

### Post by cj13579 on 2009-12-05
> Alter the declarations at the top to your liking, as well as the extensions I'm capturing in the case statement. Throw this into a script file, `chmod +x script.sh` and execute it as `./script.sh &`

That's brilliant, but will it move the whole folder that is created or will it just move the contained files? Also, when running the script do you have to give it the locations i.e:

```
./script.sh /source/folder/ /destination/folder/
```

many thanks with your help on this!

---

### Post by pbrane on 2009-12-05
inotifywait is watching **~/Desktop** for changes. If you download your files to another location you should change that line. The script does not create directories. You should have those already created. Basically if you download a music file ( .mp3 in this script ) to the desktop with this script running in the background it will mv that music file to the $MUSIC directory. The **mv** command can move files and/or directories. The way this is written it will be moving files.

run **man inotifywait** in a terminal to see the options.

this is a cool script!

---

### Post by cj13579 on 2009-12-05
> You should have those already created. Basically if you download a music file ( .mp3 in this script ) to the desktop with this script running in the background it will mv that music file to the $MUSIC directory.

Say I torrent an album to my dl directory it will put it in a folder in that directory. How would I edit the script to move the whole folder to another directory. I think I will need to read the folder name into a variable somehow but I don't know how to do that. I can then us "mv" to put it in $MUSIC/$newalbum or whatever.

---

