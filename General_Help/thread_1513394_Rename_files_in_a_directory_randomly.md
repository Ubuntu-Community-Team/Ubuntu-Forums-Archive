---
title: "Rename files in a directory randomly"
date: 2010-06-19
forum: General Help
---

### Post by Smart Viking on 2010-06-19
Hey everyone, quick little question here.

I want to rename all files in a directory to "random" names(the point is that the name does not exist, it can be anything). In my case is it *.wav file i want to rename, i basically want to burn cd's to my pc with cdparanoia, then rename them and put them in a directory with other songs i have which also have been given random names. (i'm creating a big music directory where the songs have no names) :P

And i will eventually make a script to make things easier, but for some reason i can't think out a way to rename the files randomly, and i guess "$RANDOM" is a good variable to use but.. how? Thank you :D

EDIT: And while i'm at it, is there any way to use the "play" command in the terminal, by "sorting" music files in a directory randomly, and then play them, so it will not be played the same order again? :P

---

### Post by kaibob on 2010-06-19
Have a look at this thread. It has a number of ways to do what you want:

[http://ubuntuforums.org/showthread.php?t=1459641](http://ubuntuforums.org/showthread.php?t=1459641)

My suggestion in this thread was:

```
#!/bin/bash

for file in *.wav ; do
   name=$(tr -dc "[:alnum:]" < /dev/urandom | head -c 10)
   mv "$file" ${name}.wav
done
```

You can change :alnum: to :digit: or :alpha: depending on what you want.

---

### Post by Smart Viking on 2010-06-19
Thank you :D

This is what i ended up with

```
#!/bin/bash
tty -s; if [ $? -ne 0 ]; then "xfce4-terminal" -e "$0"; exit; fi
for file in *.wav ; do
   name=$(tr -dc "[:alnum:]" < /dev/urandom | head -c 10)
   mv "$file" /home/smartviking/Music/eternity/${name}.wav
done
```

Worked perfectly, and i am gona integrate cdparanoia with that script, that helped a lot. :)

---

### Post by Smart Viking on 2010-06-19
Now my script looks like this

```
#!/bin/bash
tty -s; if [ $? -ne 0 ]; then "xfce4-terminal" -e "$0"; exit; fi
cdparanoia -B

for file in /home/smartviking/Music/burn/*.wav ; do
   name=$(tr -dc "[:alnum:]" < /dev/urandom | head -c 10)
   mv "$file" /home/smartviking/Music/eternity/${name}.wav
done
```

I put the script in /home/smartviking/Music/burn/, and created a symbolic link to the desktop so a basically i only have to put a cd in and double click the link. :D


Now as i mentioned earlier, i am looking for a command that "sorts" those music files randomly, and then play it. That way everything will be completely random. Any tips?

This forum have been a great help! :)

---

### Post by Smart Viking on 2010-06-19
I finally found a solution for my last question. :D

```
#!/bin/sh
tty -s; if [ $? -ne 0 ]; then "xfce4-terminal" -e "$0"; exit; fi
cd /home/smartviking/Music/eternity
ls *v | sort -R > playlist
mplayer -playlist playlist
```

I had to use the "mplayer" command, but that works perfectly for me. :D

This thread is now solved. :)

---

