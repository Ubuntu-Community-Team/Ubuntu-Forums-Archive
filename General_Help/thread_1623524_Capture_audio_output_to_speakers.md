---
title: "Capture audio output to speakers"
date: 2010-11-16
forum: General Help
---

### Post by Silvernail on 2010-11-16
I have this file:
```
vid-gd-19940626-peggy.rm
```

I would like to extract the audio and copy to a file to burn on a CD.

'pitivi' will load the file and show the audio timeline. But I can not find a save or copy button.

'vlc' will play the file but I can not find how to seperate/save the audio.

I found a 'ffmpeg' that is suppose to read whatever is being sent to your speakers.
```
ffmpeg -f oss -i /dev/dsp -f video4linux2 out.wav
```
This produce a file that 'mplayer', 'vlc', 'audacity' will load but it is empty of useful data. Black screen only.

This is the second week I have worked on this. Either I'm googling for the wrong words or what I'm reading, I don't understand.

Can anyone get me turned around and back on track. I would like Jerry Garcia and Peggy-O to go with me when I drive into town.

---

### Post by amauk on 2010-11-16
Bash script
will record all sound produced by your system, and save it as a wav file

```
#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/
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
MONITOR=$(pactl list | grep -A2 '^Source #' | \
    grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"
```

---

### Post by Silvernail on 2010-11-16
Worked like a charm. Thank you very much for the help.

---

### Post by Habitual on 2010-11-16
Mad Props for the nice script.

Thank You.

---

### Post by sudo_rm_ignorance on 2011-07-23
Awesome, this is exactly what I was looking for.  Thanks for sharing, this is extremely useful.

---

