---
title: "PulseAudio not working and filling up /var/log"
date: 2010-06-01
forum: General Help
---

### Post by ProN8 on 2010-06-01
Recently I rearranged my system to have the home folder in a separate partition (in addition to a dual boot with Windows 7 that I already had).  Around that same time the volume buttons on my keyboard stopped working and when I try to adjust the volume by going to System>Preferences>Sound it just says "waiting for sound system to respond".  I can still get sound and if the player has it's own volume adjustment I can change it there but not at the system level.  

At first I was ok with it but later I started getting messages that my file system was filling up,  so I looked in the Disk Usage Analyzer and found that /var/log was 8.0 GB the largest files were user.log(1.6 GB) and messages.1(1.2 GB) they were both filled with different errors from pulseaudio

messages.1 had 
"lock-autospawn.c: Cannot access autospawn lock."  
printed over and over again

and user.log had these three lines
"core-util.c: Home directory /home/nathan not ours.
lock-autospawn.c: Cannot access autospawn lock.
main.c: Failed to acquire autospawn lock"

(each line started with the date, time, my username, and pulseaudio[*number*])

---

### Post by benplanet on 2010-06-02
i'm in the same boat, it's been a full week now .. still no solution.

---

### Post by SudoNikon on 2010-06-23
Same here. Thousands of pulseaudio errors at a rate of about 30 a second. Need some help here.

Here is an example of syslog:
[http://pastebin.ca/1889159](http://pastebin.ca/1889159)
(tail of the last 50 messages)

---

### Post by tommcd on 2010-06-23
You can safely delete all those log messages in /var/log/user.log, /var/log/syslog, and /var/log/messages.

PulseAudio is a huge resource hog. Many people, including me, happily live without it. Unless you really need PulseAudio for some specific reason, consider removing it and just using alsa:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273)

---

### Post by SudoNikon on 2010-06-23
> **tommcd said:**
> You can safely delete all those log messages in /var/log/user.log, /var/log/syslog, and /var/log/messages.

PulseAudio is a huge resource hog. Many people, including me, happily live without it. Unless you really need PulseAudio for some specific reason, consider removing it and just using alsa:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273)

Works! :D Thanks

---

### Post by afrodeity on 2010-11-09
you removed pulseaudio?

---

