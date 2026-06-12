---
title: "Applications stop opening after some time."
date: 2009-08-13
forum: General Help
---

### Post by arturhoo on 2009-08-13
Hi,

I'm running Ubuntu 9.04 x86 - Gnome Desktop Env. on a Core2Duo, 4 GB RAM, Proprietary NVIDIA driver (8800 GTS). Today a strange thing happened when I logged in: applications would not open after some time, none of them, calc, gedit, nautils, browser or terminal. I would just get the "Starting ..." box in the task bar.

Applications that were already opened would still run normally. Just a X restart would get things back to normal - for another 5 minutes or less. I tried another kernel and it did not solve the problem. Even tough, if I logged as root, everything would work just fine.

Another thing that happened was that cycling through the tty's and coming back to tty7 would crash the system completely, making a hard reset the only way out.

I could also notice that it would still happen if I just logged in and waited for 5 minutes or less.


Finally, I searched within the forums and did not find something related to that.

Thank you for your support.

---

### Post by arturhoo on 2009-08-13
Somewhat related to this problem here:

[http://ubuntuforums.org/archive/index.php/t-345361.html](http://ubuntuforums.org/archive/index.php/t-345361.html)


I will just try to leave a terminal opened, and wait for the problem to start, and them try to open any application though the terminal and see what is the output.

---

### Post by sprintexec on 2009-08-13
My frustration with ubuntu is going through the roof. I just installed 9.04 after having a dismal time with hardy heron. It (9.04) started off working fine. then I tried using evolution which seemed to work ok. Then I opened flash on an adobe website and the whole thing froze up and every time I went to restart it all I got a screen full of rubbish.  This is crazy...

---

### Post by arturhoo on 2009-08-13
Opening  Gedit gives me:

Maximum number of clients reached
(gedit:9328): Gtk-WARNING **: cannot open display: :1.0


Nautilus:
Maximum number of clients reachedCould not parse arguments: Cannot open display: 

Firefox:
Maximum number of clients reachedError: cannot open display: :1.0

---

### Post by DeMus on 2009-08-13
> **sprintexec said:**
> My frustration with ubuntu is going through the roof. I just installed 9.04 after having a dismal time with hardy heron. It (9.04) started off working fine. then I tried using evolution which seemed to work ok. Then I opened flash on an adobe website and the whole thing froze up and every time I went to restart it all I got a screen full of rubbish.  This is crazy...

Please get your own thread instead of stealing somebody else's.
Your subject isn't even related to the one written by the OP.

---

### Post by arturhoo on 2009-08-13
Thank you all for your support.


Here is what was happening:

I have a script that runs in my sessions startup, which is supposed to disable my touchpad whenever my USB MOUSE is inserted. It detects my USB mouse by its name.

Today I changed my usb mouse, and the script went on a loop, starting many syndaemon's, which caused the XLib collapse.

Script fixed, problem solved. Thread may be closed.

---

