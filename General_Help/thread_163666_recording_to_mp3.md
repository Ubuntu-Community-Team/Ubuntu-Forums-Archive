---
title: "recording to mp3?"
date: 2006-04-21
forum: General Help
---

### Post by tardis on 2006-04-21
Is there anyway to use Sound Recorder or any other program to record from Line In on the computer and save it to mp3?  And then record it to a CD, with options as mp3 or as a normal CD that any CD player can play?  I know it can be done with ogg do it all the time, but can you do it with mp3?  Thanks...

---

### Post by gondilon on 2006-04-21
The best program for doing this is probably Audacity, and open sound sound recorder. You can get it using synaptic.

---

### Post by jazzmuzik on 2006-04-21
As mentioned, Audacity has an "Export to MP3" option. I'm trying to remember though if you need to install one of the restricted format libraries.

If you have a file in .wav format you can create an mp3 on the command line with this:

lame -b 128 infile.wav outfile.mp3

You can run 'lame --longhelp' to see the other supported bitrates besides 128. The highest is 320.

---

### Post by ronmarley1 on 2006-04-21
To export from Audacity, you'll need the lame codec.  It's in the repos, I think...

---

### Post by jayanm on 2008-07-03
you need to install gstreamer0.10-plugins-ugly-multiverse and sound recorder will be able to record to mp3.

sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

---

