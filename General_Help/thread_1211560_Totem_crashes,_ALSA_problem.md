---
title: "Totem crashes, ALSA problem??"
date: 2009-07-12
forum: General Help
---

### Post by 3pinner on 2009-07-12
Running 8.10 (intrepid)
Totem Movie Player 2.24.3
Movie Player using GStreamer 0.10.21

Up until this point, I've had no problems with Totem. It played wmv, mpg, DVD, and streaming audio/video with no problems.
Recently I tried to open a wmv file that corrupted something in Totem, it just grayed out and stopped working. I cannot open any files with Totem,  (no sound or video) or get sound in  some other applications.

Sound card is OK. I get logon sounds. but after I'm logged in, nothing.

I do have Mplayer and VLC Media player as well. Both will work, playing mpg or wmv files with sound.
But rythmbox will crash when attempting to play audio, as does Thunderbird (which usually plays a sound for incoming mail).
There is no audio for streaming files in my web browser (no audio for youtube for example)
So I think this is an ALSA problem.

WHAT I'VE TRIED
I tried removing and reinstalling Totem

I have opened  volume control on the panel to make sure nothing is muted. I have tried all 3 devices listed, and still get no sound.

I've played around in Sound Preferences. All devices are set to the default Automatic, 

If I reset devices from Automatic to 
NVIDIA CK804 With ALC850 NVIDIA CK804 (ALSA)

 and test, I get the following error message:

audiotestsrc wave+sine 512 !
audioconvert ! audiosample !
gconfaudiosink: Failed to connect stream:
Invalid Argument
And I have to force close the Sound properties box.

This happens with anything marked ALSA,
but if I switch the device to anything labeled OSS, the test runs fine, but I still get no audio in Totem or elsewhere.

So I suspect some problem with ALSA that is making my other applications crash.
Any idea what's going on and how to fix this?

Thanks for the help!

---

### Post by 3pinner on 2009-07-12
Oddly enough............ I think I fixed it. (EDIT - PROBLEMS RETURNED DON'T KNOW WHY!)
I ran Bleachbit as administrator, checked all the boxes to clean out everything. I have sound & video back in Totem, and all the other issues I mentioned in the post seem to be fixed.

Any ideas what I might have cleaned out that would have caused the problem?????

---

### Post by kerry_s on 2009-07-12
try the "totem-xine" instead, remove totem-gstreamer.
another option is gnome-mplayer+gecko-mediaplayer it's far lighter, looks better embedded.

---

### Post by 3pinner on 2009-07-12
> **kerry_s said:**
> try the "totem-xine" instead, remove totem-gstreamer.
another option is gnome-mplayer+gecko-mediaplayer it's far lighter, looks better embedded.

Thank you kerry s,
now my idiot question:
Whats the basic difference between the two - totem-xine and totem gstreamer?
Thanks!

---

### Post by 3pinner on 2009-07-13
Now I'm back to having the same problems. Don't know why, can anybody help me figure out what's wrong???

---

### Post by Freezing on 2009-07-13
Have checked if you installed the sound drivers correctly?

---

### Post by 3pinner on 2009-07-13
Shouldn't be an issue. this has worked OK for months, but something corrupted it and now its not working, and causing other applications that use sound to crash also.

Any other ideas?

This is definitely an audio issue.
When I try to open an mpg file using Totem (exine) I get the following error message:

Totem could not play '/home/anyname/Desktop/chipturns.MPG'.
The audio device is busy. Is another application using it?

The answer is no. There is no other application that I know of that is using sound at that time.
What the heck is going on????

---

### Post by 3pinner on 2009-07-13
Here's the output of Totem --debug.
first I opened the program, then tried to open a MPG file with the following result:

anyname@frodo-desktop:~$ totem --debug
** (totem:6687): DEBUG: Init of Python module
** (totem:6687): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:6687): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:6687): DEBUG: Creating Python plugin instance
** Message: Error: Failed to connect stream: Invalid argument
pulsesink.c(634): gst_pulsesink_prepare (): /GstPlayBin:play/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin6/GstAutoAudioSink:autoaudiosink1/GstPulseSink:autoaudiosink1-actual-sink-pulse

---

### Post by 3pinner on 2009-07-13
This is really frustrating, I think I have it fixed, reboot and back to the same problems.
Shold I reinstall the OS?

---

