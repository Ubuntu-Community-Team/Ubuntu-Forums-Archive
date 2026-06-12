---
title: "how can I make my soundcard recognized by alsa?"
date: 2010-10-09
forum: General Help
---

### Post by hihihi100 on 2010-10-09
```
!!Sound Servers on this system !!
---------------------------- 

Pulseaudio:       
Installed - Yes (/usr/bin/pulseaudio)       
Running - Yes  

ESound Daemon:       
Installed - Yes (/usr/bin/esd)       
Running - No  

Jack:       
Installed - Yes (/usr/bin/jackd)       
Running - No   

!!Soundcards recognised by ALSA !!
-----------------------------    

!!PCI Soundcards installed in the system !!
--------------------------------------  

00:0f.0 Audio device: 
Silicon Integrated Systems [SiS] Azalia Audio Controller  
```

Why does that happen?

cheers

---

### Post by ellgor on 2010-10-10
Hi,

In a terminal type in:  

alsamixer

a small window should open in the left corner (alsa) follow the advice given in the window
(F1 - F6) do various things and capture this and that, hope this is of help.

Regards, Ellgor.

---

