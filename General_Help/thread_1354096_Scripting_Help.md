---
title: "Scripting Help"
date: 2009-12-13
forum: General Help
---

### Post by Debian1 on 2009-12-13
Hello,

I'm trying to write a bin/bash command that looks at two separate directories and determine if the files date/time stamps are different. If the files date/time are different then copy files over to my backup folder. If not, then don't copy files. 

I know there are tools out there that do this, but I want to learn how to do this by using command line. 

Your help is much appreciated!

Thanks,

---

### Post by mtecknology on 2009-12-13
You shouldn't try to do this yourself because the command line isn't meant for complex operations such as this. Your best option would be to use rsync and make your script a wrapper around this. I use rsync in a large number of my scripts.

rsync -au --delete ---progress
^ I use this a lot

---

### Post by serpantman on 2009-12-13
If you want to learn why are you asking others to do it? There are guides for this sort of thing. A much better learning choice than asking other to do it for you. I'd tell you how right now but i've never checked the time stamp of a file. Also, some of those tools are probably open source. A good start if you wanna figure out how it works.

---

### Post by mtecknology on 2009-12-13
> **serpantman said:**
> If you want to learn why are you asking others to do it? There are guides for this sort of thing. A much better learning choice than asking other to do it for you. I'd tell you how right now but i've never checked the time stamp of a file. Also, some of those tools are probably open source. A good start if you wanna figure out how it works.

You can easily do "apt-get source rsync" if you have the source repositories enabled and you will get the full package source. You could traverse that code and see how they handle it... There's also #bash on Freenode.

Like I said though; there's a reason people rely on code that exists. Reproducing efforts usually doesn't teach you as much as doing something completely new.

---

### Post by ghostdog74 on 2009-12-13
> **mtecknology said:**
> You shouldn't try to do this yourself because the command line isn't meant for complex operations such as this. 
this is crap. what you do on the command line can be put into a script AND you can do complex task with it.

---

### Post by ghostdog74 on 2009-12-13
minimalistic solution, if you have bash 4.0+

```

dir1="/home/dir1"
dir2="/home/dir2"
backup="/dest"
shopt -s globstar
for files in $dir1/**
do
    basename=${files##*/}
    if [ -f "$files" ] && [ -e "$dir2/$basename" ];then
       if [ "$files" -nt "$dir2/$basename" ] || [ "$files" -ot "$dir2/$basename" ];then
            echo cp "$files" "$dir2/$basename" $backup
       fi
    fi

done


```

---

