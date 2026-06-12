---
title: "upgraded to 9.10, now no sound in firefox flash"
date: 2009-11-04
forum: General Help
---

### Post by Glich on 2009-11-04
I've recently upgraded to Ubuntu 9.10 form 9.04. Everything was working fine on 9.04. In 9.10 the sound in firefox flash does not work. For instance, I can watch, click start/stop for youtube videos but I can not hear any sound. I can do the same for iPlayer as well.

When I go to sound preferences the dialogue box is out of shape and there are many enteries for the firefox application as the screenshot shows. The dialogue box looks fine before I try playing sound in firefox and if I only try to play music in rhythmbox.

Thank you for any help!
Glich.

---

### Post by Glich on 2009-11-04
I also get this sound related error when I run firfox 3.5 from terminal and try to play a youtube video:

ALSA lib pcm_pulse.c:724:(pulse_prepare) PulseAudio: Unable to create stream: Too large


Please help.

---

### Post by hesto on 2009-11-04
I am also having this problem.  I have tried reinstalling flash player also and it does not fix it.

Help would be very nice!

Thank you
Hesto

---

### Post by phillw on 2009-11-04
lovinglinux keeps an excellent thread of firefox issues over here ..... [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Because it is a good thread, you might want to start at the last page, and go back a few pages to see if it has been noted there.

If it hasn't, then pop a note there ... it's a well supported thread.

Phill.

---

### Post by Glich on 2009-11-04
Thanks for the messages. I managed to solve my problem simply by removing pulseaudio. Everything works fine for me now.

---

### Post by khopek on 2010-01-01
I just upgraded to 9.10 and am having a similar problem. I installed the generic flash drivers as well as the Adobe flash, and sound will work perfectly for a bit, but it will randomly stop. The only way I have found to fix this is to log out then back in of Ubuntu.

Let me clarify that I only have sound issues while trying to watch/listen to Flash Objects. System sound works perfect.

---

