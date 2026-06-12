---
title: "Unable to log into Ubuntu via main login GUI after installing NX"
date: 2011-07-18
forum: General Help
---

### Post by welshstew on 2011-07-18
Hi Guys,

First time poster, and a first time convert to using linux, have mainly been a Windows man but as a software dev beginning to broaden horizons using linux (and Eclipse is real fast in ubuntu!!)

Anyway, my problem:
1. I have installed NX as per this form post: [http://ubuntuforums.org/showthread.php?t=736509](http://ubuntuforums.org/showthread.php?t=736509)

2.  I can log in via the tty consoles on the actual machine, and can still log in via the NX console (into a kubuntu environment), however, I am unable to log in to gnome or kubuntu via the main logon gui on the actual computer.

When I do attempt to logon to gnome/kubuntu the screen flickers and I return back to the main logon GUI.


3.  I have since reverted the port 55555 changes to port 22 in /usr/NX/etc/server.cfg  and /etc/ssh/sshd_config - I can still NX onto the box, but point 2 is still a problem.

Can anyone point me in the direction to find out why I can't login via the main GUI???

Many Thanks!!

Stu.

---

### Post by welshstew on 2011-07-18
Sorry, I managed to fix it...  For anyone who runs into this issue please check your 

/home/username/.profile

After running in a Terminal "tail .20 ~/.xsession-errors"
I found I had 
30: Syntax error:  "(" unexpected

I removed the offending .profile line and logged in no problems... :)

I hope thats of help to someone!

---

### Post by wildmanne39 on 2011-07-18
> **welshstew said:**
> Sorry, I managed to fix it...  For anyone who runs into this issue please check your 

/home/username/.profile

After running in a Terminal "tail .20 ~/.xsession-errors"
I found I had 
30: Syntax error:  "(" unexpected

I removed the offending .profile line and logged in no problems... :)

I hope thats of help to someone!
Hi, thank you for sharing your answer for it to help people better,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

