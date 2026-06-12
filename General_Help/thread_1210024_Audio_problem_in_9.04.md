---
title: "Audio problem in 9.04"
date: 2009-07-10
forum: General Help
---

### Post by aerojad on 2009-07-10
Greetings.  I've been using Ubuntu for a handful of releases now and the audio on the computers I've used over time have just worked, never needed to configure anything.

I did a clean install of 9.04 today on a machine that had 8.10, and audio is not working.  Pulseaudio and alsa are definitely installed, the volume control program shows my SB Audigy 4 as being there, and audio worked on this machine just fine earlier in the day with 8.10, where should I start looking for what's wrong?

---

### Post by QIII on 2009-07-11
In System | Preferences | Sound  try toggling between Auto Detect, ALSA and Pulse Audio and see if anything works any better than anything else.  I wouldn't mix and match.  Change them all to one of the three and test things out.

If something doesn't work, you can always set everything back to the way it was before you start getting suggestions for CLI commands.

I have everything on Auto Detect except for sound capture, for which I use ALSA.

But given the multitude of hardware support variations, what works for one may not work for all.

---

### Post by kostkon on 2009-07-11
Don't change your sound preferences, but try this:

right click on the speaker in your system tray and select *Open Volume Control*. Select the *Switches* tab and make sure that the *Analog/Digital* switch is not enabled.

Hope that helps.

---

### Post by Jebtrix on 2009-07-11
Try using alsamixer and try max'ing out everything. Since 9.04 went to Pulse Audio by default, you may want to look into removing pulse audio completely and just use alsa (as v8.xx did)

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

---

### Post by akqj10 on 2009-07-11
Many of us have tried to solve the sound problem in 9.04. I myself have tried dozens of configurations and nothing has worked until today. All you have to do is go into your BIOS and turn off the motherboard sound, reboot into Ubuntu and voila, sound is working. I opened Firefox and went to CNN and CNET and played videos and the sound works!

---

### Post by optikal1 on 2009-07-14
I have Audigy2 and I was able to get sound when I chose Audigy2 Multichannel Playback (ALSA) in sound preferences, and 'checked' the Analog/Digital switch. But now, I don't have the 'Switches' tab anymore in that dialog box! Worse, sound is coming only from the rear speakers...

---

### Post by 0re0 on 2009-07-14
[akqj10]("http://ubuntuforums.org/member.php?u=872656") was your sound problem with an hp mini? bc i do not see that setting anywhere in BIOS for this machine

---

### Post by danwood76 on 2009-07-14
The issue can normally be fixed by installing PA volume control and setting your sound blaster as the default.
It will probably be choosing the onboard sound as default as it inits first.

Jaunty did have a nice way to choose this through GNOME but unfortunatly it was taken out because people complained in the alpha stage of development.

---

### Post by akqj10 on 2009-07-14
> **0re0 said:**
> [akqj10]("http://ubuntuforums.org/member.php?u=872656") was your sound problem with an hp mini? bc i do not see that setting anywhere in BIOS for this machine
 
To 0re0:  I'm using a Dell Dimension 8400.   I went into the BIOS, Onboard Devices, Integrated Audio, then turned it to OFF.   I didn't loose any system sounds or sound on any of my programs.   I hope you can find a solution with yours.  I was battling this problem for months.   My Dell Inspiron laptop had no problems with sound.

---

### Post by 0re0 on 2009-07-14
Thanks, unfortunately the hp bios does not have a whole lot of options. Ive been searching for awhile but I will let anyone know if i find some help

---

