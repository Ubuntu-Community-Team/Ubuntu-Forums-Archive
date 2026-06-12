---
title: "Folder sync with transcoding"
date: 2011-04-16
forum: General Help
---

### Post by georgebrough on 2011-04-16
I am trying to write a script to maintain a copy of my music collection at a lower bit rate to allow me to stream it.  Unfortunately the plugbox server doesn't have the power to transcode on the fly.  

This is my first attempt at programming in Linux, I've written this which does what I need but only for the current directory.  Various problems occur when you add sub dirs.  

```

#!/bin/bash

# Delete from destination (3) folder if missing from source (2) based on file name [] is the same a test

for i in /test/3/*; do
filename=`basename "$i"`
if [[ ! -f /test/2/$filename ]]; then
echo del $filename
rm "/test/3/$filename"
fi
done


# Transcode from source (2) to destination(3) if missing from destination

for i in /test/2/*.mp3; do
echo $i
filename=`basename "$i"`
if [[ ! -f /test/3/$filename ]]; then
echo trans $filename
lame --mp3input -b 96 "$filename" "/test/3/$filename"
fi
done


# Copy non mp3s in the same way

for i in /test/2/*; do
filename=`basename "$i"`
if [[ ! -f /test/3/$filename ]]; then
echo cp $filename
cp "/test/2/$filename" "/test/3/$filename"
fi
done

```I also looked at using the find command as discussed here [http://ubuntuforums.org/showthread.php?t=380009](http://ubuntuforums.org/showthread.php?t=380009) but I can't get that to work either.  

Any help would be appreciated!

Thanks

George

---

### Post by papibe on 2011-04-16
Take a look at MediaTomb. It does [transcoding on the fly]("http://mediatomb.cc/pages/transcoding").

Regards.

---

### Post by georgebrough on 2011-04-16
Hi,

The software i'm using (Subsonic) does transcoding.  However the server that it is running doesn't have enough processing power to do it on the fly.  I want the sever to do it while I'm asleep :)

---

### Post by papibe on 2011-04-16
I see.

The syntax on the find command on the thread you linked is indeed incorrect, and won't work. Check my post on this [one]("http://ubuntuforums.org/showthread.php?t=1730353").

I hope it helps.

---

### Post by georgebrough on 2011-04-17
I tried this

```
find -iname *.mp3 -exec lame --mp3input -b 96 "{}" "/test/3/{}" \;
```but I get errors such as

Can't init outfile '/test/3/./untitled folder/ a music file.mp3'

So I tried to use substring to remove the first couple of letters from the file name

```

find -iname *.mp3 -exec lame --mp3input -b 96 "{}" "/test/3/${{}:2}" \;
```I played around with the syntax for a while but keep getting a message about bad substitution

---

### Post by papibe on 2011-04-17
First of all, you need to quote the regular expression:
```
$ find -iname '*.mp3' -exec lame --mp3input -b 96 {} /test/3/{} \;
```
Note the '*.mp3'.

Now, the problem with that is the first time you need the full path as an argument, so the first appearance of {} will be correct. The second time (/test/3/{}) you need just the file name and not the full name. The command basename could do that, but it can't be called in the -exec argument (it would required bash interpretation). The solution that I came up with is to use bash itself as the exec argument, and past what you have now as an string to be executed.

```
find -iname '*.mp3' -exec bash -c 'file=`basename {}`; lame --mp3input -b 96 {} /test/3/$file' \;

```

Let me know how it goes,
Regards.

---

### Post by georgebrough on 2011-04-19
Hi,

For the benefit of anyone who may want to do the same here is my script so far.  

```

#!/bin/bash

#sync the folder structure and all non mp3 files
rsync -r --delete-after --exclude '*.mp3' /home/george/Music/Albums/ /home/george/Music/Stream/Albums

#look for mp3s in current dir and if they don't exist in destination transcode them to it
find /home/george/Music/Albums/ -iname '*.mp3' -exec bash -c 'file="{}"; file=${file:26}; if [[ ! -f /home/george/Music/Stream/Albums/$file ]] ; then lame --mp3input -b 96 "{}" "/home/george/Music/Stream/Albums/$file"; fi ' \;

#look for mp3s in destination and delete them if they are not in source
find /home/george/Music/Stream/Albums -iname '*.mp3' -exec bash -c 'file="{}"; file=${file:32}; if [[ ! -f /home/george/Music/Albums$file ]] ; then rm "{}" ; fi ' \;

```I couldn't use basename because it only gives the file name, I wanted to keep the folder structure below the level from where the find is so I used substring e.g.  ```
${file:26}
```I couldn't find a way to achieve this in one assignment to the variable but I feel that I shouldn't have to do it in two parts?

```
file="{}"; file=${file:32}
```The substring function didn't seem to like having "{}" instead of the variable name.  

The only problem I can see now is with file names that have special characters in them such as ' or $ .  There are few enough that I could remove them but I wonder if anyone can tell me how to deal with these?

Thanks for all your help!

---

### Post by papibe on 2011-04-20
I think the bash string has 'increase' enough to take it out if the find. Something like this:
```
#!/bin/bash
...

for f in `find /home/george/Music/Albums/ -iname '*.mp3'`
do
    file="$f"
    file=${file:26}

    if [ ! -f /home/george/Music/Stream/Albums/$file ]
    then
        lame --mp3input -b 96 "$f" "/home/george/Music/Stream/Albums/$file"
    fi
done

...

```
It's the same idea but since the code is out of the find, it is just plain bash.

I hope it helps.

---

### Post by georgebrough on 2011-04-20
I think this code can't deal with spaces in the file names (which they all have...you can tell it's not been long since i moved from windows to linux right ;) ) it tries to run the loop for each word in each file name!  I tried playing around with some "quotes" but couldn't make it any better.

---

### Post by papibe on 2011-04-20
I see. There's a trick: change what the loop 'for' interprets as separation. 'for' uses a bash variable called IFS. The trick is change its value before the loop (a good idea is to set it back as before at the end). Something like this:
```
#!/bin/bash
...

SAVEIFS=$IFS
IFS=`echo -en "\n\b"`

for f in `find /home/george/Music/Albums/ -iname '*.mp3'`
do
    file="$f"
    file=${file:26}

    if [ ! -f /home/george/Music/Stream/Albums/$file ]
    then
        lame --mp3input -b 96 "$f" "/home/george/Music/Stream/Albums/$file"
    fi
done

IFS=$SAVEIFS
...
```
Let me know how it goes this time,
Regards.

---

### Post by georgebrough on 2011-04-21
That's got it!

Many thanks for all your help :)

Regards

George

---

