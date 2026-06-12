---
title: "ok... here goes. simple copy script question???"
date: 2010-02-04
forum: General Help
---

### Post by drink_stir on 2010-02-04
Alright im trying to make just a simple copy script to copy the video files that are saved in the /tmp folder from when i watch a video online, and want to keep. i dont know why im having such a hard time.

This is what i have so far...

if [ /tmp/{Flash} ] ; then  cp -f /tmp/{Flash} ~/Videos; else echo "Nothing There"; fi

The files that are in the /tmp folder all start with Flash folowed by a series of numbers al letters. im stuck and kind of new to linux.

---

### Post by doas777 on 2010-02-04
I'm not seeing anythign there that actually loops through all the files in your dir. you can try the find command for that, or actually define a loop of your own. 
it's been a long time since i did any really shell stuff so you'll have to ask someone else for the code itself. i tend to use python anymore instead. shell is often just too cryptic for daily use.

---

### Post by Odd-rationale on 2010-02-04
Try with the -f :

```

if [ -f /tmp/Flash* ]; then
...

```

---

### Post by Barriehie on 2010-02-04
**inotifywait** might be the tool you're looking for.  I've got a script, posted below, which runs and when a file is created in a dir. it will rename it and move it to another dir.  inotify wait has an event trigger such that when a file is closed it will do whatever.

Here's the script, never mind the line where it calls picsdaemond-timer, this just kills the script after so many minutes.
```

#!/bin/bash
#

/home/barrie/bin/picsdaemond-timer &

OLDDIR=$HOME"/Desktop/temp/pics/"
NEWDIR=$HOME"/Pictures/SS/moved/"
declare -a CHARSARRAY=('a' 'A' 'b' 'B' 'c' 'C' 'd' 'D' 'e' 'E' 'f' 'F' 'g' 'G' 'h' 'H' 'i' 'I' 'j' 'J' 'k' 'K' 'l' 'L' 'm' 'M' 'n' 'N' 'o' 'O' 'p' 'P' 'q' 'Q' 'r' 'R' 's' 'S' 't' 'T' 'u' 'U' 'v' 'V' 'w' 'W' 'x' 'X' 'y' 'Y' 'z' 'Z' '0' '1' '2' '3' '4' '5' '6' '7' '8' '9')
declare -a CHARS
declare -i NUMBER=0
declare -i LOOPCOUNTER=0

inotifywait -mq --format '%f' -e create /home/barrie/Desktop/temp/pics/ | while read line
do
file=$line

  while [ $LOOPCOUNTER -lt 10 ]
  do
    RANDOM=$(date +%N)
    NUMBER=$((RANDOM%62+1))
    CHARS[$LOOPCOUNTER]=${CHARSARRAY[$NUMBER]}
    LOOPCOUNTER+=1
  done
  LOOPCOUNTER=0         # ----------------------------- Reset name length counter
  NEWFILENAME=${CHARS[0]}${CHARS[1]}${CHARS[2]}${CHARS[3]}${CHARS[4]}${CHARS[5]}${CHARS[6]}${CHARS[7]}${CHARS[8]}${CHARS[9]}.jpg

  mv $OLDDIR$file $NEWDIR$NEWFILENAME

  declare -a CHARS=  # ----------------------------- Reset CHARS array

done

```

TMH,
Barrie

P.S.:  Might have to install inotify-tools.

---

### Post by drink_stir on 2010-02-04
i think i got it to work with 
```
if /tmp/Flash* ; then  cp -f /tmp/Flash* ~/Videos; else echo "Nothing There"; fi

```
 but now i get permission denied

how do i get around that?

---

### Post by Barriehie on 2010-02-04
/tmp is owned by root so your script will have to be run by root.

Barrie

---

### Post by screaminfakah on 2010-02-04
I just use the add on "downloadhelper" right from firefox but where is the fun in that?

---

### Post by falconindy on 2010-02-04
Because your if loop is trying to execute the file, not check for the existance of it. I think what you're trying to accomplish is better suited to something like find:
```
#!/bin/sh
find /tmp -type f -iname flash* -exec cp "{}" ~/Videos/ \;
```

> **Barriehie said:**
> /tmp is owned by root so your script will have to be run by root.

Barrie
/tmp is owned by root, but on a healthy system it should be mode 1777 meaning that anyone can write, but you can only delete/modify your own files. Regardless, this is a copy **from** /tmp, not copy **to** so the OP needs only read permissions.

> **doas777 said:**
> I'm not seeing anythign there that actually loops through all the files in your dir. you can try the find command for that, or actually define a loop of your own. 
it's been a long time since i did any really shell stuff so you'll have to ask someone else for the code itself. i tend to use python anymore instead. shell is often just too cryptic for daily use.
Bash is beautiful! It can do so much, and its light years faster than python.

---

### Post by x C0MMAND0 x on 2010-02-04
You could set this up in crontab to run every minute or so, or add an entry to have in automatically run every 10 minutes to the script itself and then put it in startup.  Let me know if you are interested in code and I shall post.

---

### Post by Barriehie on 2010-02-04
> **screaminfakah said:**
> I just use the add on "downloadhelper" right from firefox but where is the fun in that?

+1, me too!

---

### Post by drink_stir on 2010-02-04
well holy hell... that download helper is pretty much what i was looking to do. guess i was jsut trying the long way. oh well... thanx everyone. ill mess with the scripts on something else. just trying to start learning from somewhere.

---

### Post by Barriehie on 2010-02-04
> **drink_stir said:**
> well holy hell... that download helper is pretty much what i was looking to do. guess i was jsut trying the long way. oh well... thanx everyone. ill mess with the scripts on something else. just trying to start learning from somewhere.

Won't tell you how long I messed around before discovering the inotify-tools for renaming/moving my files... :)

---

### Post by Barriehie on 2010-02-05
So if this thread is solved might consider marking it as such. :)

---

### Post by drink_stir on 2010-02-06
well it wasnt quite solved cause i hadnt found quite what i was looking to do but with a little messing around i got it to work. i saved

```
#!/bin/bash
find /tmp/Flash* -exec cp "{}" ~/Videos/ \;
```

as a .txt file and then just added a custom application launcher to my toolbar with "bash 2.txt" and bam... now if i watch a video i like i dont have to wait for it to download i can just copy it. thanx all for the help. now its off to some renaming scripts.... yee haw...

---

