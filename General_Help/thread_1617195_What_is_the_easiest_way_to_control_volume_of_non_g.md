---
title: "What is the easiest way to control volume of non gui VLC?"
date: 2010-11-09
forum: General Help
---

### Post by tobytoby on 2010-11-09
As a newbie, I have read that it is not possible to control a running instance of VLC through bash scripting :(
If I want to have a simple Launcher icon connected to some code to do something as trivial as increasing/decreasing volume of a running instance of VLC, what would be the best way to do that?
Thanks in advance!

---

### Post by tobytoby on 2010-11-09
BTW, if anyone knows of an alternative to vlc (I am only playing audio files) that can be run w/o gui and control the volume of a running instance, that would also be a solution!

---

### Post by nothingspecial on 2010-11-09
> **tobytoby said:**
> BTW, if anyone knows of an alternative to vlc (I am only playing audio files) that can be run w/o gui and control the volume of a running instance, that would also be a solution!

mplayer, control the volume with 0 and 9

0 = vol up
9 = vol down

---

### Post by tobytoby on 2010-11-09
how would the code look for doing that?
can I also store the current volume value in a file and feed that as a parameter when starting mplayer again?

---

### Post by nothingspecial on 2010-11-09
You can start mplayer at a specific volume.

If you post exactly what you are trying to do, I`ll try and give you the right code which you can then alias

Where are the audio files? Do you want them random? etc etc

---

### Post by tobytoby on 2010-11-09
I have a folder /home/user1/Desktop/audio_files, which contains the audio files

I use a crontab job to play the "audio files" folder at a set interval. 

I use /usr/bin/vlc audio_files/ to play the files with vlc, but does not work with mplayer :confused: I have also tried to add a wild card audio_files/*, but does not work.

Regarding the volume, I write to a file the value of the volume, that I then feed to vlc every time vls gets restarted (since I kill and restart vlc every time the crontab job starts the script). I write the volume value to a file since I of course want vlc to use the latest volume the user has set.

in vlc I have done it with --volume $lastused_volume (but as said, VLC will not accept changes when VLC runs which makes it a bit dificult for the user to hear what volume he/she has chosen...)
Thanks in advance!

---

### Post by nothingspecial on 2010-11-09
Maybe you would be better controlling the last volume level with aplay rather than the music player itself?

An example can be found in this mplayer script- 

[http://ignorantguru.users.sourceforge.net/downloads/mplayerstart.txt](http://ignorantguru.users.sourceforge.net/downloads/mplayerstart.txt)

As far as I know, mplayer only looks for files in the current directory and doesn`t descend directories recursively. This can be over come with find eg

```
mplayer -playlist <(find /home/user1/Desktop/audio_files/ -type f)
```

---

