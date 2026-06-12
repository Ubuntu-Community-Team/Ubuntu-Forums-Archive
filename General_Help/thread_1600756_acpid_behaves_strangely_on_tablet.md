---
title: "acpid behaves strangely on tablet"
date: 2010-10-19
forum: General Help
---

### Post by nikosm on 2010-10-19
Hi all,

I have followed [this guide]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_an_X61_Tablet#Setup_Automatic_Screen_Rotation") to setup automatic screen rotation on a fresh installation of Maverick on a Lenovo X200t. This involves creating the file

```
$cat /etc/acpi/events/x200t-swivel-down 
# /etc/acpi/events/x200t-swivel-down
# called when tablet head swivels down
event=ibm/hotkey HKEY 00000080 00005009
action=/etc/acpi/x200t-swivel-down.sh
```

and the script
```
$cat /etc/acpi/x200t-swivel-down.sh 
#!/bin/sh
/usr/bin/xrandr -o inverted
touch /home/nikos/Desktop/swivel-down
xsetwacom set "Serial Wacom Tablet stylus" Rotate half
xsetwacom set "Serial Wacom Tablet touch" Rotate half
xsetwacom set "Serial Wacom Tablet eraser" Rotate half
```
(similar for swivel-up)

What I find strange:
 - calling the script with ./x200t-swivel-down.sh works (both with and without sudo).
 - rotating the screen to tablet mode only executes the touch commands (which I entered for debugging)

Obviously, the acpi event is registered correctly and reacted upon. Just why are the xrandr and xsetwacom commands ignored?

Any ideas?

Thanks,
Nikos

---

### Post by orwellsbrother on 2010-10-25
Hi Nikos,

I am using the same script on my X201t. Since Maverick I had to change the rotation part to:

```
for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
#    getXconsole;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum.0"           
        /usr/bin/xrandr -d $DISPLAY -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation
    fi
done
```which works for me. For the xsetwacom scripts I had to put it like this:
```
for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
#        getXconsole;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum.0"
          /usr/bin/xsetwacom -d $DISPLAY set "Serial Wacom Tablet eraser" Rotate $NEW_ROTATION
          /usr/bin/xsetwacom -d $DISPLAY set "Serial Wacom Tablet touch" Rotate $NEW_ROTATION
          /usr/bin/xsetwacom -d $DISPLAY set "Serial Wacom Tablet stylus" Rotate $NEW_ROTATION
        fi
done

```Regards,

Sebastian

---

### Post by nikosm on 2010-10-26
Thank you for the suggestion Sebastian!

I tried your script by itself, and it works fine for me as well. I tried just the xrandr command with acpid (in the loop that you wrote), restarted acpid and it worked! But then I edited it to add the xsetwacom commands and it strangely stopped working (when called by acpid). 

The current state is that both your script and my old scripts work as expected when run from the terminal but when acpid is responsible for calling them only my debugging-purpose touch commands get executed...

Could this be a permissions problem? All three (my two old scripts or the one suggested by you, Sebastian) have the same permissions:
```
-rwxrwxr-x 1 root root 741 2010-10-25 21:51 rotatescreen.sh
-rwxrwxr-x 1 root root 853 2010-10-25 22:10 x200t-swivel-down.sh
-rwxrwxr-x 1 root root 607 2010-10-25 21:57 x200t-swivel-up.sh

```

Any ideas?

Thanks again,
Nikos

---

### Post by nikosm on 2010-11-15
bump. any ideas anybody?

---

