---
title: "Can't use my mic to record or Skype"
date: 2011-04-26
forum: General Help
---

### Post by brozium on 2011-04-26
I'm using Ubuntu Natty 11.04 updated as of today (4-26-11)

I can hear my mic through the speakers if I move the volume levels on alsamixer but I can't use it for Skype or recording.

More info:
[http://www.alsa-project.org/db/?f=baaca838af866d23dc143614f1aa78754b4dbcbc](http://www.alsa-project.org/db/?f=baaca838af866d23dc143614f1aa78754b4dbcbc)

Help?:)

---

### Post by brozium on 2011-04-27
bump?

---

### Post by KegHead on 2011-04-27
Hi!

Real basic:

goto;

system.preferences..sound

there are a number of parameters.

KegHead

---

### Post by brozium on 2011-04-28
That doesn't work, I can turn up the volume of my mic via Gnome ALSA Mixer but all it does is make the mic output to the speakers and i can't use it for skype

---

### Post by hwttdz on 2011-04-28
Run pavucontrol, you might have to install it.  

In pavucontrol, while recording (gnome-sound-recorder or other) find the name of your input stream (you might have to change the dropdown to show all streams or something of the sort).  Then go start skype  (leave pavucontrol running), and while doing a test call (or something else, but the important thing is that skype is an application that is using an input audio stream), move skype to the working input stream. 

The same procedure would apply to gnome-sound-recorder, or any other application, you just need to move it to the input stream attached to that microphone.  

Conveniently you can also adjust microphone volume from pavucontrol.  

I hope that's somewhat clear.

---

### Post by brozium on 2011-04-28
Ok tried using the PulseAudio Volume Control.
I only got 2 inputs, the mic and the stereo mix.
Tried to make a recording while changing the levels to see if it works. The volume indicator moves but when I play the recording I can only hear like pops and clicks.
And yes, the mic works.

---

### Post by hwttdz on 2011-04-28
So on the input devices tab you should have it set to "show all input devices" and when you talk you see none of the bars moving?

---

### Post by brozium on 2011-04-28
I see one of the bars moving as if the mic was capturing sounds, but when i do a recording i only get pops and clicks, no audio.

---

### Post by hwttdz on 2011-04-28
So while you are recording with gnome-sound-recorder, on the input streams tab set the drop down to "show all streams", and then you can change the "record stream from" field to the same channel as you can see the bar moving on the input devices tab.  (also make sure it's not muted).

---

### Post by brozium on 2011-04-28
It's not muted and the stream selected is the correct one.

---

### Post by hwttdz on 2011-04-28
Is the bar on the recording applications tab moving in the same way as the bar on the input devices tab?

---

### Post by brozium on 2011-04-28
Yes they move the same. They are always at 100% and sometimes they move a little regardless I speak on the mic or not

---

### Post by pwabrahams on 2011-05-03
I'm running Natty with pulseaudio.  I had the Skype microphone working under Maverick, but now it doesn't work in Skype.  Yet Audacity shows that the mike signal is being picked up just fine.  I've diddled the settings in alsamixer and in pavucontrol, but nothing helps.  Very frustrating.

---

