---
title: "No sound in Karmic after login"
date: 2009-11-03
forum: General Help
---

### Post by singpolyma on 2009-11-03
**Solved**
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732/comments/77](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732/comments/77)

**Original Message**
> The GDM sound works, but after I login I have nothing.
It did work yesterday, although one time I had to log out and back it to get it working.
Today when I booted sound was muted, but unmuting didn't help.
I am running DWM, but even when I ran gnome-session to make sure all the background crap was running I get nothing.
Restarting pulseaudio (per [http://pneves.net/2009/06/08/karmic-has-no-sound-after-login/](http://pneves.net/2009/06/08/karmic-has-no-sound-after-login/)) didn't help, nor did restarting ALSA.
The gnome-volume-control correctly shows programs playing audio, and lets me adjust the levels, but no sound is produced.
I'm going to try rebooting now and see if that helps.

---

### Post by aiwarrior on 2009-11-04
Hi i am the owner of pneves.net
The post in my blog was for the Release candidates and i think was later corrected.
It occurred to me once that i was messing around with the audio preferences and changed the output to headphones instead of the normal analog output. It caused me to have no output on the normal computer speakers. If you had sound and had messed with the settings go check it out.

I am sorry if this does not help. I am really pissed with the new release too.

---

### Post by singpolyma on 2009-11-04
I've determined that audio is always set to very low volume and muted after I log in.  Unmuting and turning up the volume has no effect.  If I then kill X and log back in, my volume is down and muted again and this time unmuting and turning up *does* work.  It's very strange.

I may look into tearing out PulseAudio again as I did last release.

---

### Post by aiwarrior on 2009-11-04
That is indeed weird but...it's a new release. In my case i have just downgraded to Jaunty again and will only update further down the line. If Jaunty worked and if you don't really the new stuff i recommend you to do the same.

By the way have you posted a bug already?
Remember to keep the thread updated if you find a solution even if temporary so people can refer to it in case of a problem

---

### Post by singpolyma on 2009-11-05
I had a similar problem in the last release ([https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732)), but it would work right away after being unmuted, instead of needing a logout-and-back-in.

---

### Post by singpolyma on 2009-11-12
Using one thing that worked for the Jaunty bug, I commented out line 378 of /etc/init.d/alsa-utils

Now when I log in my sound is not muted, but I still have no sound (I hear nothing).  Killing X and logging back in then gives me sound, just like unmuting killing and logging in used to (the unmuting being no longer necessary).

---

### Post by spamless on 2009-11-30
> **singpolyma said:**
> Now when I log in my sound is not muted, but I still have no sound (I hear nothing).  Killing X and logging back in then gives me sound, just like unmuting killing and logging in used to (the unmuting being no longer necessary).

I have the same issue but have not tried killing X.  (Not even sure how to do that.)  Karmic 64-bit under AMD.  I hear sounds in general, e.g., from my webcam and on GDM splash just before the login prompt .  Just not once I log in.  I miss it!

---

### Post by wavded on 2009-12-12
After checking alsamixer to see what was muted.  Running this command in a login script fixed it for me:

```
amixer set Master unmute
```

---

