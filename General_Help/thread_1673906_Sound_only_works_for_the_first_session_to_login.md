---
title: "Sound only works for the first session to login"
date: 2011-01-23
forum: General Help
---

### Post by mashedbear on 2011-01-23
Our family PC is shared by 5 users. The first user to login has sound working fine - no problem in all applications, also more than one app can play sound at the same time. But when a user switches to another user session - ie without the first user logging out - then the sound will not work in the second session (all applications affected, system sounds affected). 

I have two workarounds - neither are very nice. One - log out all other user sessions; or 2 restart alsa ie ```
sudo alsa force-reload
```

How can I troubleshoot / fix the issue?

My system is Ubuntu 10.10 (2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux). 

My version of alsa is Advanced Linux Sound Architecture Driver Version 1.0.23.

cheers

---

### Post by sanderj on 2011-01-23
Interesting: I have something similar: When a second account is logged on (or has been logged on), the sound is gone for the first user.
Relevant or not: the second user has sound muted. I don't know if this is related, and I don't know if it's the second user's or a system's choice.

Only solution so far: reboot Ubuntu.

---

### Post by mashedbear on 2011-01-23
Thanks sanderj

Sounds similar. But in my case the second user does not have sound muted. 

I've been looking in syslog and have found the following entry at about the right time the 'second user' is trying to play sound:  > pulseaudio[6037]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy

Seems to be the cause - but if so how do I fix this?

Cheers

---

