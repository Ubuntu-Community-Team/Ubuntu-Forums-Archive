---
title: "Desktop Background Colour Changer - not working"
date: 2010-04-06
forum: General Help
---

### Post by CraigThomas on 2010-04-06
I have been successfully using a transparent wallpaper (as found [_here_]("http://ubuntuforums.org/showpost.php?p=6316408&postcount=26")) for a while.  It's great I can get the same design in many, many colours just by changing the solid background colour.

I fancied automating this and changing the background colour every hour.  But I didn't want to have anything running continually in the background so I decided I just want a simple (bash) script which could be set as a cron job.

I have created the script and it seems to change the background colour (using 'gconftool-2 --get ..' it reports that it has changed) but the desktop doesn't update to show the new colour.  Am I doing something wrong or can this not be done?

Here's my script:
```

#!/bin/sh

#set a default background colour to use if anything goes wrong
CURRCOL="#000000";	#black

#get background colour
CURRCOL=$(gconftool-2 --get /desktop/gnome/background/primary_color);
#echo $BACKCOL;

#find first and last colours in the list
FIRSTCOL=$(head colours.txt --lines=1);
LASTCOL=$(tail colours.txt --lines=1);

if [ "$CURRCOL" = "$LASTCOL" ]; then
	NEWCOL=$FIRSTCOL
	echo "Last Colour"
else
	echo "Not Last Colour"
	#find current colour in list, then use tail to find next colour
	NEWCOL=$(grep -A 1 $CURRCOL ~/Scripts/colours.txt | tail --lines=1)
	if [ "$NEWCOL" = "" ]; then
		#if current colour is not in the list reset it to black
		NEWCOL="#000000"	#black
	fi
fi

echo $NEWCOL

#set background colour
gconftool-2 -t str --set /desktop/gnome/background/primary_color $NEWCOL;
```

and a sample of the colours.txt file:
```

#000000
#000080
#00008B
#0000CD
#0000FF
#006400
#008000
#008080
#008B8B
#00BFFF

```

I'm aware of this [_Howto change background color with a script_]("http://ubuntuforums.org/showthread.php?t=1392177&highlight=gconftool-2+background+color") thread but just want to use a bash script in a cron job.

Be gentle I'm new to Linux and it took me a while to get this far.

---

### Post by CraigThomas on 2010-04-06
Here's some output too: (with my debugging bits left in)

```

c@a:~/Scripts$ sh backcolour.sh
Not Last Colour
#000000
c@a:~/Scripts$ sh backcolour.sh
Not Last Colour
#000080
c@a:~/Scripts$ sh backcolour.sh
Not Last Colour
#00008B
c@a:~/Scripts$ sh backcolour.sh
Not Last Colour
#0000CD
c@a:~/Scripts$ sh backcolour.sh
Not Last Colour
#0000FF

```

---

### Post by gmargo on 2010-04-06
It won't work for gnome, from cron.
The difference is the DBUS_SESSION_BUS_ADDRESS environment variable.
Without it the changes don't get through to gnome.  At least in my experience.  Another thread reported that setting the DISPLAY variable worked, but it didn't for me.

---

### Post by CraigThomas on 2010-04-07
Thanks gmargo.  It appears you are right, I've hit a brick wall.  My script now works fine from a terminal but the cron job isn't working.

If anyone else can offer any help I'd be grateful, otherwise I'm restricted to call it from a terminal or a desktop launcher whenever I want a different colour.

Here's the code as it stands:
```

#!/bin/sh

#apparently allows this script to work when run from a cron job

# This function required in order to run gconftool-2 from cron
# ======================================================
function export_variables
{
   user=$( whoami )
   pid=$( pgrep -u $user gnome-panel )
 
   for dbusenv in $pid; do
 	DBUS_SESSION_BUS_ADDRESS=$( grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//' )

 	data="DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS"
        eval " export $data"
    done
}
# ======================================================
export_variables
# ======================================================



#get background colour
CURRCOL=$(gconftool-2 --get /desktop/gnome/background/primary_color);

#find first and last colours in the list
FIRSTCOL=$(head ~/Scripts/colours.txt --lines=1);
LASTCOL=$(tail ~/Scripts/colours.txt --lines=1);

#if last colour go back to the first colour
if [ "$CURRCOL" = "$LASTCOL" ]; then
	NEWCOL=$FIRSTCOL
else
	#if not last colour
	#find current colour in list, then use tail to find next colour, then trim any line feed or carriage returns
	NEWCOL=$(grep -A 1 $CURRCOL ~/Scripts/colours.txt | tail --lines=1 | tr -d '\n' | tr -d '\r')
fi

#set the new background colour
gconftool-2 -t str --set /desktop/gnome/background/primary_color $NEWCOL;

```

Note. Above you can see I've added in a function I came across several times which supposedly should help but doesn't (can be seen at the top of my script).
I also tried putting this code (found in another thread) into the start of my script (without success):
```

export $(xargs -n 1 -0 echo </proc/$(pidof x-session-manager)/environ | grep -Z DBUS_SESSION_BUS_ADDRESS=)

```

This is all new to me but I think Cron is setup correctly (running every minute whilst testing):
```

* * * * * /home/craig/Scripts/backcolour.sh # JOB_ID_1

```
Is there anyway I can find out if cron, my cron job or a test job is running or has run?

If it helps at all, I'm using a pretty standard install of Ubuntu 9.10 with all the latest updates.

---

### Post by gmargo on 2010-04-07
I would just run it as a script started from the Startup Applications list.  You said you didn't want a loop in the background, but why not?  The main issue I have with loops started from Startup Applications is that they don't get killed on logout, unless somehow attached to the desktop.  But I figured out a way around that.  Here's my wrapper script around a background changer script, which exits after the gnome session goes away.
```

#!/bin/sh

while :
do
    # When gnome exits, our parent process becomes init,
    # but the PPID stays set.
    if ! ps -p $PPID > /dev/null
    then
        exit 0
    fi
    /home/gmargo/bin/change_background.sh
    sleep 60
done


```> Is there anyway I can find out if cron, my cron job or a test job is  running or has run?Have it write to a file. Just "date >> $HOME/file.txt" is enough isn't it? Or check the /var/log/syslog file.

---

