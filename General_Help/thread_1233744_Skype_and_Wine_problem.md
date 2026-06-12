---
title: "Skype and Wine problem"
date: 2009-08-07
forum: General Help
---

### Post by malikge on 2009-08-07
Hi.
When I use skype to make calls first it gave me an error that "audio playback failed".
On ubuntu forms I read about that problem to change the setting of audio devices of skype to pulse. After doing that I can make a test call, I can hear but can't hear my own voice, if someone calls me I can't hear them too.

Someone told me to install wine and use windows skype, ".exe" file. I have installed wine, it seems fine, a virtual c drive and system 32 files etc. But when I try to install skype.exe it starts to download and after installation it gave me an error.

               "We are having problems connecting to the download server.
               To download an alternative installer for Skype, click "Download" button"

When I click the Download button nothing happend.
Can anyone help me... Thanks

---

### Post by P4man on 2009-08-07
using the windows version on wine is a terrible idea, who ever told you that, dont ever list to him again lol. Use the ubuntu version. You may just have to reconfigure the sound input in skype. Go to options, sound devices and experiment with the sound in settings. Also make sure you mic isnt muted. Run alsamixer from the command line, press "tab" to go to inputs and use the arrows to adjust mixer settings.

If none of this helps, you might want to try using the skype Dynamic Static OSS version:
[http://www.skype.com/go/getskype-linux-oss](http://www.skype.com/go/getskype-linux-oss)

edit: easier packaged version (for jaunty):
[http://packages.medibuntu.org/jaunty/skype-static-oss.html](http://packages.medibuntu.org/jaunty/skype-static-oss.html)

---

### Post by malikge on 2009-08-07
> **P4man said:**
> using the windows version on wine is a terrible idea, who ever told you that, dont ever list to him again lol. Use the ubuntu version. You may just have to reconfigure the sound input in skype. Go to options, sound devices and experiment with the sound in settings. Also make sure you mic isnt muted. Run alsamixer from the command line, press "tab" to go to inputs and use the arrows to adjust mixer settings.

If none of this helps, you might want to try using the skype Dynamic Static OSS version:
[http://www.skype.com/go/getskype-linux-oss](http://www.skype.com/go/getskype-linux-oss)

edit: easier packaged version (for jaunty):
[http://packages.medibuntu.org/jaunty/skype-static-oss.html](http://packages.medibuntu.org/jaunty/skype-static-oss.html)


Well I have tried what you have said above but non of them work...
I have tried OSS version and it still is not working...
When I make a test call and when she speaks to record your voice after that nothing happend

---

### Post by P4man on 2009-08-07
can you record in any other app? Try sound recorder, and see if you can record anything at all. If you can't, double or tripple check your microphone settings, it may be muted, may need boost... run alsamixer and verify.

Also have a look in system > preferences > sound. See whats used for recording and test there.

Are you using a laptop with buit-in mic ?

---

