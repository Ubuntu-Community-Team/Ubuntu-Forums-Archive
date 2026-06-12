---
title: "Bash script help"
date: 2010-10-10
forum: General Help
---

### Post by inameiname on 2010-10-10
I have a simple bash script I found on the net which can auto-start any program and run it for a specified time allotted. 

Now, what I'd like to do is to make it so when run, instead of having it run the program already listed in the script (under 'progID' as you can see in the scripts below), it opens a simple box that asks what program desired, so I can run it and use it for any program I want in the moment. 

Another possible tweak would be to do the same with the length it runs as well, if possible. 

The following is the original script and the second is my 'attempt' at finding the right code (which currently doesn't work):

```

#!/bin/bash
#sample script to start a program, permit it to run for a predefined amount of wallclock time, then kill it.  Specify time in seconds
#
progID="smplayer"
$progID &
mypid=`eval ps ax|grep "$progID"|grep -iv "grep"| awk '{print $1}'`
echo "mypid $mypid"
maxtime="5"
mins=0
secs=0
killmins=5
startsecs=`eval date | awk '{print $4}'| awk -F\: '{print $3}'`
starthours=`eval date |awk '{print $4}'| awk -F\: '{print $1}'`
startmins=`eval date |awk '{print $4}'| awk -F\: '{print $2}'`
while [ $secs -lt $killmins ]; do
  cursecs=`eval date | awk '{print $4}'| awk -F\: '{print $3}'`
  curhours=`eval date |awk '{print $4}'| awk -F\: '{print $1}'`
  curmins=`eval date |awk '{print $4}'| awk -F\: '{print $2}'`
  secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))
  sleep 1
done
kill "$mypid"

``````

#!/bin/bash
#sample script to start a program, permit it to run for a predefined amount of wallclock time, then kill it.  Specify time in seconds
#
progID="(zenity --entry --text="Type the name of the program you wish to start and run (eg. smplayer, firefox, bleachbit)""
$progID &
mypid=`eval ps ax|grep "$progID"|grep -iv "grep"| awk '{print $1}'`
echo "mypid $mypid"
maxtime="5"
mins=0
secs=0
killmins=5
startsecs=`eval date | awk '{print $4}'| awk -F\: '{print $3}'`
starthours=`eval date |awk '{print $4}'| awk -F\: '{print $1}'`
startmins=`eval date |awk '{print $4}'| awk -F\: '{print $2}'`
while [ $secs -lt $killmins ]; do
  cursecs=`eval date | awk '{print $4}'| awk -F\: '{print $3}'`
  curhours=`eval date |awk '{print $4}'| awk -F\: '{print $1}'`
  curmins=`eval date |awk '{print $4}'| awk -F\: '{print $2}'`
  secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))
  sleep 1
done
kill "$mypid"

```

---

### Post by KiLaHuRtZ on 2010-10-10
Why not just pass in variables for it?

./my-script [MY PROGRAM] [RUN TIME]

```
#!/bin/bash
#sample script to start a program, permit it to run for a predefined amount of wallclock time, then kill it.  Specify time in seconds
#
progID="[COLOR="Red"]$1[/COLOR]"
$progID &
mypid=`eval ps ax|grep "$progID"|grep -iv "grep"| awk '{print $1}'`
echo "mypid $mypid"
maxtime="[COLOR="Red"]$2[/COLOR]"
mins=0
secs=0
killmins=5
startsecs=`eval date | awk '{print $4}'| awk -F\: '{print $3}'`
starthours=`eval date |awk '{print $4}'| awk -F\: '{print $1}'`
startmins=`eval date |awk '{print $4}'| awk -F\: '{print $2}'`
while [ $secs -lt $killmins ]; do
  cursecs=`eval date | awk '{print $4}'| awk -F\: '{print $3}'`
  curhours=`eval date |awk '{print $4}'| awk -F\: '{print $1}'`
  curmins=`eval date |awk '{print $4}'| awk -F\: '{print $2}'`
  secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))
  sleep 1
done
kill "$mypid"
#!/bin/bash
```

---

### Post by inameiname on 2010-10-10
Probably because I didn't know how to do that. :P Thanks for the suggestion.

It still would be best I think to figure out how to do it the way I'd like, as your method requires to run in a terminal, and I was hoping to be able to just double click the script, or open it as a nautilus script, and it automatically opens a box asking for the program, and the time.

Thanks again though; it's definitely something.

---

### Post by inameiname on 2010-10-10
Bump

---

### Post by inameiname on 2010-10-12
bump

---

### Post by lykeion on 2010-10-12
Try this zenity line instead:
[PHP]progID=$(zenity --entry --text="text...")[/PHP]

---

### Post by inameiname on 2010-10-12
Thank you. That worked. I changed the time for it to be killed in the same way as well, so now it works just how I'd like. I also removed 'maxtime-"$2"' as I don't think it was necessary:

```

#!/bin/bash
#sample script to start a program, permit it to run for a predefined amount of wallclock time, then kill it.  Specify time in seconds
#
progID=$(zenity --entry --text="What is the desired program you would like to run?")
$progID &
mypid=`eval ps ax|grep "$progID"|grep -iv "grep"| awk '{print $1}'`
echo "mypid $mypid"
mins=0
secs=0
killmins=$(zenity --entry --text="How long would you like it to run? (in seconds)")
startsecs=`eval date | awk '{print $4}'| awk -F\: '{print $3}'`
starthours=`eval date |awk '{print $4}'| awk -F\: '{print $1}'`
startmins=`eval date |awk '{print $4}'| awk -F\: '{print $2}'`
while [ $secs -lt $killmins ]; do
  cursecs=`eval date | awk '{print $4}'| awk -F\: '{print $3}'`
  curhours=`eval date |awk '{print $4}'| awk -F\: '{print $1}'`
  curmins=`eval date |awk '{print $4}'| awk -F\: '{print $2}'`
  secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))
  sleep 1
done
kill "$mypid"

```

---

### Post by inameiname on 2010-10-12
Nevermind. It popped up this error for some reason. I ran it from the terminal just to see why when I ran 'Opera' for the heck of it, and set it for '60 seconds', it would close at like 20 seconds:

```

 ./Run-Program-On-A-Timer.sh
mypid 20498
./Run-Program-On-A-Timer.sh: line 18: 08: value too great for base (error token is "08")
Failed to discover whether data is available [select]: Interrupted system call

```
Looking at Line 18, this is what's causing the error. It's obviously some substitution error that I don't quite get yet:

secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))

---

### Post by inameiname on 2010-10-12
Ok, I think I've got it fixed. I found a slightly different version, and for some reason I'm not getting that occasional error. So hopefully this will stay fixed:

```

#!/bin/bash
#sample script to start a program, permit it to run for a predefined amount of wallclock time, then kill it.  Specify time in seconds
#
progID=$(zenity --entry --text="What is the desired program you would like to run?")
$progID &
mypid=`eval ps ax|grep "$progID"|grep -iv "grep"| awk '{print $1}'`
echo "mypid $mypid"
mins=0
secs=0
killmins=$(zenity --entry --text="How long would you like it to run? (in seconds)")
startsecs=`eval date +%-S `
starthours=`eval date +%-H`
startmins=`eval date +%-M`

#echo "startsecs=$startsecs starthours=$starthours startmins=$startmins"

while [ $secs -lt $killmins ]; do
    cursecs=`eval date +%-S `
    curhours=`eval date +%-H`
    curmins=`eval date +%-M`
    echo "Aval..."
    secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))
    echo "Secs: $secs"
    sleep 1
done
kill "$mypid"
if [ $? -eq 0 ]; then
    echo "Process $mypid was killed"
fi

```

---

