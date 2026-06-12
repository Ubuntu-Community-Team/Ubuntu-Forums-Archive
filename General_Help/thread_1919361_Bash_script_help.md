---
title: "Bash script help"
date: 2012-02-02
forum: General Help
---

### Post by Nakira89 on 2012-02-02
I'm trying to write a bash script that will automatically transfer the photos from the camera to a folder sorted by date.
My issue is getting it to run after its mounted automatically. When i plug the camera in the script does not run, but, if i run the script through command line a few seconds after its mounted then it works. Its as if the camera is not mounted in time for the script.

My Script :
```

#!/bin/bash
touch "/home/josh/Desktop/file.file"
(
mount /dev/sdd1 /media/Sony-A350
touch "/media/Sony-A350/DCIM/100MSDCF/"
NUM=$(ls -l /media/Sony-A350/DCIM/100MSDCF/ | grep -v ^l | wc -l )
count=0
ls -p /media/Sony-A350/DCIM/100MSDCF/ | grep -v '/' | while read file;
do
count=`expr $count + 1`
FILENAME="${file##*/}";
echo "#/media/Sony-A350/DCIM/100MSDCF/$FILENAME" 
MODDATE=$(stat -c %y "/media/Sony-A350/DCIM/100MSDCF/$FILENAME")
MODDATE=${MODDATE%% *}
IFS="-"
set -- $MODDATE
array=( $@ )
NAME="/media/Movies/BackupDrive/Photos/Joshs/test/${array[0]}/${array[1]}/${array[2]}";
mkdir -p "$NAME";
cp "/media/Sony-A350/DCIM/100MSDCF/$FILENAME" $NAME;
rm "/media/Sony-A350/DCIM/100MSDCF/$FILENAME"
echo "scale=10;($count/$NUM)*100" | bc
done
echo "#Files Fnished Copying"
) |
  zenity --progress \
          --title="Downloading Photos From Sony-A350" \
          --text="" \
         --percentage=0
exit 0


```rule 70 :
```

# /etc/udev/rules.d/70-camera-script.rules

BUS=="usb", KERNEL=="sd?1", ATTRS{serial}=="592680233B55", NAME="%k", SYMLINK+="Sony-A350"

```rule 90 : 
```

# /etc/udev/rules.d/99-camera-script.rules

KERNEL=="sd?1", ATTRS{serial}=="592680233B55", ACTION=="add", RUN+="/home/josh/script/camera-connect"

```Hope you can help 

n.b. rules where in same file, but tried separating them into separate ones to attempt to solve my issue.

Thanks in advance,
Regards,
Josh.

---

### Post by lechien73 on 2012-02-02
Have you tried, maybe, adding:

```
sleep 10
```

at the top of your script beneath the shebang?

This will make the script pause for 10 seconds before continuing execution. It might give the camera time to mount.

---

### Post by Vaphell on 2012-02-02
maybe probing if the directory exists/is accessible would work? something like
```
while true; do if [ -d ... ]; then break; fi; sleep 1; done
```

```
... | grep -v ^l | wc -l
```
can be replaced with ```
... | grep -vc ^l
```
and
```
count=`expr $count + 1`
```
with
```
((count++))
```

---

### Post by sisco311 on 2012-02-02
> **Nakira89 said:**
> 
```

#!/bin/bash
touch "/home/josh/Desktop/file.file"
(
[COLOR="Red"]mount /dev/sdd1 /media/Sony-A350[/COLOR]
touch "/media/Sony-A350/DCIM/100MSDCF/"
[COLOR="Green"]NUM[/COLOR]=$([COLOR="Blue"]ls -l /media/Sony-A350/DCIM/100MSDCF/ | grep -v ^l | wc -l[/COLOR] )
count=0
[COLOR="Blue"]ls -p /media/Sony-A350/DCIM/100MSDCF/ | grep -v '/'[/COLOR] | while read file;
do
count=[COLOR="Orange"]`expr $count + 1`[/COLOR]
[COLOR="Green"]FILENAME[/COLOR]="${file##*/}";
echo "#/media/Sony-A350/DCIM/100MSDCF/$FILENAME" 
[COLOR="Green"]MODDATE[/COLOR]=$(stat -c %y "/media/Sony-A350/DCIM/100MSDCF/$FILENAME")
[COLOR="Green"]MODDATE[/COLOR]=${MODDATE%% *}
IFS="-"
set -- [COLOR="DarkRed"]$MODDATE[/COLOR]
array=( $@ )
[COLOR="Green"]NAME[/COLOR]="/media/Movies/BackupDrive/Photos/Joshs/test/${array[0]}/${array[1]}/${array[2]}";
mkdir -p "$NAME";
cp "/media/Sony-A350/DCIM/100MSDCF/$FILENAME" $NAME;
rm "/media/Sony-A350/DCIM/100MSDCF/$FILENAME"
echo "scale=10;($count/$NUM)*100" | bc
done
echo "#Files Fnished Copying"
) |
  zenity --progress \
          --title="Downloading Photos From Sony-A350" \
          --text="" \
         --percentage=0
exit 0


```

Hmmm, you should check out the following links:
[[COLOR="Red"]UsingUUID[/COLOR]]("https://help.ubuntu.com/community/UsingUUID")

[COLOR="Blue"]BashFAQ 004[/COLOR] (link in my signature).

[[COLOR="Blue"]ParsingLS[/COLOR]]("http://mywiki.wooledge.org/ParsingLs")

[[COLOR="Orange"]Arithmetic Expression[/COLOR]]("http://mywiki.wooledge.org/ArithmeticExpression")


You should use "[COLOR="DarkRed"]double quotes[/COLOR]" around expansions and 'single quotes' to prevent Bash expansion. See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)


...[COLOR="Green"]and,, in Bash[/COLOR], by convention, we capitalize environment variables (PAGER, EDITOR, SHELL, ...) and internal shell variables (BASH_VERSION, RANDOM, ...). All other variable names should contain at least one lowercase letter. Variable names are case-sensitive; this convention avoids accidentally overriding environmental and internal variables.

---

### Post by galvatron408 on 2012-02-02
do what vaphell said... just put a while loop and test to see if the dir exists.

---

### Post by Nakira89 on 2012-02-03
Wow so much useful help, thanks all, i will try it out later on today and let you know how it goes.
Much appreciated all,

Josh.

---

### Post by Nakira89 on 2012-02-03
Ok, I've made a few changes, but still nothing works.
I've made the majority of the changes suggested here, except the ls ones, will change them at a later date though.
Here is the script again:
```
#!/bin/bash
while true; do if [ -d /media/Sony-A350/DCIM/100MSDCF/ ]; then break; fi; sleep 1; done
(
touch "/mediaSony-A350/DCIM/100MSDCF/text.txt"
Num=$(ls -l /media/Sony-A350/DCIM/100MSDCF/ | grep -v ^l)
Count=0
ls -p /media/Sony-A350/DCIM/100MSDCF/ | grep -v '/' | while read file;
do
((Count++))
Filename="${file##*/}";
echo "#/media/Sony-A350/DCIM/100MSDCF/$Filename" 
ModDate=$(stat -c %y "/media/Sony-A350/DCIM/100MSDCF/$Filename")
ModDate=${ModDate%% *}
IFS="-"
set -- "$ModDate"
array=( $@ )
Name="/media/Movies/BackupDrive/Photos/Joshs/test/${array[0]}/${array[1]}/${array[2]}";
mkdir -p "$Name";
cp "/media/Sony-A350/DCIM/100MSDCF/$Filename" $Name;
rm "/media/Sony-A350/DCIM/100MSDCF/$Filename"
echo "scale=10;($Count/$Num)*100" | bc
done
echo "#Files Finished Copying"
) |
  zenity --progress \
          --title="Downloading Photos From Sony-A350" \
          --text="" \
         --percentage=0
exit 0

```and i've used the UUID for mounting it in fstab:
```
UUID=4DCC-F3FA    /media/Sony-A350    vfat    auto,users,rw,umask=000 0 0
```Also, a problem I'm having is that it creates numerous entries for Sony-A350 in the computer, i think its only mounted in one location, but appears more than once. I can upload a screen-shot if you wish?

Anyway, i really hope you can all help me out, regards,
Josh.

---

### Post by sudodus on 2012-02-03
> **Nakira89 said:**
> I'm trying to write a bash script that will automatically transfer the photos from the camera to a folder sorted by date.
...
Are you doing it for fun, to make a new photo organizing program or would you like to take a short-cut and start using a program, that is already doing it? In that case, have a look at ***Shotwell*** and ***DigiKam***. They are available from the repositories and can be easily installed using ***apt-ge***t or ***Synaptic***.

---

### Post by Nakira89 on 2012-02-03
> **sudodus said:**
> Are you doing it for fun, to make a new photo organizing program or would you like to take a short-cut and start using a program, that is already doing it? In the third case, have a look at ***Shotwell*** and ***DigiKam***. They are available from the repositories and can be easily installed using ***apt-ge***t or ***Synaptic***.
Mainly doing it for fun, Im tryig to get it to copy all phot's off when the camera is plugged in, all photo's going into folders in hierarchy like 2012 -> 02 -> 03 for pictures taken today.
It should then remove the photos from the camera once they are copied.
Thanks for that though.

---

### Post by sudodus on 2012-02-03
Then you might be interested in the following thread

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1839153_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1839153")

---

### Post by Vaphell on 2012-02-03
maybe add some ```
echo .... >> ~/log.file
``` here and there to provide some debugging info (values of variables, steps in the procedure) and see what happens/where the script fails.

---

