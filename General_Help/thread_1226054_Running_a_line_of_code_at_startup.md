---
title: "Running a line of code at startup"
date: 2009-07-29
forum: General Help
---

### Post by merdok1981 on 2009-07-29
Hi Guys,

I've recently installed webcam-server, the startup script that came with it was not something I could get working but I managed to make it work using the following terminal code:

export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so; webcam-server -d /dev/video1 -c 
PUDDLESCAM! -g 640x480

Problem is, I have to put this full thing in terminal every time my system boots and then leave the terminal window open to keep it going, is there a way I can get it to run automatically?

I'm still a bit of a noob when it comes to linux so sorry if this is a really stupid question.

---

### Post by unutbu on 2009-07-29
Edit /etc/rc.local:
```

gksu gedit /etc/rc.local
```

Put the command at the end, but *before* the "exit 0" line.
This will cause the command to be run as root near the end of the boot process but before you log in.

---

### Post by merdok1981 on 2009-07-29
Excellent! Thank you very much :)

---

### Post by merdok1981 on 2009-07-29
hmm... well I just did a reboot and altough I didnt get an error message, the script does not appear to be running.

---

### Post by merdok1981 on 2009-07-29
My bad, the code was split across two lines. Its working now.

---

### Post by unutbu on 2009-07-29
Edit: Oh, okay, very good.

---

