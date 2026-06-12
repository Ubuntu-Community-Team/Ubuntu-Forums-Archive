---
title: "Popping sound when start and end audio."
date: 2011-06-15
forum: General Help
---

### Post by joelstitch on 2011-06-15
I upgraded to Ubuntu 11.04 Natty Narwhal and now there's a popping sound  every time I log in, log off before I start audio/movie and after I close an audio program or movie. I notice that is a common issue for Maverick and Natty but couldn't find how to fix it. Any help will be appreciated!

---

### Post by DirtyPC on 2011-06-15
> **joelstitch said:**
> I upgraded to Ubuntu 11.04 Natty Narwhal and now there's a popping sound  every time I log in, log off before I start audio/movie and after I close an audio program or movie. I notice that is a common issue for Maverick and Natty but couldn't find how to fix it. Any help will be appreciated!

 run alsamixer and adjust the PCM volume to 0.00 gain. Run sudo alsactl store 0 to save it so it persists through reboot.

---

### Post by joelstitch on 2011-06-15
The PCM was already to 0.00.

---

### Post by DirtyPC on 2011-06-15
then try

$ alsamixer -Dhw

---

### Post by joelstitch on 2011-06-15
This is what I get:

[IMG]http://www.postapocalypticgear.org/files/psm.png[/IMG]

---

### Post by DirtyPC on 2011-06-15
set playback to auto detect

---

### Post by joelstitch on 2011-06-15
> **harrylucas1 said:**
> set playback to auto detect

How do I do that?

---

### Post by DirtyPC on 2011-06-15
NC on Ubuntu at the moment. Racking my brain, try F3 and see what on-screen options are there.

---

### Post by joelstitch on 2011-06-15
It didnt do anything.

---

### Post by DirtyPC on 2011-06-15
sorry, try increasing PCM volume!

---

### Post by joelstitch on 2011-06-15
It seems like that did it. But now VLC has no audio. Aaaaggghhh I should have stayed with Lucid!

---

### Post by DirtyPC on 2011-06-16
> **joelstitch said:**
> It seems like that did it. But now VLC has no audio. Aaaaggghhh I should have stayed with Lucid!
I agree! But what's done is done. 

Make sure the vlc-plugin-pulse is installed and then open vlc -> tools -> preferences, click on the audio icon and in output drop down on right change from default to pulseaudio

---

### Post by joelstitch on 2011-06-16
VLC is working now but it seems like the PCM didnt do anything. It is still doing the noises when before and after I play a sound.

---

### Post by DirtyPC on 2011-06-16
remember my earlier post about saving it so it persists through reboot?

> sudo alsactl store 0 to save it so it persists through reboot.

---

### Post by joelstitch on 2011-06-17
It still does it.

---

### Post by joelstitch on 2011-06-22
I tried the directions on [http://ubuntuforums.org/showthread.php?t=1759570](http://ubuntuforums.org/showthread.php?t=1759570).

I installed pulseaudio and pavucontrol and set the settings like on the attached image.

---

### Post by joelstitch on 2011-06-29
Nevermind, its still doing the popping sounds :(

---

### Post by coldraven on 2011-06-29
Yes, I get the popping sound but that's because I enabled it.
[IMG]http://ubuntuforums.org/home/jamie/Desktop/sound-prefs.png[/IMG]
[IMG]http://ubuntuforums.org//home/jamie/Desktop/sound-prefs.png[/IMG]

---

