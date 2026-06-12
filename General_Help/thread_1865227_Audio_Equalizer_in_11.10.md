---
title: "Audio Equalizer in 11.10?"
date: 2011-10-19
forum: General Help
---

### Post by Nixarter on 2011-10-19
I would like an equalizer for 11.10.  I know they come with many programs, BUT they only apply to a single program.  I want a system-wide equalizer (lower level) that modifies all sound.

Is there such a program?

---

### Post by Nixarter on 2011-10-21
well, I kinda found one.  But it says for only up to 10.10 or so (maybe just 10.04), and I'm on 11.10.  URL to site---> [Pulseaudio System-wide Equalizer](http://www.webupd8.org/2010/02/pulseaudio-system-wide-equalizer-now.html), and to a UF thread about it [(Thread Link)](http://ubuntuforums.org/showthread.php?t=1308838).

The instructions only apply to those older versions, but I tried it anyway... and it didn't work.  (W: Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found) and so on

any ideas on another one, or a way to get this one to work?

---

### Post by oldos2er on 2011-10-21
The webupd8 PPA has pulseaudio-equalizer for 11.10. 

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

---

### Post by reality1011 on 2012-03-27
> **oldos2er said:**
> The webupd8 PPA has pulseaudio-equalizer for 11.10. 

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

Worked like a charm  Thanks!


```

  206  sudo add-apt-repository ppa:gwibber-daily/ppa
  207  sudo apt-get update
  208  sudo apt-get install pulseaudio-equalizer
  209  which pulseaudio-equalizer
  210  /usr/bin/pulseaudio-equalizer

```

---

