---
title: "crontab stops halfway through my script"
date: 2010-02-24
forum: General Help
---

### Post by crimius on 2010-02-24
hi.  I am trying to schedule a script that changes my wallpaper to run every so often, maybe 15 minutes lets say, via crontab.  the entry is like this:

```
*/15 * * * * $HOME/wall.sh > $HOME/wallsh.txt
```

wall.sh has +x permission, and is listed below
```

cd "/media/OTHER STUFF/stuff/pics/misc/jpegs/meow/"
filepath=$(pwd)
echo "filepath generated"
random.choice() { echo $(eval echo \${$(($RANDOM%$#+1))} ) ; }
echo "random choice method built"
randomfile=$(random.choice *.jpg)
echo "random file selected"
randompic="$filepath"/$randomfile
echo "path and file concatenated"
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$randompic"
echo "wallpaper changed"

```

the echos are just there for tracking purposes.  the only one that gets logged in wallsh.txt is at line 3, echo "filepath generated".

any ideas on why it doesn't run the entire script?

---

### Post by gmargo on 2010-02-24
You are using **bash**-isms, but your script is being run by **dash** (the default "sh").

Put this as the first line of the script file:
```

#!/bin/bash

```

---

### Post by crimius on 2010-02-24
now it runs through the script all the way, all the echos appear, however it doesn't change my wallpaper and it doesn't out any errors to wallsh.txt

I'll keep playing with it, thanks for your help gmargo

EDIT: it does this after I prepended #!/bin/bash to the script

---

### Post by rnerwein on 2010-02-24
hi
i am not shure, but i am using crontab for "zenity" and i have to set the DISPLAY in my script because zenity is a graphical aplication. i don't know the gconftool-2 but i guess there you have to set the DISPLAY too.
my script:
#!/bin/bash
DISPLAY=:0
export DISPLAY
....
....

this works.
gook luck

ciao

---

### Post by crimius on 2010-02-24
tried this; observed no change in behaviour.  still ran through it all and echod the echos, but no change in wallpaper.  script still runs fine on it's own, however.

edit:  revised script posted
```
#!/bin/bash
DISPLAY=:0
export DISPLAY
cd "/media/OTHER STUFF/stuff/pics/misc/jpegs/meow/"
filepath=$(pwd)
echo "filepath generated"
random.choice() { echo $(eval echo \${$(($RANDOM%$#+1))} ) ; }
echo "random choice method built"
randomfile=$(random.choice *.jpg)
echo "random file selected"
randompic="$filepath"/$randomfile
echo "path and file concatenated"
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$randompic"
echo "wallpaper changed"

```

---

### Post by gmargo on 2010-02-24
Here's the problem.  I speculated that **gconftool** was dependent on an environment variable, and sure enough, the first one I tried was **DBUS_SESSION_BUS_ADDRESS**.  When I copied that from my desktop environment to the cron script, it worked!

Since that's a dynamic string, it looks like you won't be able to run **gconftool** from a cron script.  There must be some way to automate running a script under gnome so that it would get the proper environment.

---

### Post by whiskeylover on 2010-02-24
This is my script.

```

DIR="blah"
PIC=$(ls $DIR/*.jpg | shuf -n1)
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC
gconftool -t string -s /desktop/gnome/background/picture_options scaled
```

And it works.

---

### Post by gmargo on 2010-02-24
> **gmargo said:**
> There must be some way to automate running a script under gnome so that it would get the proper environment.

[https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)

Go to System -> Preferences -> Startup Applications and you can make any shell script run on startup, and it gets the proper desktop environment.  Just use a sleep loop instead of cron.

---

### Post by crimius on 2010-02-24
thanks for all your help gmargo, that works.  whiskeylover:  that code causes issues with my setup, and won't execute for me.  it doesn't read .../*.jpg as a wildcard.

thanks for the help, both of you. :D

---

