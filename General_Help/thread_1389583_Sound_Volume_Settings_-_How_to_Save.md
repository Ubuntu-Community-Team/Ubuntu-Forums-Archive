---
title: "Sound Volume Settings - How to Save?"
date: 2010-01-24
forum: General Help
---

### Post by Sky Aisling on 2010-01-24
This questions concerns how to save the volume settings in sound mixer applications.

Here's the situation:
There is a 'sound mixer' icon in XFCE panel that allows me to increase my speaker volume.  
The sound mixer window offers two apps; Yamaha DS-1E (YMF754) Alsa mixer and Asahi Kasei Ak4543 (Oss mixer).
Each of the apps have configuration choices which seem to work properly.
The problem is that they do not save my choices at the end of a session.

My sound is low on this machine (Toshiba Satellite vintage 2002).  I set the volume when I power up in the morning and then have to reset it the next day as the configuration is lost at power down.  I have sound but it is low so I boost it up when I go to listen to videos or newsclips...

 The mechanical volume adjuster on the machine set to high.

Is there a 'save' button I am missing?

---

### Post by Leppie on 2010-01-24
are you using the save session option?

---

### Post by Sky Aisling on 2010-01-24
I thought I was.  Oh, oh!
I found the save sessions settings. No, I am not saving sessions.  Looks like I need to look at this and set up my save sessions configuration.

Question:  Does 'saving the session' begin to build a large archieve file that might hinder my limited storage space?

Thank you...

---

### Post by Leppie on 2010-01-24
> **Sky Aisling said:**
> I thought I was.  Oh, oh!
I found the save sessions settings. No, I am not saving sessions.  Looks like I need to look at this and set up my save sessions configuration.

Question:  Does 'saving the session' begin to build a large archieve file that might hinder my limited storage space?

Thank you...
i don't believe so. it should only create some config file while with some info on open apps and their settings when exiting the system.

---

### Post by Sky Aisling on 2010-01-24
I am testing the save session now.  If this solves the problem I will return and mark this thread saved.  Thank you in advance.

Questions:  By turning the volume to max on either one of these mixer apps will I cause any problems for the tiny speakers in this machine?  Will turning up volume to max cause the machine to draw extra power?  Should I be circumspect in raising the volume?

---

### Post by Leppie on 2010-01-24
> **Sky Aisling said:**
> I am testing the save session now.  If this solves the problem I will return and mark this thread saved.  Thank you in advance.

Questions:  By turning the volume to max on either one of these mixer apps will I cause any problems for the tiny speakers in this machine?  Will turning up volume to max cause the machine to draw extra power?  Should I be circumspect in raising the volume?
i know that pulseaudio can overload the speakers. if you have a physical colume control, you could set the software controls to the max you like and use the physical one to prevent your speakers from getting fried during boot/halt.

---

### Post by Sky Aisling on 2010-01-24
Situation:

Logout Settings:
Automatically save session at log out option is on.
Prompt at log out is on.

I 'restarted' the system.

Volume control settings on mixers did not save.

Hummm?

---

### Post by Leppie on 2010-01-24
have you checked the pulseaudio settings?

---

### Post by Sky Aisling on 2010-01-24
I am not familiar with 'pulseaudio'.  Catfish tells me I have 'pulseaudio' icons but does not show an application in the system.

---

### Post by Sky Aisling on 2010-01-24
Regarding: the 'save session' at log out time...
Do 'Shut Down', 'Restart', 'Log Out' all save the session setting?
Are the 'save session' options related only to the 'Log Out' command?

I am setting the save sessions options via Applications/Settings/Session and Startup.

---

### Post by Leppie on 2010-01-24
i will have to investigate a bit more then...

---

### Post by Sky Aisling on 2010-01-24
Thank you.  I'll sit with it also.  I'll leave the thread open.

Ubuntu's ease of use is a delight to me (I am a recovering MS user).  The ease of how it takes care of saving files is so appreciated.  All the other settings that I've tinkered with so far take just by closing the window.  Seems like this mixer settings should too.  Maybe there is a bug in that settings window.

---

### Post by Leppie on 2010-01-24
> **Sky Aisling said:**
> Thank you.  I'll sit with it also.  I'll leave the thread open.

Ubuntu's ease of use is a delight to me (I am a recovering MS user).  The ease of how it takes care of saving files is so appreciated.  All the other settings that I've tinkered with so far take just by closing the window.  Seems like this mixer settings should too.  Maybe there is a bug in that settings window.
i used to have sound level issues as well, but am using pulseaudio now and all is working fine. you may want to try installing that in the meantime.

try also looking in the xfce settings: Applications>Settings>Settings Editor

---

