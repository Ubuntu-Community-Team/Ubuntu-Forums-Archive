---
title: "Skype and music"
date: 2006-04-29
forum: General Help
---

### Post by csseurg6 on 2006-04-29
Hello,

how to play music and in the same time, speak on Skype?


bye,
fred

---

### Post by ajgreeny on 2006-04-29
I eventually managed to do this (with the exception of recording sounds with Audacity or krecord) by following the information in this thread:-
[http://ubuntuforums.org/showthread.php?p=653625](http://ubuntuforums.org/showthread.php?p=653625)
It also seems worth trying to stop the hijacking of the skype system after the first call by disabling the file *hangup.wave* in /usr/share/skype/sound/ by renaming it *hangup.wav-disabled*.  The file is owned by you so you will not need to do this as root, or that was so in my case anyway.
Now, if only it didn't take so long to start up skype and logon it would be perfect.

---

