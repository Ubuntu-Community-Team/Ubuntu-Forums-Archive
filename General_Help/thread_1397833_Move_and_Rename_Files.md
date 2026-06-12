---
title: "Move and Rename Files"
date: 2010-02-03
forum: General Help
---

### Post by Magical Tiger on 2010-02-03
Hey everybody out there on the internet! I have a bunch of media files that are named very ridiculously and would like to organize them based on their file names. They are *.avi named in the format of:

./<name_of_artist>-<alubum_name>_<track_number>-<song_name>.avi

I would like to rename and organize them like:

./<Name Of Artist>/<Album Name>/<track number> - <Song Name>.avi

I used music stuff which it isn't but I think you can get the idea. I am looking for maybe a short script or something that would automate the process so I don't have to do it. Thanks to anyone out there you decides to help!

---

### Post by Dr Belka on 2010-02-04
sounds like you need to use a program called sed.  I would tell you how exactly to get it to work, but I am not yet THAT good at regular expressions

---

### Post by Magical Tiger on 2010-02-04
Yeah, sed would probably work but I don't know how to use it. I have tried to learn it but it just doesn't make sense. Could someone write a script or tell me how to in sed?

---

### Post by viking1au on 2010-02-04
Unless I miss something, you should be able to click on "View" then click on "Arrange Icons" then select "By Name" or whatever.

---

### Post by Magical Tiger on 2010-02-04
Yeah I could do that and that is what I'm doing but I don't like it and thats why I came to this forum.

---

### Post by falconindy on 2010-02-04
This isn't actually completely straight forward because you can't expect the directories to exist and mv won't make the directories for you. I'm sure someone may come along and do this in a single sed script, but I'm only familiar with sed one-liners, so I fall back on Bash's string manipulation.

Also, not tested, but it might get you moving in the right direction. Run it in the base of the directory with the .avi files:
```
#!/bin/bash

find . -mindepth 1 -maxdepth 1 -type f -iname *.avi | while read file; do
    file=${file##*/}  # equivalent to the basename command
    orig="$file"  # save the basename since we'll be messing with it

    artist=${file%%-*}  # words before the first - are considered the artist
    file=${file/$artist-}  # Don't need the artist info anymore, stored separately

    # Repeat the same as above for the album and track name
    album=${file%%_*}
    file=${file/$album_}

    track=${file%%-*}
    file=${file/$track-}  # Remainder here is name.ext

    [[ -d "$artist/$album" ]] && mkdir -p "$artist/$album"  # make the dir if it doesn't exist
    mv "$orig" "$artist/$album/$track - $file"  # move into place
done
```
Because I'm using find and limiting depth, this script can actually be re-run over and over again without touching already sorted files. I would advise changing the final 'mv' command to an 'echo' to see what it'll do before you actually go ahead and execute.

---

### Post by Magical Tiger on 2010-02-06
Thanks for the script. I had to heavily modify it but it provided me with a very good starting point. Thanks again.

---

