---
title: "Audio, recording."
date: 2010-05-06
forum: General Help
---

### Post by Drenriza on 2010-05-06
Is it possible in ubuntu to record, songs i hear on the internet?

In other words, i would like to the record audio that comes out of my head-phones in roughly high quality.

Thanks on advance.
Kind regards.

---

### Post by Smart Viking on 2010-05-06
Applications -> sound and video -> Sound recorder?

---

### Post by 3rdalbum on 2010-05-06
A better approach is to try and rip the music digitally - if it's on Youtube for instance, you can capture the Youtube FLV file by looking in your /tmp directory, and then import it into Audacity.

I personally use an audio cable with two 3.5mm plugs, put one end into the Headphone socket of my desktop, and the other end into the Sound In socket of my netbook, and record that way.

It may be possible to use Jack or even Pulseaudio to reroute the sound from the outputting program to the sound recording program on the same computer, but I don't know how to do this.

It should be possible too to use the cable I described in a loop from Headphone to Sound In on the same computer, but you'd have to be VERY careful that you have 'monitoring' turned off... otherwise the sound coming in would also go out the Headphone socket, and then back to the Sound In, and the feedback loop could destroy your sound card.

---

### Post by Drenriza on 2010-05-06
> **3rdalbum said:**
> A better approach is to try and rip the music digitally - if it's on Youtube for instance, you can capture the Youtube FLV file by looking in your /tmp directory, and then import it into Audacity.



It is youtube.
What would i be looking for in the /tmp file?

---

### Post by Drenriza on 2010-06-01
bump.

---

### Post by StuartN on 2010-06-01
> **Drenriza said:**
> bump.

I just watched a music video and **ls -ltr /tmp** shows the most recent file to be called Flash4POWgV, with no file extension. I can watch this with the command **vlc /tmp/Flash4POWgV** - you should copy or move it if you want to keep it.

I can open the File -> Convert/Save dialog in VLC, pick the same file, choose the OGG, FLAC or MP3 profile and save the audio into a new file.

EDIT: I see that there is a bug in VLC [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/550599](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/550599) causing unusable MP3 files - OGG and FLAC work fine, so you can save as either and then use SoundConverter or similar later. The Bug Report suggests **vlc $SOURCE --no-sout-video --no-sout-spu --sout "#transcode{acodec=mp3,ab=128}:standard{dst=$DESTINATION,mux=raw}"** as a rather unwieldy workaround.

---

### Post by Drenriza on 2010-06-02
Fantastic. Thanks mate. Works like a charm

---

