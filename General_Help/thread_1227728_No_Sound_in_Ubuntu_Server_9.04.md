---
title: "No Sound in Ubuntu Server 9.04"
date: 2009-07-31
forum: General Help
---

### Post by rootless on 2009-07-31
Hey, I was wondering if anyone could take a swing at this problem I've been having. I've built my own minimalistic distro on top of ubuntu server 9.04, and I'm not getting any sound!

My thinkpad's (R40) volume is turned up, unmuted, and alsa is unmuted and turned up as well. I have fluxbox, alsa-base, alsa-utils, gnome-alsamixer, linux-sound-base and pulseaudio. Could this be a driver problem? If so, how should I proceed?

I know that this computer can play sound because before, when I was running a vanilla install of ubuntu hardy it was working fine.

For some reason, now, when I call alsamixer, I get "alsamixer: function snd_ctl_open failed for default: no such file or directory"

---

### Post by rootless on 2009-07-31
I just found a thread just like this one, but it was never solved. Same deal. IBM R40, ubuntu server, no sound.

[http://ubuntuforums.org/archive/index.php/t-1063807.html](http://ubuntuforums.org/archive/index.php/t-1063807.html)

---

### Post by rootless on 2009-07-31
aaand another.

[http://ubuntuforums.org/showthread.php?t=860919](http://ubuntuforums.org/showthread.php?t=860919)

It seems like nobody has been able to do this... maybe i should reinstall server but with a desktop kernel?

---

### Post by dcstar on 2009-07-31
> **rootless said:**
> Hey, I was wondering if anyone could take a swing at this problem I've been having. I've built my own minimalistic distro on top of ubuntu server 9.04, and I'm not getting any sound!
........

By definition a "server" install does not have any of the superfluous stuff that comes with a desktop distro - like sound or graphics.

As well, Ubuntu now uses the Pulseaudio sound system which is heavily tied into the desktop configurations - older sound systems were not nearly as finicky.

---

### Post by MaxIBoy on 2009-07-31
I would imagine that a server kernel would not include soundcard drivers, as there would be no reason for it. You can install a desktop kernel from the repositories without reinstalling the OS. 

In any case, the server kernel isn't well-suited for desktop use (optimized for throughput over latency,) so for optimum performance you should get a desktop kernel anyway.

This can be accomplished by running the command```
sudo apt-get install linux-image-generic
```Which will install the most recent version of the generic kernel for whatever version of the distro you have.

---

### Post by rootless on 2009-07-31
Is there anything I need to do after running that command?

---

### Post by rootless on 2009-07-31
I ran the command and got "linux-image-generic is already the latest newest version"

---

