---
title: "Want to record what I hear from the speakers in audacity"
date: 2011-06-27
forum: General Help
---

### Post by p3aul on 2011-06-27
Hi I am using Alsa as a realtek soundcard driver. I want to record on Audacity what I hear from the speakers. I could do this in Win 7 but I don't know how to set this up in Ubuntu 11.04.
Thanx,
Paul

---

### Post by decrepit on 2011-06-27
don't you just press the record button?

---

### Post by p3aul on 2011-06-27
Obviously that doesn't work. You have to press record to record anything, what you hear from the speakers or anything else.:confused: There must be a control panel that I can't locate or a script that needs to be run
Thanks,
Paul

---

### Post by p3aul on 2011-06-27
Can anyone please help me?
Thanks,
Paul

---

### Post by oldfred on 2011-06-27
I have not done either. The instructables link is pretty old.

streamripper in synaptic
This command-line tool can be used to record MPEG III
and OGG online radio-streams into track-separated audio
files..

[http://www.instructables.com/id/SOYT5MMF6S8YZ1O/](http://www.instructables.com/id/SOYT5MMF6S8YZ1O/)

---

### Post by p3aul on 2011-06-27
I am using alsa for a driver. I typed in alsamixer at the terminal pressed tab to get to the inputs and pushed capture and capture 1 to the max. I esc out of mixer and then typed in alsactl store. I then got an error msg: alsactl: save_state:1547: Cannot open /var/lib/alsa/asound.state for writing: Permission denied
Paul

---

### Post by JKyleOKC on 2011-06-27
Try "sudo alsactl store" and see if that works. You'll be asked for your password; this will be the same password you use to log in. You won't see any indication that it's being accepted, but it is; this is a security feature.

The "permission denied" indicates that you don't have write permission to the file or to its directory; the "sudo" prefix gets you full administrative privilege for the duration of the command, allowing you to write out the changed file.

Hope this helps; if it solves the problem, please mark the thread as "solved."

---

### Post by Habitual on 2011-06-28
install sox with 
```
sudo apt-get install sox
```
Create this file and save it. I used soundcap.sh for this filename here.
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
MONITOR=$(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"

# End of soundcap.sh
```

To use it.

chmod 700 /path/to/soundcap.sh

Fire up Audacity. When your song(s)|list starts to play...open a terminal and execute /path/to/soundcap.sh (**LEAVE THE TERMINAL OPEN**), it will show "Recording. Ctrl-C or close window to stop" and it will put a WAV file in the directory it ran from
i.e., recording_16-Nov-10_2314-EST.wav

When angels stop singing, Close Audacity and in the terminal, Press Ctrl-C

Replay at your leisure.

---

### Post by p3aul on 2011-06-28
Thanks Habitual. The script worked but it wasn't using audacity. I wanted to be able to play a song from the internet and using Audacity to record the song. 
I have done this before using windows xp and it worked. But now I don't have the same driver and I don't know how to configure the Alsa driver to capture the song.

JKyleOKC: I did and it did make the change persistent, but it didn't make any difference. It still would not capture the song  I think it should have, but it didn't Is there anymore drivers for the realtek soundboard?
If the board wasn't built in I'd just try another board:(
Paul

---

### Post by p3aul on 2011-06-28
You know that I think about it, I don't need Audacity to record from the speakers. With Habitual's script I can just double-click on the file name and it brings up the dialog box asking me if I want to run in the terminal, which of course I do, so I get the same performance. What language is the script in BTW. I haven't heard of the .sh extension before.

My Next question is:

Can I create an Icon(button) I could load into the launcher? Then it would be perfect!
Thanks
Paul

---

### Post by Habitual on 2011-06-28
I use it on Grooveshark personally. :wink::wink::wink:

---

### Post by Habitual on 2011-06-28
> **p3aul said:**
> I haven't heard of the .sh extension before.

My Next question is:

Can I create an Icon(button) I could load into the launcher? Then it would be perfect!
Thanks
Paul

.sh = shell can be any valid shell I think, but this is a BASH shell script.

Sure, fire up alacarte and make a launcher that points to soundcap.sh

Originally, my instructions read
Fire up say GrooveShark and then open a terminal. When your song(s)|list starts to play...execute /path/to/soundcap.sh , it will show "Recording. Ctrl-C or close window to stop" and put a WAV file in the directory it ran from
(i.e.,
recording_16-Nov-10_2312-EST.wav
recording_16-Nov-10_2314-EST.wav)

Then go listen. When angels stop singing, Press Ctrl-C

---

### Post by p3aul on 2011-06-28
Thanks for turning me on the GrooveSharke!

> Sure, fire up alacarte and make a launcher that points to soundcap.shWhere do I find Alacarte? It's not in the Ubuntu Software Center, I can't find it by a search either.

It sounds like just what I need, but this is the first app that I've run across that I can't find :(
Paul

---

### Post by p3aul on 2011-06-28
OK I finally found alacarte but it wouldn't show the launcher I created. I just happened to right-click on the desktop and I found I could choose to create a launcher from there! I tried it and it worked. I got a default Icon(looks like a board on top of a spring) which I dragged to the launcher bar.

I don't know how to change the icon or how to get delete the launcher from the desktop without removing it from the launcher bar.
Thanks,
Paul

---

### Post by Habitual on 2011-06-29
> **p3aul said:**
> (looks like a board on top of a spring) which I dragged to the launcher bar.

Click that image of the board+spring and go have a look at/in/under /usr/share/icons

re: "from the desktop without removing it from the launcher bar."
they should actually be 2 separate launchers now, but I could be wrong (I frequently am)

Glad you like GrooveShark!

---

### Post by p3aul on 2011-06-30
Well I was able to change the icon but not from the launcher When you right-click on an icon in the launcher it just gives the standard two or three options none of which are "Properties". I managed to change the icon from the "Proerties" of the icon on the desktop but now it won't let me drag it to the launcher :(
Paul

---

### Post by Ubu noir on 2011-08-26
> **p3aul said:**
> Hi I am using Alsa as a realtek soundcard driver. I want to record on Audacity what I hear from the speakers. I could do this in Win 7 but I don't know how to set this up in Ubuntu 11.04.
Thanx,
Paul

How did you get Audacity to work in Windows 7??? I can't get any volume at all. I used Audacity every day to record radio progs in Windows XP. Another free audio recorder gave the same problem. 

Can't get anything which works in Ubuntu - I'm new to this system. All the instructions I have found are toooo complicated for a non tech to understand. I don't care if I record using Ubuntu or Windows 7 and would be really grateful if someone could help with either.

Thanks.

---

### Post by Bobhuber on 2011-08-26
> **p3aul said:**
> Hi I am using Alsa as a realtek soundcard driver. I want to record on Audacity what I hear from the speakers. I could do this in Win 7 but I don't know how to set this up in Ubuntu 11.04.
Thanx,
Paul
You don't need audacity.
[http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)

---

### Post by Ubu noir on 2011-08-28
Thanks Bobhuber. I've installed that but when I click on it nothing happens. So here is the dumb question of the month: how do I activate this recording system? With Audacity I simply opened it up on my desktop and chose stereo input, record. With this new thing, I don't even know how to get it to make a desktop icon. I have had to install it in DATA on my harddrive as I couldn't locate the C: drive where the other programs run from - I have both Windows 7 and Ubuntu but I don't know how to make programs available for both OS's - the others were set by tech support in the HP shop but he is not available to add other progs for me.

Thanks.

---

### Post by Bobhuber on 2011-08-28
> **Ubu noir said:**
> Thanks Bobhuber. I've installed that but when I click on it nothing happens. So here is the dumb question of the month: how do I activate this recording system? With Audacity I simply opened it up on my desktop and chose stereo input, record. With this new thing, I don't even know how to get it to make a desktop icon. I have had to install it in DATA on my harddrive as I couldn't locate the C: drive where the other programs run from - I have both Windows 7 and Ubuntu but I don't know how to make programs available for both OS's - the others were set by tech support in the HP shop but he is not available to add other progs for me.

Thanks.
This program is for Ubuntu only and works extremely well in 10.04 thru 11.04 Ubuntu (probably many more). Click on the support link on the site I gave you and there is a PDF file that explains how to use it.I dont know what version of Ubuntu (Classic or Unity) you are using but it works in either one.The program creates a link under sound/video called outrec that you can click on Or  from a terminal /usr/bin/outrec.gambas to launch. It will save the audio file in the outrec subdirectory in your home directory  ( home/bob/outrec ) in the format of your choice. Just make sure you only have one audio output source enabled under sound/hardware/preferences or it will not work. For instance if you have an HDMI output on your video card as most of the new cards have , this needs to be disabled. Have fun and good luck.

---

