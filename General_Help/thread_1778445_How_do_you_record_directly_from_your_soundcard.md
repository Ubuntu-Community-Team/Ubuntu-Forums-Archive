---
title: "How do you record directly from your soundcard?"
date: 2011-06-09
forum: General Help
---

### Post by misterbreadcrum on 2011-06-09
I got the lame mp3 encoder and ran $ arecord -f cd -t raw | lame -x -r - out.p3

What are the values for these letters?
Does cd pertain to the directory where it's recording? and once I start recording how do I stop?

---

### Post by jerrrys on 2011-06-09
try this:

&#65279;#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# [http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/](http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/)
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

---

### Post by misterbreadcrum on 2011-06-09
I created the .sh file for this and it works perfectly, thanks! 
Now for further functionality is there a command I can enter in the terminal to get this shell script to run?  The point is to be able to hotkey the command and begin recording at a moments notice.  Thanks

---

### Post by jerrrys on 2011-06-09
i rarely rip from radio so i just use terminal.  go to the site, kees is a very helpful person and say hi for me :D

---

