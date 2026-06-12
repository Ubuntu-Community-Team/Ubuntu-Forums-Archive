---
title: "Increase volume control steps on volume wheel"
date: 2012-10-01
forum: General Help
---

### Post by SiO2* on 2012-10-01
Hello,
I'm running Ubuntu 12.04.1 64bit, what i'd like to do is increase the number of steps between mute and 100% while using my volume wheel. Right now it seems like there are 5 steps, which is about a 20% change for just a small amount of rotation. It'd be nice to have the volume up and down 'shortcut' to be more in the range of a 3-4% change.

I'd imagine this is hidden in a config file somewhere, but i'm not sure where to look.

I've already searched this forum but I've found only solutions valid for Ubuntu 8.10 or older that don't work on Ubuntu 12.04 (e.g. dconf editor or gconf editor)

Thank you in advance for your help!

---

### Post by SiO2* on 2012-10-04
up

---

### Post by pqwoerituytrueiwoq on 2012-10-04
on my 10.04 install the setting is in the configuration editor (gconf-editor) under
[FONT=Courier New]/apps/gnome_settings_daemon/volume_step[/FONT]
the actual file is here
[FONT=Courier New]~/.gconf/apps/gnome_settings_daemon/%gconf.xml[/FONT]
```
<?xml version="1.0"?>
<gconf>
    <entry name="volume_step" mtime="1311896260" type="int" value="2"/>
</gconf>
```

you could use a script to do this if that setting no longer exist
[http://ubuntuforums.org/showthread.php?t=2047908](http://ubuntuforums.org/showthread.php?t=2047908)

---

### Post by SiO2* on 2012-10-04
> **pqwoerituytrueiwoq said:**
> on my 10.04 install the setting is in the configuration editor (gconf-editor) under
[FONT=Courier New]/apps/gnome_settings_daemon/volume_step[/FONT]
the actual file is here
[FONT=Courier New]~/.gconf/apps/gnome_settings_daemon/%gconf.xml[/FONT]
```
<?xml version="1.0"?>
<gconf>
    <entry name="volume_step" mtime="1311896260" type="int" value="2"/>
</gconf>
```

you could use a script to do this if that setting no longer exist
[http://ubuntuforums.org/showthread.php?t=2047908](http://ubuntuforums.org/showthread.php?t=2047908)

Thank you for your reply.
This setting no longer exists in ubuntu 12.04, I've tried to create the file xml with the exact path and content you posted but it doesn't work...
I'm sorry but my scripting skill is close to zero, I kindly need some more detail on what the script you suggested should do

---

### Post by pqwoerituytrueiwoq on 2012-10-04
to install the script
[FONT=Courier New]gksu gedit /usr/local/bin/volume[/FONT]
paste the code in the last post
looks at lines 2 to 4
lines that start with a # are comments (anything after a # is a comment)
line 2 has automatic detection disabled via the # character
line 3 is line 2 in manual (delete this line for auto to work)
line 4 is the volume step (increase/decrease the number as needed)
save it
close gedit
[FONT=Courier New]sudo chmod +x /usr/local/bin/volume[/FONT]

now the script is installed, now you just go into your keyboard shortcuts and create a new keyboard shirtcut for the volume
the commands would be
[FONT=Courier New]volume plus
volume minus[/FONT]
run [FONT=Courier New]volume[/FONT] in a termianl for more commands


BTW if the command in the 1st post adjust your sound you don't need the script you can just add those command to keyboard shortcuts

---

### Post by SiO2* on 2012-10-05
> **pqwoerituytrueiwoq said:**
> to install the script
[FONT=Courier New]gksu gedit /usr/local/bin/volume[/FONT]
paste the code in the last post
looks at lines 2 to 4
lines that start with a # are comments (anything after a # is a comment)
line 2 has automatic detection disabled via the # character
line 3 is line 2 in manual (delete this line for auto to work)
line 4 is the volume step (increase/decrease the number as needed)
save it
close gedit
[FONT=Courier New]sudo chmod +x /usr/local/bin/volume[/FONT]

now the script is installed, now you just go into your keyboard shortcuts and create a new keyboard shirtcut for the volume
the commands would be
[FONT=Courier New]volume plus
volume minus[/FONT]
run [FONT=Courier New]volume[/FONT] in a termianl for more commands


BTW if the command in the 1st post adjust your sound you don't need the script you can just add those command to keyboard shortcuts
Very clear thank you.
I followed your instructions for the script but this is what I get after running "volume plus" in a terminal:
```
silvio@Qosmio-G50:~$ volume plus
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
^C
```
setting up the shortcuts, the script "volume" launches several instances of itself and the system get stuck...
any idea about the reason?

---

### Post by pqwoerituytrueiwoq on 2012-10-05
```
volume dump;cat /usr/local/bin/volume | head -4
```

---

### Post by SiO2* on 2012-10-05
Thanks again.
Same behavior:
```
silvio@Qosmio-G50:~$ volume dump;cat /usr/local/bin/volume | head -4
alsa_output.pci-0000_00_1b.0.analog-stereo
#!/bin/bash
# SINK_NAME="`pacmd dump | grep set-sink-volume | sed 's/ /\n/g' | grep alsa | head -1`" # this is auto detect but it may break using the reset action to fix maxed volume at login
SINK_NAME="alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1"
VOL_STEP="0x01000"
silvio@Qosmio-G50:~$ volume plus
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
Waiting on volume to become setable (infinite loop on invalid sink name)
^C

```

---

### Post by pqwoerituytrueiwoq on 2012-10-05
[s]please paste the command i gave you
why: i said [FONT=Courier New]volume dump[/FONT] not [FONT=Courier New]volume plus[/FONT][/s]

Problem:
You are using the sink name for my hdmi card not your analog one
this will make it use your analog sound card
```
sudo sed -i '/s/alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/' /usr/local/bin/volume
```you could do this
```
volume plus alsa_output.pci-0000_00_1b.0.analog-stereo
```
or (since you only have 1 sound card with alsa in the name)
```
volume plus `volume dump`
```

---

### Post by SiO2* on 2012-10-05
```
silvio@Qosmio-G50:~$ sudo sed -i '/s/alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/' /usr/local/bin/volume
[sudo] password for silvio: 
silvio@Qosmio-G50:~$ volume plus alsa_output.pci-0000_00_1b.0.analog-stereo
/usr/local/bin/volume: riga 2: lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/: File o directory non esistente
/usr/local/bin/volume: riga 3: lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/: File o directory non esistente
/usr/local/bin/volume: riga 4: lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/: File o directory non esistente
/usr/local/bin/volume: riga 6: lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/: File o directory non esistente
/usr/local/bin/volume: riga 7: lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/: File o directory non esistente
/usr/local/bin/volume: riga 8: lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/: File o directory non esistente
/usr/local/bin/volume: riga 10: lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/: File o directory non esistente
/usr/local/bin/volume: riga 11: lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/: File o directory non esistente
/usr/local/bin/volume: riga 12: lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/: File o directory non esistente
/usr/local/bin/volume: riga 98: errore di sintassi vicino al token non atteso "newline"
/usr/local/bin/volume: riga 98: `lsa_output.pci-0000_01_00.1.hdmi-stereo-extra1/alsa_output.pci-0000_00_1b.0.analog-stereo/'

```
sorry the output is in italian but, 
riga 2, riga 3 etc. mean line 2, line 3 etc.
"File o directory non esistente" means "File or directory doesn't exist" 
riga 98: errore di sintassi vicino al token non atteso "newline" means
line 98: syntax error close to the unexpected token "newline"

Thank you for your patience

---

### Post by pqwoerituytrueiwoq on 2012-10-05
opps dam type probably damaged the script with a that one
here is the entire script, configured for your sound  card
[FONT=Courier New]gksu gedit /usr/local/bin/volume[/FONT]
```
#!/bin/bash
# Uncomment line 3 and delete line 4 to enable auto detect, edit line 5 as needed 
# SINK_NAME="`pacmd dump | grep set-sink-volume | sed 's/ /\n/g' | grep alsa | head -1`" # this is auto detect but it may break using the reset action to fix maxed volume at login
SINK_NAME="alsa_output.pci-0000_00_1b.0.analog-stereo"
VOL_STEP="0x01000"

function wait {
    while [ -z "$VOL_NOW" ]; do
        VOL_NOW=`pacmd dump | grep -P "^set-sink-volume $SINK_NAME\s+" | perl -p -i -e 's/.+\s(.x.+)$/$1/'`
        if [ -z "$VOL_NOW" ]; then
            echo "Waiting on volume to become setable (infinite loop on invalid sink name)"
            sleep 1
        fi
    done
}

if [ "$1" == "--help" ]; then
    echo "Usage: `basename $0` [ACTION] [SINK] [STEP]"
    echo "Action:"
    echo "   plus      Increase volume by one step"
    echo "   minus     Decrease volume by one step"
    echo "   mute      Toggle volume mute status"
    echo "   reset     Re-apply current volume (useful if you have maxed volume at login)"
    echo "   dump      List sink name(s)"
    echo "Sink (Optional):"
    echo "   Default is '$SINK_NAME'"
    echo "   Run '`basename $0` dump' for a list"
    echo "Step (Optional):"
    echo "   Increment to adjust volume by"
    echo "   Default is '$VOL_STEP'"
    echo "Note:"
    echo "   Configure defaults by editing lines 3 and 4 of `dirname $0`/`basename $0`"
    echo "   To set STEP and not SINK use empty quotes for SINK"
    exit
fi

if [ -n "$2" ]; then
    SINK_NAME="$2"
fi
if [ -n "$3" ]; then
    VOL_STEP="$3"
fi

case "$1" in
    plus)
        wait
        VOL_NEW=$((VOL_NOW + VOL_STEP))
        if [ $VOL_NEW -gt $((0x10000)) ]; then
            VOL_NEW=$((0x10000))
        fi
        pactl set-sink-volume $SINK_NAME `printf "0x%X" $VOL_NEW`
    ;;
    minus)
        wait
        VOL_NEW=$((VOL_NOW - VOL_STEP))
        if [ $(($VOL_NEW)) -lt $((0x00000)) ]; then
            VOL_NEW=$((0x00000))
        fi
        pactl set-sink-volume $SINK_NAME `printf "0x%X" $VOL_NEW`
        ;;
    mute)
        wait
        MUTE_STATE=`pacmd dump | grep -P "^set-sink-mute $SINK_NAME\s+" | perl -p -i -e 's/.+\s(yes|no)$/$1/'`
        if [ $MUTE_STATE = no ]; then
            pactl set-sink-mute $SINK_NAME 1
        elif [ $MUTE_STATE = yes ]; then
            pactl set-sink-mute $SINK_NAME 0
        fi
        ;;
    reset)
        wait
        pactl set-sink-volume $SINK_NAME `printf "0x%X" $VOL_NOW`
        ;;
    dump)
        SINK="`pacmd dump | grep set-sink-volume | sed 's/ /\n/g' | grep alsa`"
        if [ -z "$SINK" ]; then
            echo "[TYPE] [NAME] [VOLUME]"
            echo "`pacmd dump | grep set-sink-volume`"
        else
            echo "$SINK"
        fi
        ;;
    *)
        `dirname $0`/`basename $0` --help
esac
```

---

### Post by SiO2* on 2012-10-05
:guitar:
it works!!! You are a master! :p
Just a couple of questions:
- [S]If I want to make the volume steps smaller, then the number 0x01000 must be lowered. This means something like 0x00500? Or this is a binary and I have to put a 0x00100, or is still another format?[/S] **
- The script doesn't affect the volume indicator bar that doesn't appear while the volume is set. I mean this bar

[IMG]http://uppix.net/5/e/e/93a361fe3b5afad111fef2c4023a4.png[/IMG]
In the upper right corner.

Do you think there is some way to get it working with your script?

I would like to share this solution in the italian ubuntu forum, linking this thread and your script. Hope you agree :)

**Edit
ok, I've just found that it's a decimal number and set it to 0x00300

---

### Post by pqwoerituytrueiwoq on 2012-10-07
the bar appears for me as long as xfce4-volumed is running, but i am running xfce, not unity/gnome3

---

### Post by SiO2* on 2012-10-07
Ok, thank you very much for your help

---

### Post by Adrian Challinor on 2012-12-07
Thank you. Saved me a huge amount of time.

---

