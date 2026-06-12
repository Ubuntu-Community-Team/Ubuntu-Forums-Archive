---
title: "gksu nautilus"
date: 2010-02-10
forum: General Help
---

### Post by Tourdog on 2010-02-10
I get the following each time using  "terminal":

tourdog@PJK3:~$ gksu nautilus
Initializing nautilus-gdu extension

** (nautilus:2347): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2347): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2347): WARNING **: No marshaller for signature of signal 'ShareCreateError'


The "root - File Browser" comes up and it all seems to work but "what's up with the 3 warnings"?

---

### Post by doas777 on 2010-02-10
well, the nautilus-gdu extensions deal with flash drives, if that helps point you in the right direction.

---

### Post by Tourdog on 2010-02-10
doas777,

Is there any way to mitigate the *** WARNING *** ?    The #2347 points toward the problem?   Or, if a solution is there I surely don't see it.

Flash Drives on or not, same "WARNING".

Does anyone else have this show up?
TIA!

---

### Post by doas777 on 2010-02-10
I always get a warning when gksu'ing nautilus, mainly about my theme. since the theme is on my profile but not roots, it kicks the warning.

I'm seeing some folks with the same problem, but it doesn't seem to cause them any issue. it looks like an issue related to the DBUS, so it kind of makes sense that another profile could not plug into the dbus to subscribe for messages.

not seeing any fixes, but some people have recomended reinstalling the ubuntu-desktop package. I would not recomend you do that unless you have a real issue.

---

### Post by Tourdog on 2010-02-10
doas777,

Your direction is good!   It's not hurting anything so "leave it alone"!    Well done!   Thank you!  :D !

---

