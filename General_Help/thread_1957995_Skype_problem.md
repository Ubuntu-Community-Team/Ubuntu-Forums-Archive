---
title: "Skype problem"
date: 2012-04-13
forum: General Help
---

### Post by beceraful on 2012-04-13
When i call somebody he heards me but i can't heard him. The sound is fixed and everything is normal , but the last problem is the skype i want to hear what the other person says. When i talk he heard me but i can't heard him. How can i fix that. I am with ubuntu 11.04

---

### Post by beceraful on 2012-04-13
Can someone tell me what to do to fix this problem?

---

### Post by jadtech on 2012-04-13
there is a good chance since you cant hear the other person the trouble can be on there end ..

---

### Post by jonobr on 2012-04-13
If regular sound works on your machine and skype uses the same sound output then I agree with jadtech, problem is most likely skype , skyppe being blocket at the other end or a problem with their setup

---

### Post by beceraful on 2012-04-13
but i don't know what to do to fix the problem....

---

### Post by jonobr on 2012-04-13
Have your friend call or be called by someone else on Skype or make the test call.

if they see the same issues there is nothing you can do.

---

### Post by alex2e1gzy on 2012-04-13
Can't you use Skype's Echo Test call? echo123 if i remember correctly. You should be able to hear somebody speaking and then test if they can hear you through playback. If that works - you are set up correctly on your computer, so the issue must be at their end...

Let us know,

---

### Post by Rodney9 on 2012-04-13
Fix internal mic for use with Skype

[http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol](http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol)

sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Thanks To ZekeGraal

---

### Post by beceraful on 2012-04-14
The problem is the people can heard me but i can't heard them , this thread is about that , that i can heard the people right?

---

### Post by jockyburns on 2012-04-14
Have you turned the volume up on your computer?

---

### Post by beceraful on 2012-04-14
yes

---

### Post by beceraful on 2012-04-16
Some way to fix the problem ?

---

### Post by HermanAB on 2012-04-16
Are you perhaps running 64 bit Linux?  Skype is a 32 bit program.  To get sound to work, you need to install some 32 bit libraries.  Skype will not complain if they are not present, it just won't work right.  

For example:
libv4l
pulseaudio-libs
alsa-plugins-pulseaudio

Make sure that you have the 32 bit i686 versions of those libraries installed.

---

### Post by beceraful on 2012-04-16
pulseaudio is working , i fixed the sound at all , but in skype i can't heard the person. You mean the whole linux sound or the skype sound to heard them ? I don't understand , the whole sound on linux or the skype to heard them ? 

I fixed the whole sound on linux only this problem with that can't i heard them is the problem.

---

### Post by HermanAB on 2012-04-16
Howdy,

If you are running 64 bit Linux, then sound will work for all other 64 bit programs, but Skype sound will not work, since it requires 32 bit libraries to connect to the Linux sound system.

So make sure that you have the 32 bit i686 sound libraries installed.

---

### Post by beceraful on 2012-04-17
I don't know how....

---

