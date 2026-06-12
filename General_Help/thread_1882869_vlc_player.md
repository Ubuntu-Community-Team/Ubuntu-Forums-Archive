---
title: "vlc player"
date: 2011-11-18
forum: General Help
---

### Post by thenectorgod on 2011-11-18
i have tried to make  a shell script which searches my directory and plays automatically whichever song i want to play if it is there in my computer.
I have reached till this sh script:
cd /media/VODKA/Hindi/
echo $1
i=" `find . -name *$1*` "
vlc $i


#sh a.sh  opardesi    --- vlc plays the song

but this requires my file structure not to have any spaces as if any space is there vlc takes it as different arguments so how to escape space chars and make it work.
Thanks for your help.

---

### Post by nixblog on 2011-11-18
What about wrapping the filename in quotes,

#sh a.sh "this is a song with spaces in the filename"

is this what you are after?

---

### Post by WasMeHere on 2011-11-18
Welcome to the Ubuntu Forums, thenectorgod,

> **thenectorgod said:**
> i have tried to make  a shell script which searches my directory and plays automatically whichever song i want to play if it is there in my computer.
I have reached till this sh script:
cd /media/VODKA/Hindi/
echo $1
i=" `find . -name *$1*` "
vlc [COLOR="Red"]"[/COLOR]$i[COLOR="Red"]"[/COLOR]

#sh a.sh  opardesi    --- vlc plays the song

but this requires my file structure not to have any spaces as if any space is there vlc takes it as different arguments so how to escape space chars and make it work.
Thanks for your help.

Would this work for you (add [COLOR="Red"]double quotes[/COLOR]) as above?

Have fun finding out about Ubuntu :-)
Olle

---

### Post by thenectorgod on 2011-11-18
The problem is when i enter any song name with name it makes the last command look like
vlc waiting for tonight
so vlc tries to run three different files named waiting,for,tonight 
and even the name of the directory in which it is should not contain spaces

---

### Post by WasMeHere on 2011-11-19
Try this script
```
#!bash
if [ "$1" == "" ]
then
 echo "Usage: $0 song-name"
 echo "or:    $0 part-of-song-name"
 exit
else
 cd /media/VODKA/Hindi/
 echo $0 finding files with $1
 find . -name "*$1*"
 find . -name "*$1*" -exec vlc {} \;
fi
```
It plays all files matching your song-name or part-of-song-name, but that can be fixed if you like.

---

### Post by thenectorgod on 2011-11-19
Thanks the problem is sorted out.
One more thing the program you wrote plays one by one all songs matching can it be done such that i can select one out of the options available .

---

### Post by WasMeHere on 2011-11-19
The standard way:
Make a ***play-list*** within the GUI version of VLC and select from that.

The short way:
Break execution by *ctrl C* in the terminal window. Then type ***vlc*** and *triple-left-click* on the line of the tune you want to play to select it and finally *middle-click* to paste it after vlc (and execute with Enter). Surround with quotes if whitespace in the name.

example
./tune number 1.ogg
./tune number 2.ogg
./tune number 3.ogg
./tune number 4.ogg
...
^C
vlc "./tune number 2.ogg"

The long way:
Make a GUI for example with ***kdialog***. Browse the internet to learn about it!

---

