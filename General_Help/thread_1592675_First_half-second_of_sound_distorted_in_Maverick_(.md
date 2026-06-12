---
title: "First half-second of sound distorted in Maverick (pulseaudio)"
date: 2010-10-10
forum: General Help
---

### Post by spoon_ on 2010-10-10
Any sound playing through pulseaudio is distorted for the first half-second or so. Sounds like a buzzing or crackling or something. This happens, for example, in Pidgin and Clementine (music player). If I set these programs to output through alsa instead of pulseaudio, there's no such problem. Also no such problem existed in 10.04. And I tried the fix in the sticky, nothing changed.

Edit: probably less than a half second of distortion, really. Maybe 100ms.

---

### Post by andrewthomas on 2010-10-10
Did you read the sticky?
 
See the second post
 
[http://ubuntuforums.org/showpost.php?p=9948061&postcount=2](http://ubuntuforums.org/showpost.php?p=9948061&postcount=2)

---

### Post by spoon_ on 2010-10-10
Yep, I mentioned in my original post that I tried the fix suggested in the sticky and nothing changed.

---

### Post by Sennaista on 2010-10-11
I think I have the same problem. If I fast-forward in Rhythmbox the music always starts with a distortion too.

---

### Post by danbuter on 2010-10-11
I'm glad MM didn't ship with any obvious basic bugs.

---

### Post by ellgor on 2010-10-11
Hi,

I was having the same issue, it also affected playback in Vlc and a couple of other apps I have since worked out, cause "Pulseaudio", completely removed it, now sound is restored amd music now sounds like its not been played at the bottom of a bucket.

Regards, Ellgor.

---

### Post by NCLI on 2010-10-11
How about reporting this as a bug in Pulseaudio instead of removing it -_-

---

### Post by Polyphenolic on 2010-10-12
Confirming same problem. Also came across the same "fix" in the sticky and applied it, but to no avail.

---

### Post by moteprime on 2010-10-22
Have anybody filed a bug on this issue?
I found this one, but it does not appear do cause much activity.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/609556](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/609556)

---

### Post by fleamour on 2010-11-02
Try here:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Took me a long while to find, I am author of bug-609556.

---

### Post by fleamour on 2010-11-02
Re-compiling ALSA kernel via CLI worked!!!

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

Yey!!!

---

### Post by moteprime on 2010-11-04
I got to admit that it is over my head to figure out what to do from that link, and i don't what to screw up my configuration.
For some reason the only application having the problem now is Pidgin, and i found an easy solution by picking Alsa from the pidgin preferences menu.

---

### Post by fleamour on 2010-11-04
Glad it's sorted.

---

### Post by fleamour on 2010-11-04
Damn it!  Although Pidgin alerts now cause no distortion & You Tube vids will play OK.  After compiling ALSA kernel:

[http://monespaceperso.org/blog-en/20...id-lynx-10-04/](http://monespaceperso.org/blog-en/20...id-lynx-10-04/)

The problem has now switched to playing any MP3 via Exaile.  This was OK before.

Bum.

---

### Post by fleamour on 2010-11-04
It would seem picking OSS from Exaile's playback tab, closing Exaile, & restarting solves the broken up audio.

---

### Post by moteprime on 2010-11-05
For me the problem is still the same, but i haven't been messing with alsa.

---

