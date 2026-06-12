---
title: "&quot;Sound Recorder&quot; and Lubuntu"
date: 2011-01-07
forum: General Help
---

### Post by t0p on 2011-01-07
One application I like to use is the "Sound Recorder" that comes with Ubuntu.

I have recently installed Lubuntu onto my EeePC netbook, because its lightness is better for the resource-challenged netbook.

"Sound Recorder" does not come with Lubuntu, nor does an alternative as far as I can tell.  So I installed gnome-media, which includes "Sound Recorder".

But when I try to run "Sound Recorder" from the menu, I get a dialogue box that says

> 
Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System Preferences menu.


This message is obviously aimed at Gnome/Ubuntu users, as there is no sound preferences control in the Lubuntu menu.

Can someone please tell me how to correct my sound preferences in Lubuntu, or alternatively suggest another sound recording app that will work with Lubuntu?

---

### Post by nothingspecial on 2011-01-07
First, I have absolutely no idea if this will work, not using lubuntu.

However, you may have some luck if you install the pavucontrol package.

Then access it through the sound & video menu (if lubuntu has that).

There is a recording settings tab.

---

### Post by t0p on 2011-01-07
> **nothingspecial said:**
> First, I have absolutely no idea if this will work, not using lubuntu.

However, you may have some luck if you install the pavucontrol package.

Then access it through the sound & video menu (if lubuntu has that).

There is a recording settings tab.

Thanks for the suggestion.  But pavucontrol won't work with Lubuntu.  I select it in Sound & Video and I get a "connection refused" message.  So I don't even get a chance to look at the recording tab.

---

### Post by cavalier911 on 2011-01-07
I would suggest installing gnome-alsamixer then menu/Sound & Video/Gnome ALSA Mixer  Experiment with the settings there and report back.

---

### Post by t0p on 2011-01-07
> **cavalier911 said:**
> I would suggest installing gnome-alsamixer then menu/Sound & Video/Gnome ALSA Mixer  Experiment with the settings there and report back.

Well, you've certainly pointed me in the right drection. The gnome "sound recorder" app still won't eork; but now I have gnome-alsamixer installed, I can use **arecord** to record my voice.

I've got some annoying background hiss intruding, but a bit of playing with the alsamixer controls may solve this issue.

Thanks!  And if anyone has further suggestions I'd love to hear them.

---

### Post by cavalier911 on 2011-01-07
sound-recorder works on Lubuntu.

These tips helped me:

Start sound-recorder in debug mode.
```
gnome-sound-recorder --gst-debug-level=2
```

Open gstreamer-properties
```
gstreamer-properties
```

When it wouldn't record I was getting error: Failed to find a supported audio source.Not exactly sure what fixed it but the error disappeared and it started recording.Level: meter doesn't work until recording starts.

---

### Post by t0p on 2011-01-08
Thanks cavalier911.  I shall check it out later when I'm at home with my EeePC.

---

### Post by t0p on 2011-01-10
**@cavalier911:**  I tried your suggestion, to no avail.  Here's the output:

```


gnome-sound-recorder --gst-debug-level=2
0:00:00.430520452  2523  0x85ac008 WARN                     oss gstosssrc.c:379:gst_oss_src_open:<osssrc0> error: Could not open audio device for recording.
0:00:00.430662506  2523  0x85ac008 WARN                     oss gstosssrc.c:379:gst_oss_src_open:<osssrc0> error: Unable to open device /dev/dsp for recording: No such file or directory
0:00:00.430853657  2523  0x85ac008 WARN               switchsrc gstswitchsrc.c:172:gst_switch_src_commit_new_kid:<gconfaudiosource> error: Failed to set state on new child.
0:00:00.431039570  2523  0x85ac008 WARN                   gconf gstgconfaudiosrc.c:157:do_toggle_element:<gconfaudiosource> Failed to update child element

```

```


t0p@deimos:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'alsasink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'

```

Help, anyone?

---

### Post by t0p on 2011-01-17
A hopeful bump.

Quick recap: I am using Lubuntu (the LXDE variant of Ubuntu).  I  want to record audio through the microphone on my computer.  I've installed **gnome-sound-recorder** but I can't get it to work.  The command-line utility **arecord** records my voice, but with an irritating hiss in the background.

My current workaround is to use an Ubuntu live usb: gnome-sound-recorder works fine in a live session (hence I know it's not a hardware issue) but it is pretty annoying to have to run a live session whenever I want to record something.

I might just need to recalibrate arecord, but I don't know how to, or if it's even possible.

Can anyone help with either arecord or gnome-sound-recorder in Lubuntu?

Cheers.

---

### Post by t0p on 2011-02-03
This is one bumpy thread!

I'm still using an Ubuntu live usb when I want to record something. But obviously that is *far* from ideal.  What if I want to make a recording whilst using other features that my installed Lubuntu possesses but which are absent in a live *Ubuntu* environment?  Is it just tough luck?

Surely *someone* can advise on this matter?  Anyone?

Bah!

---

