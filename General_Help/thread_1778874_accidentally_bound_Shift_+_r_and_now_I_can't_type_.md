---
title: "accidentally bound Shift + r and now I can't type a capital r"
date: 2011-06-09
forum: General Help
---

### Post by misterbreadcrum on 2011-06-09
How do I go about fixing this?  I got a bash script called record and stupidly thought it would be a good idea to bind it to Shift + r :(
Does anyone know where to go to rebind this to capital r?

I'm also having trouble with my recording script.  The script goes like this
#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# [http://www.outflux.net/blog/archives...om-pulseaudio/](http://www.outflux.net/blog/archives...om-pulseaudio/)
#
#This script require sox
#sudo apt-get install sox

if [ -n "$1" ]; then
OUTFILE="$1"
else
TIME=$(date +%d-%b-%y_%H%M-%Z)
OUTFILE="recording_$TIME.wav"
fi

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"

# End of sound_cap.sh


It works fine and well, until I run the script with the keyboard command I made for it.  I wrote the command like this:
 ```
gnome-terminal -e "sudo bash /home/colin/Music/record.sh"
```The terminal asks me for my password and then claims to be recording, however no mp3 is saved in the directory my bash script is in.  

Any help on either of these problems would be greatly appreciated, thanks!

---

### Post by misterbreadcrum on 2011-06-09
bump
if anything I need a capital r!

---

### Post by AlphaLexman on 2011-06-09
Goto 'System -> Preferences -> Keyboard Shortcuts -> Custom Shortcuts' 

Highlight the offending shortcut, and click the 'Remove' button.

Good Luck!

---

### Post by amauk on 2011-06-09
> **misterbreadcrum said:**
> The terminal asks me for my password and then claims to be recording, however no mp3 is saved in the directory my bash script is in.

You need to make some minor changes to the script, and how it's executed

The script is designed for running manually in the terminal (as opposed to automatically via a key-combo), so first, specify an exact location for the recording, Eg```
if [ -n "$1" ]; then
OUTFILE="$1"
else
TIME=$(date +%d-%b-%y_%H%M-%Z)
OUTFILE="[COLOR="Red"]/home/colin/Music/[/COLOR]recording_$TIME.wav"
fi
```(or whereever you want files to be saved)

Next, when you run it, don't use sudo
running the script as root will record root's audio, not yours
```
gnome-terminal -e "bash /home/colin/Music/record.sh"
```

---

### Post by misterbreadcrum on 2011-06-09
I had already disabled the offending shortcut but it didn't work.  After a reboot however, typing a capital R was again possible with Shift + r.  Thanks!

---

