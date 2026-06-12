---
title: "Link keystroke with a sound"
date: 2011-12-30
forum: General Help
---

### Post by randj on 2011-12-30
I would like to have a sound linked to the Caps Lock key operation. I do have a visual indication.
 
Looking through past posts it seems that this is not possible.
 
I have tried Windows programs under Wine, but these don't work.
 
Surely it must be possible to make a link somehow?
 
Any ideas?
 
Randj

---

### Post by stinkeye on 2011-12-30
Firstly this is when running compiz.
**[COLOR="Red"]EDIT[/COLOR]**: Even though this was set in unity using compiz, I found that it carries over to your other sessions with different window managers...eg gnome and gnome classic(no effects).
  
It uses **ffplay** which needs **ffmpeg** to be installed.
There are other ways of playing a sound but I find ffplay more reliable for different formats.

Test this in the terminal...
```
ffplay -nodisp -autoexit /usr/share/sounds/gnome/default/alerts/glass.ogg
```

If that works open **compizconfig-settings-manager** (ccsm)
and goto the commands plugin.
In the **command line 0** box, paste in...
```
ffplay -nodisp -autoexit /usr/share/sounds/gnome/default/alerts/glass.ogg
```

Goto the key bindings tab and click on the **disabled** button for **run command 0**
Mark enabled and hit the **grab key combination** button.
Press the CapsLock key then just close the little ccsm window and click ok.
You should now have a sound when capslock is pressed.


I actually use the path to this script  in the **command line 0** box.
It plays a sound and sends a notification on the status of capslock.
The sound only plays when capslock is enabled.
```
#!/bin/bash

value=$(xset q | grep "Caps Lock:" | awk '{print $4}' | grep -c on)

if [ "$value" -eq "1" ]; 
then
   notify-send -i  "/usr/share/icons/gnome/48x48/devices/keyboard.png" "                    Caps Lock ON" &
   ffplay -nodisp -autoexit /usr/share/sounds/gnome/default/alerts/glass.ogg



else
   notify-send -i  "/usr/share/icons/gnome/48x48/devices/keyboard.png" "                    Caps Lock OFF"
   
fi
```

---

### Post by drdos2006 on 2011-12-30
Very nice.

regards

---

### Post by randj on 2012-01-01
Dear stinkeye
 
Thank you for your reply. I used your first solution and _it worked OK_. I had to install
ffmpeg first.
 
A couple of points:-
 
I assume that the sound "glass.ogg" can be sustituted eg "sonar.ogg". I haven't done this yet.
 
When the caps lock key is pressed I get the sound required, but also a small blank, black window which dissapears after a few seconds. This is headed with the sound file?
It is there for such a short period I cannot find more info!
 
Can I get rid of this, or minimise it in some way? Its not vital tho'.
 
(Ubuntu 11.04 Gnome desktop)
 
Thanks
 
Randj

---

### Post by stinkeye on 2012-01-01
I don't get the blank window in unity 11.10. The **-nodisp** flag should stop that from appearing.
eg if run without **-nodisp**
```
ffplay -autoexit /usr/share/sounds/gnome/default/alerts/glass.ogg
```
Is that what your seeing?


You can try other commands to play a sound.
eg
```
paplay /usr/share/sounds/gnome/default/alerts/glass.ogg
or
aplay /usr/share/sounds/gnome/default/alerts/glass.ogg
```
Test in the terminal and the alter the script or the ccsm command.


You can use any sound you want, even your own downloaded sounds.
eg ```
paplay /path/to/your/soundfile
```
You just need to test to see if it will play the sound format or you
could convert the sound to .ogg using **winff**.

---

### Post by randj on 2012-01-03
Thank you for your reply. I have tried your suggestions.
 
Changed sound OK
 
The "-nodisp"  is present in the command
 
The other commands suggested did not work at all
 
I have got the label on the blank window. It is :-
 
/usr/share/sounds/gnome/default/alerts/sonar.ogg
 
Regards
 
randj

---

### Post by stinkeye on 2012-01-03
> **randj said:**
> Thank you for your reply. I have tried your suggestions.
 
Changed sound OK
 
The "-nodisp"  is present in the command
 
The other commands suggested did not work at all
 
I have got the label on the blank window. It is :-
 
/usr/share/sounds/gnome/default/alerts/sonar.ogg
 
Regards
 
randj

Dont really know why the window displays as it doesn't here on 11.10 with unity.

You could try ogg123 which can be used for playing ogg files in the command line.
It is in the **vorbis-tools** package.
```
sudo apt-get install vorbis-tools
```

Then try the command...
```
ogg123 -q /usr/share/sounds/gnome/default/alerts/sonar.ogg
```
or
make it use Pulseaudio with...
```
ogg123 -q -d pulse /usr/share/sounds/gnome/default/alerts/sonar.ogg
```

---

### Post by randj on 2012-01-04
Stinkeye

[LEFT] The use of vorbis tools_** worked OK**_ without using  the the pulse audio option.

Thank you for all your help.

Regards

randj
[/LEFT]

---

