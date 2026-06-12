---
title: "DVD not being recognised in Ubuntu"
date: 2010-08-04
forum: General Help
---

### Post by DavidG24 on 2010-08-04
hi guys,

let me preface this by saying I am a complete noob with Ubuntu, so I know I won't be providing all the required information to actually address the problem.

I'm running Ubuntu 10.04 and have just got the built in Mplayer (only change made happened first time I played a DVD and it automatically downloaded the required codec) ; I have a DVD that it not being recognised by Ubuntu and when I force it open in Mplayer nothing happens. I tried installing VLC however it still wouldn't run. Weirdly (or maybe not?) the DVD works fine in a XP virtual os through VirtualBox using Windows Media Player Classic...

Any starters would be greatly appreciated.

Cheers,

David

---

### Post by theozzlives on 2010-08-04
Have you tried [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")?

---

### Post by DavidG24 on 2010-08-04
hey mate,

installed mediubuntu...no luck unfortunately; maybe if I install windows media player classic under wine...

Cheers,

David

---

### Post by ajgreeny on 2010-08-04
Read [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and follow all the instructions.

So simply put, you need to install **ubuntu-restricted-extras**, then run the command 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
``` in terminal

---

