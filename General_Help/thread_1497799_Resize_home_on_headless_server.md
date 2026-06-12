---
title: "Resize /home on headless server?"
date: 2010-05-31
forum: General Help
---

### Post by jerome1232 on 2010-05-31
I am trying to shrink /home on a headless server, I understood it was possible to umount /home while a system was running but that doesn't seem to be working, is that not possible while ssh'd into the computer?

To me it looks like the user I ssh'd in as (jerome) has bash running in /home, is there a way to do this remotely or will I have to drag this thing out of it's corner and hook up a monitor and keyboard.

Maybe this is helpful information maybe it's not
```
jerome@voiceserv:~$ sudo -i
root@voiceserv:~# umount /home
umount: /home: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
root@voiceserv:~# lsof /home
COMMAND   PID   USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
bash    12546 jerome  cwd    DIR  251,0     4096 6291457 /home/jerome
root@voiceserv:~# ps -p 12546
  PID TTY          TIME CMD
12546 pts/2    00:00:02 bash
root@voiceserv:~# who
jerome   pts/2        2010-05-30 23:59 (main)
root@voiceserv:~# pwd
/root

```

---

### Post by jerome1232 on 2010-05-31
Wow scratch that I figured it out as I hit post, turns out I intiated a bash session from /home using sudo -i, cd'ing out of /home then becoming root fixed it.

---

