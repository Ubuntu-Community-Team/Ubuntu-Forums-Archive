---
title: "Howto change background color with a script"
date: 2010-01-27
forum: General Help
---

### Post by CJN on 2010-01-27
I don't know much about scripting and so despite my best efforts i can't seem to get my script right and I was wondering how to do the following:

at startup set the background color to a certain hex value
over time cycle through the entire range of possible values from (0x000000 to 0xFFFFFF)
do this slowly, not abruptly
start the script every time I login

I know I need to use 

gconftool-2 -t str --set /desktop/gnome/background/primary_color "#$COLOR"

where COLOR is a hex value variable

but really beyond that the specifics of how to time the updating of the hex value or whether a variable can be a hex value at all (if not how to work around that).

---

### Post by CJN on 2010-01-28
I have this so far:

#! /bin/bash
# while logged in and running...
COLOR="0"
while [ $COLOR -lt 16777216 ]
do
COLOR=$[$COLOR+1]
#sleep 1
COLORHEX="ibase=10; obase=16; $COLOR"
gconftool-2 -t str --set /desktop/gnome/background/primary_color "#$COLORHEX"
done
#done

but it stays at black, and does not cycle... any ideas?

---

### Post by CJN on 2010-01-28
Ok so i got it working by "learning" perl and rewriting it in perl, but now I can't seem to make it run after I log in, I followed a couple tutorials and howtos online but to no avail, anybody can help with this at least?

---

### Post by CJN on 2010-01-28
I got it to launch with startup applications, so I guess that's that.

---

### Post by Simme on 2010-01-30
Hi!

Today I stumbled upon the same problem... is it possible to post your finished script?
I would be very happy about a colorful desktop :)

---

### Post by pbrane on 2010-01-30
try this

```

#!/bin/bash
# cycle through colors on the desktop root window
 
COLOR=0
while [ $COLOR -lt 16777216 ]
do
    COLOR=$[$COLOR+1]
    COLORHEX=$(echo "obase=16; $COLOR" | bc)
    COLORPADDED=$(echo "$COLORHEX" | awk '{printf "#%012s\n",$0}')
#   sleep for some duration?

    gconftool-2 -t string --set /desktop/gnome/background/primary_color "#$COLORPADDED"
 done

```

put this script in the directory of your choice and make it executable by typing **chmod u+x *name_of_script*** in a terminal. Then add the script to your Startup Applications

CJN:

I think the reason your script failed is because you assigned COLOR="0" with double quotes you made the zero a string. Then you tried to use it as a number. Also the output was not padded to 12 places, not sure if that really matters to gconf or not.

---

### Post by CJN on 2010-02-01
The script is here: [http://www.ualberta.ca/~narzt/Silvers_Shadows/Portfolio/Entries/2010/1/31_Ubuntu_Linux_Desktop_Customization_files/perlScript.pl]("http://www.ualberta.ca/%7Enarzt/Silvers_Shadows/Portfolio/Entries/2010/1/31_Ubuntu_Linux_Desktop_Customization_files/perlScript.pl")

---

### Post by noreun on 2011-07-21
> **pbrane said:**
> try this

```

#!/bin/bash
# cycle through colors on the desktop root window
 
COLOR=0
while [ $COLOR -lt 16777216 ]
do
    COLOR=$[$COLOR+1]
    COLORHEX=$(echo "obase=16; $COLOR" | bc)
    COLORPADDED=$(echo "$COLORHEX" | awk '{printf "#%012s\n",$0}')
#   sleep for some duration?

    gconftool-2 -t string --set /desktop/gnome/background/primary_color "#$COLORPADDED"
 done

```

put this script in the directory of your choice and make it executable by typing **chmod u+x *name_of_script*** in a terminal. Then add the script to your Startup Applications

CJN:

I think the reason your script failed is because you assigned COLOR="0" with double quotes you made the zero a string. Then you tried to use it as a number. Also the output was not padded to 12 places, not sure if that really matters to gconf or not.


New version: for gradient background, random initial colors, increase by a step, sleep time, loop for ever (not really a shell script programmer, but it works... :) )

```

#!/bin/bash
# cycle through colors on the desktop root window
 
COLORP=$(rand -M 16777215)
sleep 1
COLORS=$(rand -M 16777215)
STEP=20
SLEEPTIME=10
while [ 1 ]
do
    COLORP=$[$COLORP+$STEP]
    if test $COLORP -gt 16777215
    then
        COLORP=0
    fi
    COLORPHEX=$(echo "obase=16; $COLORP" | bc)
    COLORPPADDED=$(echo "$COLORPHEX" | awk '{printf "#%s\n",$0}')

    COLORS=$[$COLORS-$STEP]
    if test $COLORP -lt 0
    then
        COLORS=16777215
    fi
    COLORSHEX=$(echo "obase=16; $COLORS" | bc)
    COLORSPADDED=$(echo "$COLORSHEX" | awk '{printf "#%s\n",$0}')

    echo $COLORPPADDED
    gconftool-2 -t string --set /desktop/gnome/background/primary_color "$COLORPPADDED"
    
    echo "$COLORSPADDED"
    gconftool-2 -t string --set /desktop/gnome/background/secondary_color "$COLORSPADDED" 

    sleep $SLEEPTIME

done

```

---

