---
title: "LMMS Problems"
date: 2010-01-13
forum: General Help
---

### Post by Zyrtec on 2010-01-13
I'm having some annoying problems with LMMS. I just have the LMMS downloaded from the repos, if it matters. 

First of all, Audio problems. I know a lot of people have had the same problem with audio in LMMS, and I've looked through the threads for solutions. I try to put it on ALSA and kill the pulseaudio... but there's still no sound on ALSA. Pulesaudio lags really badly when I try to do the playback of the song, and sometimes I can't tell what my "song" sounds like. 

The main problem are random crashes. I'll be working on something, or exporting a file (so that I can listen to the song without lag), and the program will just crash as if I clicked the X in the corner to close it out. It doesn't give an error or anything... just closes out. I've learned now to save a bunch, but it still does it a lot. 

Finally, when I close out of LMMS, apparently there's still some of it going... because when I try to restart or shut down my computer, it will tell me that there's 2 processes of LMS still running. I closed out of LMMS and looked on the System Resources, and LMMS is still on there "sleeping". It's only a minor annoyance because I can still shutdown/restart anyways.

I'm just mainly wondering, do I have some sort of package problem? Or is there something going wrong?

---

### Post by JayPeeJay on 2010-01-28
The default setting for the device does not seem to work really well, I had to look up my device in terminal using the *aplay -l*  command.  Then enter that instead of default.  For example, mine was hw: 0,0  Having said that I am myself having issues with the midi settings.

---

### Post by a2z on 2010-01-29
I've been also having intermittent audio trouble. 
However, I may have solved at least my problem. 
And hopefully yours too.
I went to edit>setings>"click on speaker" icon (left column)
From the drop down list under audio interface, select
oss (Open Sound System) 
In doing this on my system, I have excellent sound, and no more extensive
cpu usage while idle. And I'd guess shutting down, there would be no more processes still working.
Hope it helps those having lmms sound trouble.

a2z

---

