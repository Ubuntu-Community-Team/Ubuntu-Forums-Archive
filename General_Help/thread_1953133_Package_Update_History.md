---
title: "Package Update History"
date: 2012-04-05
forum: General Help
---

### Post by eckeroo on 2012-04-05
After an update, sometimes something goes wrong with another package due to a conflict with the new updates. Is there an updates history so I can see what packages have been recently updated?

FYI, the atari800 emulator now has a problem with choppy sound.

---

### Post by Dave_L on 2012-04-05
The logs are kept in /var/log/apt/

You can view those files manually, or with Log File Viewer.

Synaptic also displays history.

---

### Post by ajgreeny on 2012-04-05
You can also use the terminal command ```
cat /var/log/dpkg.log.1 /var/log/dpkg.log | grep upgrade
```
This command with minor changes is also useful to see what you have installed or removed by changing the final word **upgrade** to **install** or **remove**

---

### Post by eckeroo on 2012-04-06
It's not just the atari800 emulator program that has choppy sound, the mp3 playback quality has also reduced. I now suspect something has reduced the performance of the ALSA driver.

Looking at the dpkg.log, it would seem the last linux kernal update on the 29/3/2012 is the most likely culprit.

Is it possible to rollback linux kernels?

---

### Post by Jose Catre-Vandis on 2012-04-06
To test, you can select the previous kernel from grub, if this works then you can set grub to default boot from that kernel

---

### Post by raja.genupula on 2012-04-06
> **ajgreeny said:**
> You can also use the terminal command ```
cat /var/log/dpkg.log.1 /var/log/dpkg.log | grep upgrade
```This command with minor changes is also useful to see what you have installed or removed by changing the final word **upgrade** to **install** or **remove**

+1 I got few more similar 
[http://askubuntu.com/questions/14328/where-can-i-look-up-my-update-history](http://askubuntu.com/questions/14328/where-can-i-look-up-my-update-history)

---

### Post by eckeroo on 2012-04-06
Having tried previous kernel releases (holding down shift at boot), I can rule out the kernel update as the reason for the ALSA reduced performance. [thanks Jose Catre-Vandis for tip]

I'm now stuck again.

---

### Post by eckeroo on 2012-04-08
I've found a fix for the problem: adjusting the PCM volume on the mixer. At certain PCM volume levels the sound just sounds awful.

---

