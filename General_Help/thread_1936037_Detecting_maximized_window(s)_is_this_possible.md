---
title: "Detecting maximized window(s) is this possible?"
date: 2012-03-05
forum: General Help
---

### Post by EgoGratis on 2012-03-05
Is there a way i could detect maximized window(s) in Ubuntu (Gnome 3) and do that reliable? And if it is is there a way i could run a script that would do one thing when it would detect maximized window(s) and another when there would be no maximized window(s)?

Thanks!

---

### Post by stinkeye on 2012-03-05
Have a look at wmctrl.
eg on my res of 1680x1050 in unity, maximized windows show "1630 x 1026" dimension.
```
[COLOR="SeaGreen"]glen@Oneiric:~$ **wmctrl -lpG**[/COLOR]
0x01600004  0 30241  0    0    1680 1050 Oneiric Desktop
0x02c00002  0 0      -1780 -1150 1680 1050     N/A DNDCollectionWindow
0x02c00003  0 0      0    24   50   1026     N/A launcher
0x02c00004  0 0      0    0    1680 24       N/A panel
0x01000004  0 30227  1362 0    48   24   Oneiric compiz
0x03c00002  0 0      65   440  410  610  Oneiric conkygmail
0x03e00002  0 0      489  39   602  302  Oneiric sbreeze
0x04000002  0 0      1108 38   564  429  Oneiric myconky
0x04600002  0 0      1337 69   104  17   Oneiric Conky (Oneiric)
0x0480000d  0 31079  1200 598  300  300  Oneiric MacSlow's Cairo-Clock
0x0440001d  0 31338  50   24   1630 1026 Oneiric Ubuntu Forums - Reply to Topic - Opera
0x04e00006  0 17273  112  302  1212 686  Oneiric glen@Oneiric: ~
0x0160037a  0 30241  50   24   1630 1026 Oneiric Home

[COLOR="seagreen"]glen@Oneiric:~$ **wmctrl -lpG | grep "1630 1026"**[/COLOR]
0x0440001d  0 31338  50   24   1630 1026 Oneiric Ubuntu Forums - Reply to Topic - Opera
0x0160037a  0 30241  50   24   1630 1026 Oneiric Home
```

Grep can be used with a count option
eg
```
[COLOR="SeaGreen"]glen@Oneiric:~$ **wmctrl -lpG | grep -c "1630 1026"**[/COLOR]
2
```


```
#!/bin/bash

MAXIMIZED=$(wmctrl -lpG | grep -c "1630 1026")

if [ "$MAXIMIZED" == "0" ]; then
	notify-send "None Maximized"
else
	notify-send "$MAXIMIZED Maximized"

fi
```

Only seems to work when run in terminal though???

---

### Post by EgoGratis on 2012-03-05
I tried it and it works. Fantastic! Now could this be done. 

If output of command:

```
wmctrl -lpG | grep -c "x y"
```Returns 0 it reads:

```
gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode"
```If output is not 0 then:

```
gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
```If output of command:

```
wmctrl -lpG | grep -c "x y"
```Is not 0 then it reads:

```
gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode"
```If output is not 1 then:

```
gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
```I found it here:

[http://askubuntu.com/questions/41241/shortcut-to-change-launcher-hide-setting](http://askubuntu.com/questions/41241/shortcut-to-change-launcher-hide-setting)

And last but not least this should always run in the background and monitor behavior automatically and act accordingly. What would be the best way to do this? It's complex i know but i hope somebody knows the answer and solution and i hope it can be done and that it will work well too! Any suggestion?

---

### Post by stinkeye on 2012-03-05
I'm just an amateur "learn by mistakes" scripter so I'll leave it up to someone who will do it properly.
Probably just need a **while true; do** loop to run in background.

---

### Post by EgoGratis on 2012-03-05
> I'm just an amateur "learn by mistakes" scripter

That solved important piece of the puzzle! Thanks!

---

### Post by EgoGratis on 2012-03-06
Based on your valuable input i managed to do this:

```
#!/bin/bash
# Install wmctrl before using: sudo apt-get install wmctrl

while true; do
sleep 2 # Set delay

SHOW_LAUNCHER=$(wmctrl -lpG | grep -c "x y") # Use wmctrl -lpG and find max value when Launcher is in neverhide mode
HIDE_LAUNCHER=$(wmctrl -lpG | grep -c "x y") # Use wmctrl -lpG and find max value when Launcher is in autohide mode

if [ $SHOW_LAUNCHER -eq 0 -a $HIDE_LAUNCHER -eq 0 ]
then
    CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
    if [ $CURRENT -ne 0 ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
    fi
else
    CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
    if [ $CURRENT -ne 1 ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
    fi
fi
done
```

It works in Unity 3D on single screen/workspace and yes it "imitates" Dodge Windows in Ubuntu 12.04. For more advanced functionality more skillful programmer should probably use window manager to detect maximized widows (_NET_WM_STATE, ATOM[])

[http://standards.freedesktop.org/wm-spec/wm-spec-1.3.html](http://standards.freedesktop.org/wm-spec/wm-spec-1.3.html)

And then show/hide launcher. And Launcher should be shown on screens/workspaces that have no maximized window(s)... But that is beyond the scope of this topic. 

Thanks!

---

### Post by stinkeye on 2012-03-06
Well done.
I put in my x y values and it worked.
Maximized windows being a different size when the launcher is hidden
makes it a bit harder.

---

### Post by EgoGratis on 2012-03-06
> Maximized windows being a different size when the launcher is hidden makes it a bit harder.If you don't want to use GUI editor to set the launcher in autohide then:


```
gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
wmctrl -lpG
```This should be easy!

P.S. I think i misunderstood.

You probably thought bash script is a bit harder to make! :D

---

### Post by AleveSicofante on 2012-03-07
I want to say thanks to EgoGratis for this initiative.

To everyone: please subscribe to [this bug]("https://bugs.launchpad.net/ayatana-design/+bug/930148") if you don't agree with the decision to remove the dodge feature (instead of making it non-default) and not even replace it with a simple intellihide.

---

### Post by EgoGratis on 2012-03-11
I have got PM from stinkeye mentioning Dash doesn't work well with the script and suggested solution. I could not reproduce the problem with Dash but i noticed similar behavior with Hud. Both stinkeye and i noticed some problems when login out and in the session again or in session other that Unity 3D so i added some fixes/features:

1.) I moved all user setting to the top of the script.

2.) I added session detection the script will only run in Unity 3D.

3.) I added detection if the script is already running when login occurs. If it detects script that was left from login out of Unity 3D and login in again it closes it and starts new one. If it detects script that was left from login out of Unity 3D and login in other session than Unity 3D it closes the running script and it does not start another one.

4.) I added both Hud and Dash exceptions so they won't interfere with the script anymore!

```
#!/bin/bash
# Install wmctrl before using: sudo apt-get install wmctrl


# Change settings
DELAY="2" # Set delay

SHOW_X="X" # Use wmctrl -lpG and find max X Y values when launcher is in never hide mode
SHOW_Y="Y" 

HIDE_X="X" # Use wmctrl -lpG and find max X Y values when launcher is in autohide mode
HIDE_Y="Y"

SCRIPT_PATH="/home/user_name/launcher.sh" # Change path


# End of user settings
ps -ef | grep "$SCRIPT_PATH" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ $DESKTOP_SESSION != ubuntu ]; then
	exit 0
fi

while true; do
sleep $DELAY

SHOW_LAUNCHER=$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$SHOW_X $SHOW_Y") 
HIDE_LAUNCHER=$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$HIDE_X $HIDE_Y") 

if [ $SHOW_LAUNCHER -eq 0 -a $HIDE_LAUNCHER -eq 0 ]
then
	CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
	if [ $CURRENT -ne 0 ]
	then
		gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
	fi
else
	CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
	if [ $CURRENT -ne 1 ]
	then
		gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
	fi
fi
done
```

---

### Post by Baldrick_NZ on 2012-03-11
> **EgoGratis said:**
> I have got PM from stinkeye mentioning Dash doesn't work well with the script and suggested solution. I could not reproduce the problem with Dash but i noticed similar behavior with Hud. Both stinkeye and i noticed some problems when login out and in the session again or in session other that Unity 3D so i added some fixes/features:

1.) I moved all user setting to the top of the script.

2.) I added session detection the script will only run in Unity 3D.

3.) I added detection if the script is already running when login occurs. If it detects script that was left from login out of Unity 3D and login in again it closes it and starts new one. If it detects script that was left from login out of Unity 3D and login in other session than Unity 3D it closes the running script and it does not start another one.

4.) I added both Hud and Dash exceptions so they won't interfere with the script anymore!

```
#!/bin/bash
# Install wmctrl before using: sudo apt-get install wmctrl


# Change settings
DELAY="2" # Set delay

SHOW_X="X" # Use wmctrl -lpG and find max X Y values when launcher is in never hide mode
SHOW_Y="Y" 

HIDE_X="X" # Use wmctrl -lpG and find max X Y values when launcher is in autohide mode
HIDE_Y="Y"

SCRIPT_PATH="/home/user_name/launcher.sh" # Change path


# End of user settings
ps -ef | grep "$SCRIPT_PATH" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ $DESKTOP_SESSION != ubuntu ]; then
	exit 0
fi

while true; do
sleep $DELAY

SHOW_LAUNCHER=$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$SHOW_X $SHOW_Y") 
HIDE_LAUNCHER=$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$HIDE_X $HIDE_Y") 

if [ $SHOW_LAUNCHER -eq 0 -a $HIDE_LAUNCHER -eq 0 ]
then
	CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
	if [ $CURRENT -ne 0 ]
	then
		gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
	fi
else
	CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
	if [ $CURRENT -ne 1 ]
	then
		gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
	fi
fi
done
```

For the uninitiated, how does one actually apply this script? Do you just open terminal and cut and paste, or something else?

Any help would be much appreciated.

Cheers.

---

### Post by stinkeye on 2012-03-11
> **Baldrick_NZ said:**
> For the uninitiated, how does one actually apply this script? Do you just open terminal and cut and paste, or something else?

Any help would be much appreciated.

Cheers.
Firstly install **wmctrl** (Search in the software centre)
and create a folder in your home directory called **scripts**.


Put the launcher into never hide mode with this terminal command...
```
gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
```
Then maximize firefox and get your maximized xy values by entering in the terminal...
```
wmctrl -lpG
```
eg```
glen@Oneiric:~$ wmctrl -lpG
0x01600004  0 1935   0    0    1680 1050 Oneiric Desktop
0x02400002  0 0      -1780 -1150 1680 1050     N/A DNDCollectionWindow
0x02400003  0 0      0    24   50   1026     N/A launcher
0x02400004  0 0      0    0    1680 24       N/A panel
0x01000004  0 1921   1380 0    24   24   Oneiric compiz
0x03a00002  0 0      65   440  410  610  Oneiric conkygmail
0x03c00002 -1 0      489  39   602  302  Oneiric sbreeze
0x03e00002  0 0      1108 38   564  412  Oneiric myconky
0x04400002  0 0      1337 69   104  17   Oneiric Conky (Oneiric)
0x0460001d  0 3060   50   24   1630 1026 Oneiric Ubuntu Forums - Reply to Topic - Opera
0x02400012  0 0      -1730 -1126 1630 1026     N/A Dash
0x04a00004  0 26518  2024 297  815  609  Oneiric launcher.sh (~/scripts) - gedit
0x04c000d1  0 28327  50   24   [COLOR="red"]1630 1026[/COLOR] Oneiric Ubuntu Start Page - **Mozilla Firefox**
0x04e00006  0 28754  770  125  902  192  Oneiric glen@Oneiric: ~
```
These are your [COLOR="red"]x y values for a maximized window with the launcher showing.[/COLOR]


Now hide the launcher with...
```
gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
```
Enter (Hint: pressing the up arrow when in the terminal will cycle through previous commands)```
wmctrl -lpG
```
and you will get your x y values when the launcher is hidden.
eg```
glen@Oneiric:~$ wmctrl -lpG
0x01600004  0 1935   0    0    1680 1050 Oneiric Desktop
0x02400002  0 0      -1780 -1150 1680 1050     N/A DNDCollectionWindow
0x02400003  0 0      -150 -1126 50   1026     N/A launcher
0x02400004  0 0      0    0    1680 24       N/A panel
0x01000004  0 1921   1380 0    24   24   Oneiric compiz
0x03a00002  0 0      65   440  410  610  Oneiric conkygmail
0x03c00002 -1 0      489  39   602  302  Oneiric sbreeze
0x03e00002  0 0      1108 38   564  412  Oneiric myconky
0x04400002  0 0      1337 69   104  17   Oneiric Conky (Oneiric)
0x0460001d  0 3060   0    24   1680 1026 Oneiric Ubuntu Forums - Reply to Topic - Opera
0x02400012  0 0      -1730 -1126 1630 1026     N/A Dash
0x04a00004  0 26518  2024 297  815  609  Oneiric launcher.sh (~/scripts) - gedit
0x04c000d1  0 28327  0    24   [COLOR="DarkOrange"]1680 1026[/COLOR] Oneiric Ubuntu Start Page - **Mozilla Firefox**
0x04e00006  0 28754  770  125  902  401  Oneiric glen@Oneiric: ~
```
These are your [COLOR="DarkOrange"]x y values for a maximized window with the launcher hidden.[/COLOR]

Open gedit and copy and paste in the script.
Edit the script to reflect your values.
eg this is the section of the script I edited for my resolution and username.
```
# Change settings
DELAY="2" # Set delay

SHOW_X="[COLOR="Red"]1630[/COLOR]" # Use wmctrl -lpG and find max X Y values when launcher is in never hide mode
SHOW_Y="[COLOR="red"]1026[/COLOR]" 

HIDE_X="[COLOR="darkorange"]1680[/COLOR]" # Use wmctrl -lpG and find max X Y values when launcher is in autohide mode
HIDE_Y="[COLOR="darkorange"]1026[/COLOR]"

SCRIPT_PATH="/home/[COLOR="Purple"]glen/scripts/[/COLOR]launcher.sh" # Change path
```
[COLOR="purple"]Change to your user name and add the scripts foder[/COLOR], then save as
**launcher.sh** in the scripts folder in your home directory.
You can save anywhere,really, just make sure "**SCRIPT_PATH=**" points to where you saved it.

Right click on the launcher.sh file
Properties > permissions and mark execute.

To test, left click on launcher.sh and choose "run in terminal".
Unmaximize all windows and then maximize one.

If it works and is what you want add it to start up applications
by browsing to where you saved the script.

---

### Post by Baldrick_NZ on 2012-03-11
Thanks for that... Do I have to use firefox, or will chrome do instead? I don't have FF installed.

Cheers.

---

### Post by stinkeye on 2012-03-11
> **Baldrick_NZ said:**
> Thanks for that... Do I have to use firefox, or will chrome do instead? I don't have FF installed.

Cheers.
Any window will do.I just tried to use any easily identifiable one.

---

### Post by EgoGratis on 2012-03-13
I noticed [how hard]("http://ubuntuforums.org/showpost.php?p=11757999&postcount=12") it is to set up the script and thought if i can do something about that!

```
#!/bin/bash
# Install wmctrl before using: sudo apt-get install wmctrl

# User settings
sleep 8 # Time it takes before script starts with autodetection

DELAY="2" # Set delay

# End of user settings

ps -ef | grep "$0" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ "$DESKTOP_SESSION" != "ubuntu" ]; then
    exit 0
fi

MAX_W="$(wmctrl -lG | awk '{if ($5 > max) { max = $5;}} END {print max}')"
MAX_H="$(wmctrl -lG | awk '{if ($6 > max) { max = $6;}} END {print max}')"

HIDE_Y="$(expr $MAX_H - 24)"

SHOW_X="$(expr $MAX_W - $(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/icon_size") - 17)"
SHOW_Y="$(expr $MAX_H - 24)"

while true; do
sleep $DELAY

SHOW_LAUNCHER="$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$SHOW_X $SHOW_Y")" 
HIDE_LAUNCHER="$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$MAX_W $HIDE_Y")"

if [ "$SHOW_LAUNCHER" -eq "0" -a "$HIDE_LAUNCHER" -eq "0" ]
then
    CURRENT="$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")"
    if [ "$CURRENT" -ne "0" ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
    fi
else
    CURRENT="$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")"
    if [ "$CURRENT" -ne "1" ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
    fi
fi
done
```

Only two setting are left and the script should work on most of the computers. If script does not work then probably 2 things happened:

1.) Scripts starts autodetection before session is loaded. Increase the sleep time.
2.) Something changed in Unity or another theme is used with different dimensions. Use [manual setup]("http://ubuntuforums.org/showpost.php?p=11757499&postcount=10") or change the script.

Installation:
-Create empty file and copy/paste the code into it. Save the file and make it executable.
-Create entry in Startup Applications and in command filed point to the script as stinkeye suggested on the picture.

Log out/ Log in and it should work. If Launcher size gets changed Log out/ Log in again and it should work again. I could probably make autodetection if launcher is changed in real-time but i think it's better if less operation gets executed in every interval!

---

### Post by Baldrick_NZ on 2012-03-13
> **EgoGratis said:**
> I noticed [how hard]("http://ubuntuforums.org/showpost.php?p=11757999&postcount=12") it is to set up the script and thought if i can do something about that!

```
#!/bin/bash
# Install wmctrl before using: sudo apt-get install wmctrl

# User settings
sleep 8 # Time it takes before script starts with autodetection

DELAY="2" # Set delay

# End of user settings

ps -ef | grep "$0" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ "$DESKTOP_SESSION" != "ubuntu" ]; then
    exit 0
fi

MAX_W="$(wmctrl -lG | awk '{if ($5 > max) { max = $5;}} END {print max}')"
MAX_H="$(wmctrl -lG | awk '{if ($6 > max) { max = $6;}} END {print max}')"

HIDE_Y="$(expr $MAX_H - 24)"

SHOW_X="$(expr $MAX_W - $(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/icon_size") - 17)"
SHOW_Y="$(expr $MAX_H - 24)"

while true; do
sleep $DELAY

SHOW_LAUNCHER="$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$SHOW_X $SHOW_Y")" 
HIDE_LAUNCHER="$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$MAX_W $HIDE_Y")"

if [ "$SHOW_LAUNCHER" -eq "0" -a "$HIDE_LAUNCHER" -eq "0" ]
then
    CURRENT="$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")"
    if [ "$CURRENT" -ne "0" ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
    fi
else
    CURRENT="$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")"
    if [ "$CURRENT" -ne "1" ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
    fi
fi
done
```

Only two setting are left and the script should work on most of the computers. If script does not work then probably 2 things happened:

1.) Scripts starts autodetection before session is loaded. Increase the sleep time.
2.) Something changed in Unity or another theme is used with different dimensions. Use [manual setup]("http://ubuntuforums.org/showpost.php?p=11757499&postcount=10") or change the script.

Installation:
-Create empty file and copy/paste the code into it. Save the file and make it executable.
-Create entry in Startup Applications and in command filed point to the script as stinkeye suggested on the picture.

Log out/ Log in and it should work. If Launcher size gets changed Log out/ Log in again and it should work again. I could probably make autodetection if launcher is changed in real-time but i think it's better if less operation gets executed in every interval!

Worked for me, thanks guys!! :p

EDIT: Well it almost worked. Worked fine when logging out/in, but on re-boot it holds the launcher at auto-hide. The script appears to override any changes you make to Ubuntu Tweak, so you can't change to never hide whilst this script is enabled. So close, but no cigar. Almost there... :-)

---

### Post by EgoGratis on 2012-03-13
> Worked fine when logging out/in, but on re-boot it holds the launcher at auto-hide.

There should not be any difference between log out/ log in and reboot. Try to increase sleep time from 8 to 16 maybe it tries to autodetect settings before session is loaded  or if u have fast PC you have to wait few seconds after login for the script to start to work.

> The script appears to override any changes you make to Ubuntu Tweak, so  you can't change to never hide whilst this script is enabled.

True, when the script is running you only get one mode: hide launcher when at least one window is maximized. If u want any other mode you have to close the script first (System Monitor).

---

### Post by EgoGratis on 2012-03-14
Race condition is not something user should think about. This should be done automatically and i added detection when autoconfiguration should start. You will not have problems any more with reboots and you don't have to set sleep time based on how fast sessions loads and if sessions loads fast there is no waiting anymore for the script to start working. There is only one setting left now and it does not need to be changed for the script to work.

```
#!/bin/bash
# Install wmctrl before using: sudo apt-get install wmctrl

# User settings
DELAY="2" # Set delay

# End of user settings
ps -ef | grep "$0" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ "$DESKTOP_SESSION" != "ubuntu" ]; then
    exit 0
fi

RACE="$(wmctrl -l | awk '{print $4}' | grep -c "panel\|launcher\|DNDCollectionWindow")"

while [ "$RACE" -lt "3" ]; do
    RACE="$(wmctrl -l | awk '{print $4}' | grep -c "panel\|launcher\|DNDCollectionWindow")"
    sleep 1
done

MAX_W="$(wmctrl -lG | awk '{if ($5 > max) { max = $5;}} END {print max}')"
MAX_H="$(wmctrl -lG | awk '{if ($6 > max) { max = $6;}} END {print max}')"

HIDE_Y="$(expr $MAX_H - 24)"

SHOW_X="$(expr $MAX_W - $(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/icon_size") - 17)"
SHOW_Y="$(expr $MAX_H - 24)"

while true; do
sleep $DELAY

SHOW_LAUNCHER="$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$SHOW_X $SHOW_Y")" 
HIDE_LAUNCHER="$(wmctrl -lpG | grep -v "Hud\|Dash" | grep -c "$MAX_W $HIDE_Y")"

if [ "$SHOW_LAUNCHER" -eq "0" -a "$HIDE_LAUNCHER" -eq "0" ]
then
    CURRENT="$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")"
    if [ "$CURRENT" -ne "0" ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
    fi
else
    CURRENT="$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")"
    if [ "$CURRENT" -ne "1" ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
    fi
fi
done
```

---

### Post by EgoGratis on 2012-03-17
-I removed all user specific settings because they are not needed and if set wrong can cause troubles.
-I added Single Screen / Multi Workspaces support.

```
#!/bin/bash
# Install wmctrl before using: sudo apt-get install wmctrl

ps -ef | grep "$0" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ "$DESKTOP_SESSION" != "ubuntu" ]; then
    exit 0
fi

RACE="$(wmctrl -l | awk '{print $4}' | grep -c "panel\|launcher\|DNDCollectionWindow")"

while [ "$RACE" -lt "3" ]; do
    RACE="$(wmctrl -l | awk '{print $4}' | grep -c "panel\|launcher\|DNDCollectionWindow")"
    sleep 1
done

MAX_W="$(wmctrl -lG | awk '{if ($5 > max) { max = $5;}} END {print max}')"
MAX_H="$(wmctrl -lG | awk '{if ($6 > max) { max = $6;}} END {print max}')"

HIDE_Y="$(expr $MAX_H - 24)"

SHOW_X="$(expr $MAX_W - $(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/icon_size") - 17)"
SHOW_Y="$(expr $MAX_H - 24)"

LAUNCHER="$(expr $(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/icon_size") + 17)"

while true; do
sleep 2

SHOW_LAUNCHER="$(wmctrl -lG | grep -v "Hud\|Dash" | awk -v LAUNCHER=$LAUNCHER '$3==LAUNCHER && $4==24' | grep -c "$SHOW_X $SHOW_Y")"
HIDE_LAUNCHER="$(wmctrl -lG | grep -v "Hud\|Dash" | awk '$3==0 && $4==24' | grep -c "$MAX_W $HIDE_Y")"

if [ "$SHOW_LAUNCHER" -eq "0" -a "$HIDE_LAUNCHER" -eq "0" ]
then
    CURRENT="$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")"
    if [ "$CURRENT" -ne "0" ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
    fi
else
    CURRENT="$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")"
    if [ "$CURRENT" -ne "1" ]
    then
        gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1
    fi
fi
done
```

---

### Post by jsevi83 on 2012-03-28
For what I see, SHOW_Y and HIDE_Y are the same values (maybe one can be omitted). I also don't know if using "- 24", "- 17" and "+ 17" is the best way. What about these lines after MAX_W and MAX_H?

LAUNCHER="$(wmctrl -lG | grep launcher | awk '{print $5}')"
PANEL="$(wmctrl -lG | grep panel | awk '{print $6}')"

SHOW_X="$(expr $MAX_W - $LAUNCHER)"
SHOW_Y="$(expr $MAX_H - $PANEL)"
HIDE_Y="$(expr $MAX_H - $PANEL)"

---

### Post by jsevi83 on 2012-03-28
I tried to simplify some things, let me know what you think:

```
#!/bin/bash
# sudo apt-get install wmctrl

ps -ef | grep "$0" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ "$DESKTOP_SESSION" != "ubuntu" ]; then exit 0; fi

RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel")

while [ "$RACE" -lt "3" ]; do RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel"); sleep 1; done

MAX_W=$(wmctrl -lG | awk '{if ($5 > max) { max = $5;}} END {print max}')
MAX_H=$(wmctrl -lG | awk '{if ($6 > max) { max = $6;}} END {print max}')
LAUNCHER=$(wmctrl -lG | grep launcher | awk '{print $5}')
PANEL=$(wmctrl -lG | grep panel | awk '{print $6}')
WIDTH=$(expr $MAX_W - $LAUNCHER)
HEIGHT=$(expr $MAX_H - $PANEL)

while true; do sleep 1

SHOW_LAUNCHER=$(wmctrl -lG | grep -v "Hud\|Dash" | awk -v LAUNCHER=$LAUNCHER -v PANEL=$PANEL '$3==LAUNCHER && $4==PANEL' | grep -c "$WIDTH $HEIGHT")
HIDE_LAUNCHER=$(wmctrl -lG | grep -v "Hud\|Dash" | awk -v PANEL=$PANEL '$3==0 && $4==PANEL' | grep -c "$MAX_W $HEIGHT")

if [ "$SHOW_LAUNCHER" -eq "0" -a "$HIDE_LAUNCHER" -eq "0" ]; then
	CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
	if [ "$CURRENT" -ne "0" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0; fi
else
	CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
	if [ "$CURRENT" -ne "1" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1; fi
fi
done
```

---

### Post by EgoGratis on 2012-03-28
I added logic for majority of things i thought could cause problems for  users and in the end nothing has to be setup manually by the user and it  works because of that i didn't put much thought into it anymore but  sure it can be optimized if anybody wants to. 

I thought i could put more autodetection in "while loop" too and user  could change settings in real time but i like less operations executed  in each interval and i didn't change this. Log out / log in is still  required after changes are made because of that.

If i understand correctly and i didn't test much and i assume it works fine:

-Dimension autodetection was added and if this changes in the future Unity the script would still work.
-Some cleanups/optimization that remove unnecessary operations was made.

Great work!

Maybe a note on delay. Changing delay below 2 in my tests didn't make  any real difference but setting value too low could create unnecessary  problems for users on some hardware.

The "real goal" of this script was to demonstrate to Unity developers  why this should be implemented in Unity by default and i hope this will  be the final outcome!

---

### Post by f_padia on 2012-03-29
Am I right in thinking that the reason for this script is to allow us to have dodge windows behaviour of the launcher? If so then why are you hiding the launcher for maximised windows?
wmctrl -lpG gives not only the size of the windows but the location too. The 4th and 5th columns are the x and y position of the top left corner of the window so would it not just be possible to put an 'if' command in the script and say 'if x position (=<) width of launcher then autohide mode'?

Im not a scripter or coder so I may be wrong but if it was possible that would give you dodge behaviour back.

---

### Post by EgoGratis on 2012-03-30
> Am I right in thinking that the reason for this script is to allow us to have dodge windows behaviour of the launcher?No, this script is just "proof of concept" how hide launcher when at least one window is maximized could work. I use it because i want to use the whole screen when i have application maximized and dodge windows was removed and i shared it if anybody else wants to use it too.

> wmctrl -lpG gives not only the size of the windows but the location too.  The 4th and 5th columns are the x and y position of the top left corner  of the window so would it not just be possible to put an 'if' command  in the script and say 'if x position (=<) width of launcher then  autohide mode'?Probably it could be possible yes BUT with bash script there is very little control on how launcher should behave. You probably notice that icon on desktop change position on launcher hide/show and if "dodge windows" would be implementer in this bash script this could not be done smooth.

> Im not a scripter or coder so I may be wrong but if it was possible that would give you dodge behaviour back.Technical it would probably be possible but it would not work smooth. It has to be "built in" Unity to work smooth.

Short answer: this script is not "dodge windows" replacement it's "prof of concept" how hide launcher when at least one windows is maximized could work. But if this behavior would be implemented in Unity then it would work smoother than with current script. Script simply put can't control anything beyond simple switching between "always and never hide" mode!

---

### Post by jsevi83 on 2012-03-30
I changed the script a little so the launcher also hides when a window is covering it (and not only when there are maximized windows). It will also work properly if the user changes the size of the dash.


```
#!/bin/bash

ps -ef | grep "$0" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ "$DESKTOP_SESSION" != "ubuntu" ]; then exit 0; fi

RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel"); while [ "$RACE" -lt "3" ]; do RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel"); sleep 1; done

MAX_W=$(wmctrl -lG | awk '{if ($5 > max) { max = $5;}} END {print max}')
MAX_H=$(wmctrl -lG | awk '{if ($6 > max) { max = $6;}} END {print max}')
PANEL=$(wmctrl -lG | grep panel | awk '{print $6}')
HEIGHT=$(expr $MAX_H - $PANEL)

while true; do sleep 1

LAUNCHER=$(wmctrl -lG | grep launcher | awk '{print $5}')
WIDTH=$(expr $MAX_W - $LAUNCHER)

COVERED=$(wmctrl -lG | grep -v "N/A\|$MAX_H" | awk '{print $3}' | awk -v LAUNCHER=$LAUNCHER '{if($1<LAUNCHER)print $1}' | wc -l)
MAXIMIZED=$(wmctrl -lG | awk -v LAUNCHER=$LAUNCHER -v PANEL=$PANEL '$3==LAUNCHER && $4==PANEL' | grep -c "$WIDTH $HEIGHT")
CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")

if [ "$COVERED" -eq "0" -a "$MAXIMIZED" -eq "0" ]; then
	if [ "$CURRENT" -ne "0" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0; fi
else
	if [ "$CURRENT" -ne "1" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1; fi
fi
done
```

---

### Post by x-shaney-x on 2012-03-31
I'm slightly confused here.  I have been a bit busy lately so out of the loop. 
So there seems to be 2 scripts now.

The one by EgoGratis is still just hiding on maximized windows and the one modified by jsevi83 is now almost like the full dodge behaviour right?

I just need to know because although you are both doing great work, I don't want full-on dodge myself, just dodge for maximized windows.

---

### Post by EgoGratis on 2012-03-31
> It will also work properly if the user changes the size of the dash.Launcher and not Dash? Yes this is one possibility but i prefer less operation executed in each interval but users have both options now and can decide for themselves.

> The one by EgoGratis is still just hiding on maximized windows and the  one modified by jsevi83 is now almost like the full dodge behaviour  right?

Yes, this is true. My last script only does hide when at least one windows is maximized for Single Screen / Multi workspaces and when changing for example louncher size log out / log in is required. I preferred it like this with bash script approach. 

Script from @jsevi83 tries to imitate old Dodge Windows behavior and he puts "real time" auto detection inside the loop and when changing for example launcher size log out / log in is not required.

So basically my script: Does auto detection on log in once and only hides launcher when at least one windows is maximized.

@jsevi83 script: tries to auto detect some changes in every interval and tries to be more like old Dodge Windows behavior.

---

### Post by jsevi83 on 2012-03-31
Here are both scripts, very similar to each other. The only difference is that the first script has the value MAXIMIZED2 and the second script has the value COVERED.


- HIDE THE LAUNCHER WITH MAXIMIZED WINDOWS:
```

#!/bin/bash

ps -ef | grep "$0" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ "$DESKTOP_SESSION" != "ubuntu" ]; then exit 0; fi

RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel"); while [ "$RACE" -lt "3" ]; do RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel"); sleep 1; done

MAX_W=$(wmctrl -lG | awk '{if ($5 > max) { max = $5;}} END {print max}')
MAX_H=$(wmctrl -lG | awk '{if ($6 > max) { max = $6;}} END {print max}')
LAUNCHER=$(wmctrl -lG | grep launcher | awk '{print $5}')
PANEL=$(wmctrl -lG | grep panel | awk '{print $6}')
WIDTH=$(expr $MAX_W - $LAUNCHER)
HEIGHT=$(expr $MAX_H - $PANEL)

while true; do sleep 1

CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
MAXIMIZED=$(wmctrl -lG | awk -v LAUNCHER=$LAUNCHER -v PANEL=$PANEL '$3==LAUNCHER && $4==PANEL' | grep -c "$WIDTH $HEIGHT")
MAXIMIZED2=$(wmctrl -lG | grep -v "N/A" | awk -v PANEL=$PANEL '$3==0 && $4==PANEL' | grep -c "$MAX_W $HEIGHT")

if [ "$MAXIMIZED" -eq "0" -a "$MAXIMIZED2" -eq "0" ]; then
	if [ "$CURRENT" -ne "0" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0; fi
else
	if [ "$CURRENT" -ne "1" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1; fi
fi
done
```



- OLD DODGE WINDOWS BEHAVIOUR:
```
#!/bin/bash

ps -ef | grep "$0" | grep -v "grep\|$$\|/bin/sh" | awk '!/awk/ {print $2}' | xargs -r kill

if [ "$DESKTOP_SESSION" != "ubuntu" ]; then exit 0; fi

RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel"); while [ "$RACE" -lt "3" ]; do RACE=$(wmctrl -l | grep -c "DNDCollectionWindow\|launcher\|panel"); sleep 1; done

MAX_W=$(wmctrl -lG | awk '{if ($5 > max) { max = $5;}} END {print max}')
MAX_H=$(wmctrl -lG | awk '{if ($6 > max) { max = $6;}} END {print max}')
LAUNCHER=$(wmctrl -lG | grep launcher | awk '{print $5}')
PANEL=$(wmctrl -lG | grep panel | awk '{print $6}')
WIDTH=$(expr $MAX_W - $LAUNCHER)
HEIGHT=$(expr $MAX_H - $PANEL)

while true; do sleep 1

CURRENT=$(gconftool-2 --get "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode")
MAXIMIZED=$(wmctrl -lG | awk -v LAUNCHER=$LAUNCHER -v PANEL=$PANEL '$3==LAUNCHER && $4==PANEL' | grep -c "$WIDTH $HEIGHT")
COVERED=$(wmctrl -lG | grep -v "N/A\|$MAX_H" | awk -v LAUNCHER=$LAUNCHER '{if($3<LAUNCHER)print $0}' | wc -l)

if [ "$MAXIMIZED" -eq "0" -a "$COVERED" -eq "0" ]; then
	if [ "$CURRENT" -ne "0" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0; fi
else
	if [ "$CURRENT" -ne "1" ]; then gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 1; fi
fi
done
```

---

### Post by mhmk on 2012-04-07
Hi,

the script didn't work at all - but I figured out why and how to fix it.

In case someone else is experiencing similar problems:

The line
```
MAXIMIZED=$(wmctrl -lG | awk -v LAUNCHER=$LAUNCHER -v PANEL=$PANEL '$3==LAUNCHER && $4==PANEL' | grep -c "$WIDTH $HEIGHT")
```
expects there to be ONE space between the width and height values returned by wmctrl. This is not the case on my (fresh) Ubuntu 12.04 Beta 2 setup with the newest wmctrl installed.
In fact the number of spaces varies to align the numbers.

Following replacement for above line fixes the problem using regex:
```
MAXIMIZED=$(wmctrl -lG | awk -v LAUNCHER=$LAUNCHER -v PANEL=$PANEL '$3==LAUNCHER && $4==PANEL' | grep -c "$WIDTH[ ]\{1,\}$HEIGHT")
```



Moritz

PS anyway thanks a million for the script!

---

### Post by EgoGratis on 2012-04-09
Nice. If more users will experience this problem i can make it default and investigate a bit but for now i will leave it as it is.

---

