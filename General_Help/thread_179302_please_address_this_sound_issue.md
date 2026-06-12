---
title: "please address this sound issue"
date: 2006-05-19
forum: General Help
---

### Post by shredfitz on 2006-05-19
Okay.  I have reinstalled ubuntu for the nth time.  I run the updates afterward and have also run automatix, but only for some stuff like flash, java, ffox plug-ins, adobe,  multi-media and non-free codecs.  My stystem sound is fine, i.e. I can hear the system alert sounds and the sound that plays at splash or when you log off.  I hear no sound whatsoever when I try to play an audio file or I hear no sound on streaming video ect.  Could someone kindly help me solve this step by step ?  I have searched for the solution elsewhere and on these forums but have not been successful.  The times that I have tried to apply the advice that I do find, I end up in a bigger hole than I was in before.  That is why I am posting this request so I can take it from the top without screwing myself over and over.    What is the first thing I should do ?

---

### Post by Jason_25 on 2006-05-19
Isnt automatix supposed to do that for you?

Anyway, what multimedia backend and frontend are you using to play the file?  What does the relevant log/messaging output from that program say when it does not play?

---

### Post by seth0x2b on 2006-05-19
The sound system may be busy when you try to use the multimedia apps.
I have the same problem with Xmms. I need to double click the song like 3 or 4 times before it starts to.
What does ```
sudo lsof /dev/dsp
``` output when you run the multimedia apps!?

Cheers

---

### Post by shredfitz on 2006-05-19
there is no output.  It appears that the file is playing, but no sound is audible.  As for what frontend/backend I am using, How do I determine that ?

---

### Post by shredfitz on 2006-05-19
seth , totem show this :

COMMAND  PID  USER   FD   TYPE DEVICE SIZE NODE NAME
totem   8613 brian   29w   CHR   14,3      7056 /dev/dsp

---

### Post by seth0x2b on 2006-05-19
well that's normal since you are using totem at the time that you run the command.
```
lsof /dev/dsp 
``` simply lists the apps that use /dev/dsp (the default sound device)
Run the command before you run the application.But I'm not sure that some other app keeping busy the sound device is your problem.It's just something that happens to me from time to time.


Cheers

---

### Post by shredfitz on 2006-05-19
okay so xmms played a file. a file that is stored on my hard drive.  when i tried to play a file from an audio file that is stored a cdrw in xmms, i get no sound.

---

### Post by shredfitz on 2006-05-19
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.

---

### Post by seth0x2b on 2006-05-19
I really can't help you there because I usually keep .ogg backups of my audio cd's on the harddrive.
I'm sure someone will have some info for you in no time.

Cheers

Edit: it shows that error because you are probably forgetting the sudo in front of the command. You can' access the sound device as a normal user.

---

