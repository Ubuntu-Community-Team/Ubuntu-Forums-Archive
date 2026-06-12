---
title: "no volume control"
date: 2010-01-16
forum: General Help
---

### Post by m4tic on 2010-01-16
My hard drive has been giving me a problem, after a failed proper login my gnome-panel did not load. After a reboot i got it back but my volume control was not there. Clicking on Sound in System-->Preferences gives "Waiting for sound system to respond". I have restarted a lot of times, i have sound but i just cannot adjust it.

---

### Post by jmszr on 2010-01-16
m4tic,

Right click on an empty space on panel > click on Add to Panel > scroll down to "Notification Area" > Add. That should do it.

---

### Post by llamabr on 2010-01-16
You can also adjust it via the terminal with alsamixer

---

### Post by jmszr on 2010-01-16
Speaking of which, you can also```
sudo apt-get install alsamixergui
```which you can then access through Applications > Sound & Video, come to think of it.

---

### Post by m4tic on 2010-01-17
notification area thing did not work, i got it back by deleting ```
~/.pulse
``` the path should recreate again within a second and so is the volume applet on the panel. I should've seen this from the output ```
user@userpc:~$ pulseaudio
E: core-util.c: Failed to stat runtime directory ~/.pulse/33ac8da344bd6c5cfdd48de04b4f68b4-runtime: Invalid argument

```I think this fix should be looked at and included somewhere in the pulseaudio tutorials or something

---

### Post by m4tic on 2010-01-17
I tested this on a machine which had no sound after upgrade to Lucid Alpha 1, it worked also. Also when playing something like audacious, it used to show an error message at /var/log/messages.

---

### Post by anur.bhargav on 2010-01-18
> **jmszr said:**
> m4tic,

Right click on an empty space on panel > click on Add to Panel > scroll down to "Notification Area" > Add. That should do it.

Thanks a ton.... i got back all my icons back(Volume control applet,Network Manager Applet,etc.....):D;):popcorn::o:):(

---

