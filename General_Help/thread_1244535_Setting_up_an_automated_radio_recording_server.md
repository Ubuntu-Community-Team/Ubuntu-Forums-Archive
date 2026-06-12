---
title: "Setting up an automated radio recording server"
date: 2009-08-19
forum: General Help
---

### Post by Jackelope on 2009-08-19
I'm in the process of setting up an old computer as a server to automatically record internet radio shows. I have it booting up and starting Streamtuner OK, but I'm running into 2 major problems.

First, I can't get streamripper (streamtuner) to automatically start ripping a particular station. I'm sure this is as simple as a few lines of script telling it to start ripping the station on startup, but I'm pretty lost.

Second, I need to shut down the computer automatically. I thought this part would be easy, but I need the sudo password to shut down. How can I get it to shutdown without typing in my sudo password each time?

Any advice is appreciated. Thanks! :)

---

### Post by ajgreeny on 2009-08-19
Not sure about the shutdown part of your post, but for recording radio, I use streamripper for some and mplayer for others depending on the stream type.

For an mp3 stream I have set up a number of script files, eg 
```
#!/bin/bash
/usr/bin/streamripper URL/OF/STREAM/MP3 -t -d /home/username/Audio_recording/Radio
```This gives the full path of streamripper, the url of the stream, the option -t to ensure each recorded file is numbered sequentially, and -d the option for the destination of the output mp3 file.

For a realplayer stream, in this case streamed as a playlist, I have the following
```
#!/bin/bash
/usr/bin/mplayer -cache 2048 -playlist http://www.bbc.co.uk/radio2/realmedia/fmg2.ram -vc null -vo null -ao pcm:fast:waveheader:file=/home/andrew/Radio/BBCR2.wav
```Again this shows the full path of the mplayer executable, the size of cache used by mplayer, -playlist as this stream is actually a playlist, not a ram stream, the url of BBC Radio 2, the options to dump the stream using pcm (ie as a wav file), and finally the name of the filedump.

I then use gnome schedule, pointing to the full pathway of those script files to record various programs without problem, so I see no reason why you could not do something similar by running similar scripts to start either mplayer or streamripper, or both, at startup.

---

### Post by Jackelope on 2009-08-20
Sounds like a plan. Those scripts look like just the thing I need. Thanks! :guitar:

---

