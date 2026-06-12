---
title: "Command Line mp3/m4a tag editors"
date: 2006-06-01
forum: General Help
---

### Post by maiki_desu on 2006-06-01
I've found some of GUI frontend tag-editors that support mp3, m4a, aac, etc... But what i need is a command line tag-editor.

Actually all I need is it to display the tag-data from mp3, mp4, m4a, and aac files.  What I need to do in the end is pipe this data through awk so i can copy files based on artist, album, etc..  

Does anybody have any ideas on a good command-line editor?

---

### Post by briguy on 2006-06-08
This app has a debian version - haven't tried it though.  It's a command line mp4 editor, not sure if that's what you're looking for.

edit - [http://atomicparsley.sourceforge.net/](http://atomicparsley.sourceforge.net/)

---

### Post by maiki_desu on 2006-06-22
thanks
 i was hoping for one that did both mp4 AND mp3, but it looks like it doesn't exist.  maybe i can just write a check in my script, if it's mp4 use this, if not use id3ed or something

sorry for the late reply

---

### Post by briguy on 2006-06-25
I've actually started using this program, and it seems to work pretty well.  Here's a quick script I made for changing a directory of mp4's.  If they are TV shows, just put the argument --tv and it will label them all as tv shows, otherwise it will assume that they are movies.   It prompts you to enter the title for each video.

I would do this on a copy of your files - it has worked so far but I haven't spent a lot of time testing it.:-k  To make it work, put it in a text file called "labelmp4" or something, chmod +x labelmp4 and put it in your path (like /usr/local/bin).

Hope you find it useful, maybe someone can expand on it to make it a bit more functional. :rolleyes:


```
#!/bin/sh
echo "This script will process all the .mp4 files in the current directory `pwd`."

# turn arguments into boolean values
istv=0 # default to false
for arg in $@
do
  if [ $arg = "--tv" ]
  then
   istv=1
  fi
done

if ls | grep .mp4 # check to see if there are any .mp4 files
then
  if [ "$istv" -eq 1 ] # check to see if files should be labelled as tv shows
  then
    echo "Processing all files as TV shows.  Assuming all files are from the same show and season."
    echo "What is the TV show name of the files in `pwd`?"
    read tvshow
    echo "For which season?"
    read season
    for vid in *.mp4
    do
      echo "Processing $vid..."
      echo "What is the title for this episode?"
      read title
      AtomicParsley "$vid" --overWrite --title "$title" --genre "TV Show" --stik "TV Show" --TVShowName "$tvshow" --TVEpisode "$title" > /dev/null
    done
  else
    for vid in *.mp4
    do
      echo "Processing $vid..."
      echo "What is the title of this video?"
      read title
      AtomicParsley "$vid" --overWrite --title "$title" --genre "Movie" --stik "Movie" > /dev/null
    done
  fi
  echo "Finished processing `pwd`"
else
  echo "No .mp4 files found!"
fi
```

---

### Post by maiki_desu on 2006-06-28
sweet, thanks for the script

Although my original need for a script and mp4 tag reading is now gone (I just figured out that gtkpod CAN copy from the ipod to the PC and maintain (or recreate) the directory structure, if you use a output filename like %a/%A/%t.m4a;%a/%A/%t.mp3 or something), I think I still want to write a script to reorganize or retag things.

Thanks for your help (i'll let you know if i come up with somethign cool or useful)

---

