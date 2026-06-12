---
title: "can anyone tell me what this means?"
date: 2011-01-28
forum: General Help
---

### Post by sbaig on 2011-01-28
Ok so everytime I run skype, I have to connect/disconnect at least 3 times for the other person to be able to hear me , not see, just hear. and very often during this process skype crashes. and the video quality is just terrible compared to when i use to run skype on windows from the same machine.

I ran skype from the terminal and im just wondering what all this output means

```
:~$ skype
X Error, request 133, minor 18, error code 9 BadDrawable (invalid Pixmap or Window parameter) 
X Error, request 133, minor 18, error code 9 BadDrawable (invalid Pixmap or Window parameter) 
X Error, request 133, minor 18, error code 9 BadDrawable (invalid Pixmap or Window parameter) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
```is this a gnome issue? am i the only one with this problem?

---

### Post by mrhhug on 2011-01-29
what version of skype are you using? Skype is not that great for linux to begin with, when i installed i had to play arround the the sound. The intermittent issues are weird thought 

```
skype -v
```

---

### Post by sbaig on 2011-01-29
I'm running Skype 2.1.0.81. But no matter which one I download, either from the skype website or the one in the repositories. I still get the same issues. It's quite annoying.

---

### Post by sbaig on 2011-01-29
> **mrhhug said:**
> what version of skype are you using? Skype is not that great for linux to begin with, when i installed i had to play arround the the sound. The intermittent issues are weird thought 

```
skype -v
```

i also have sound issues as well where the other person cant hear me when we connect , i have to manually drag the volume slider to mute then back to full volume again and u can hear click noises and then th microphone comes back on.

---

### Post by sbaig on 2011-01-30
> X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes) 
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** ERROR: NPN_ReleaseObject() invoke: Broken pipe


anyone know what this is?

---

### Post by derklempner on 2011-01-30
[http://art.ubuntuforums.org/showthread.php?t=1373051](http://art.ubuntuforums.org/showthread.php?t=1373051)

---

