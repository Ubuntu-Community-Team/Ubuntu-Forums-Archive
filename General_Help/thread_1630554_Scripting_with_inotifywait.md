---
title: "Scripting with inotifywait"
date: 2010-11-25
forum: General Help
---

### Post by snyderxc on 2010-11-25
Hi all,

I'm a very novice scripter, and I am looking for some help with the recursive flag (-r) of inotifywait.  inotifywait does see when a file is created and triggers the event, but I cannot figure out how to determine what directory the file that triggered the event is in.

Basically, I started with the code on this page:

[http://www.webupd8.org/2010/11/script-to-watch-folder-and-upload-new.html](http://www.webupd8.org/2010/11/script-to-watch-folder-and-upload-new.html)

And I want to upload the picture from subdirectories.  Adding -r will see when there is a new file, I just need to get the directory that file is in.

Thanks!

SnyderXC

---

### Post by aeiah on 2010-11-25
doesn't look like you can. it looks like it'll always just pass the filename / directory, not the whole path from looking at the [manual]("http://linux.die.net/man/1/inotifywait")

maybe there's another way around it though. how many subdirectories are we talking? perhaps you could just watch those directories instead of recursivley watching everything? or if you are syncing to a server that supports rsync, you could just sync the whole thing if something changes and rsync will make sure it only transfers the bits that have changed

---

### Post by snyderxc on 2010-11-25
Thanks for the response. It's actually using GoogleCL (Google Command Line tool) as the backend. It allows you to sign in as a Google user. If I try uploading the entire directory, I get "[Errno 21] Is a directory: '/media/fdrive/Pictures/2010 Pictures'" So I guess that is out of the picture.

It's only one directory deep (2010 Pictures/Picnic and 2010 Pictures/Christmas, etc.) So I guess I could just create a watch for each one, maybe there's a way to automate this?

Thanks,
SnyderXC

---

### Post by snyderxc on 2010-11-25
I've been thinking this through. Because there I only need to go one subdirectory deep, perhaps there is a way to use "ls -1" and parse each line to add to the end of "WATCHED_DIR"

---

### Post by snyderxc on 2010-11-26
So, I've finally got it to what is a satisfactory working state. It will upload from subdirectories one level deep as long as the folder names have no whitespaces. Included in the script are the remnants of other attempts. If anyone has improvements, feel free to contribute! :-)

```
# !/bin/sh
# 1. Watch ~/Pictures/PicasaWeb folder. 
# 2. Upload new file to Picasa using Google CLI. 
# 3. Launch the browser to the direct Picasa URL. 
# 

#set -x


###########################################
#change the variable below with the folder you want this script to watch for new images:

WATCHED_DIR="/home/user"
###########################################


LINES=`ls ./ | wc -l`
cd "$WATCHED_DIR"
ls -1 >> .subdirs
i=1

############################################
#change the variable below with exact name of the PicasaWeb album you want to upload the images to:
PICASA_ALBUM="Drop Box"
############################################


while [ 1 ]
do
  echo 'Watching directory: '"$WATCHED_DIR" 'for new files'

#for i in {ls $WATCHED_DIR}
#do
MYSUB=dirname                   #${WATCHED_DIR}${i}

  while file=$(inotifywait -r -q -e create "$WATCHED_DIR" --format "%f" "$DIR"); do




    NEWDIR=$WATCHED_DIR
    echo 'New file to upload to PicasaWeb:' $file
    notify-send -i "gtk-go-up" "Picasa Web Monitor" "Uploading image $file"
#    MY_DIR=`cwd`
     for n in $( ls `$WATCHED_DIR` )
     #for i in { 1..`$lines` }
     




     #while [  $i -lt $LINES ]
     do
     #set n=$(echo sed -n 3p .subdirs)    
if [ -e "$WATCHED_DIR"/"$n"/"$file" ]
then

    google picasa post --title "$PICASA_ALBUM" "$WATCHED_DIR"/"$n"/"$file"
fi
#let i=i+1
    done
if [ -e "$WATCHED_DIR"/"$file" ]
then
    google picasa post --title "$PICASA_ALBUM" "$WATCHED_DIR"/"$file"
fi
#    i=1

    url=$(google picasa list url-direct --title $PICASA_ALBUM | grep "$file" | sed -e "s/$file\,//g")
    echo 'Picasa url: ' $url
    notify-send -i "gtk-home" "Picasa Web Monitor" "Image uploaded."
#    xdg-open $url
#    done
  done
done
```

---

