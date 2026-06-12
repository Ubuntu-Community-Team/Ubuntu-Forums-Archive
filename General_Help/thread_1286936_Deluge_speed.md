---
title: "Deluge speed"
date: 2009-10-09
forum: General Help
---

### Post by TDKING on 2009-10-09
Is there a way to increase upload and download speeds in deluge ?

---

### Post by wojox on 2009-10-09
Preferences > Bandwidth

---

### Post by prem1er on 2009-10-09
Not trying to jack this thread (I'm not at an ubuntu machine). What settings can be adjusted in 'bandwidth'?

---

### Post by TDKING on 2009-10-09
thanks could you tell me whic i needto alter most of them are set to unlimated

---

### Post by jeremyswalker on 2009-10-09
> What settings can be adjusted in 'bandwidth'?
Max connections, max upload slots, max down speed, max up speed, max half-open connections, max connection attempts per second, ignore local network limits, rate limit IP overhead.

---

### Post by prem1er on 2009-10-09
Is your port forwarded correctly? Do you have a firewall up? Are you connectable to other peers who you are sharing with?

---

### Post by wojox on 2009-10-09
[IMG]http://ubuntuforums.org/picture.php?albumid=1409&pictureid=4935[/IMG]

---

### Post by prem1er on 2009-10-09
> **jeremyswalker said:**
> Max connections, max upload slots, max down speed, max up speed, max half-open connections, max connection attempts per second, ignore local network limits, rate limit IP overhead.

Thank you.

---

### Post by kiridude on 2009-10-09
> **TDKING said:**
> thanks could you tell me whic i needto alter most of them are set to unlimated

Whatever's on -1 (unlimited) is already set to maximum. If you're speeds are slow, it's probably due the uploading capacity of your peers.

---

### Post by wojox on 2009-10-09
> **TDKING said:**
> thanks could you tell me whic i needto alter most of them are set to unlimated

See this nice HowTo:

[http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by jeremyswalker on 2009-10-09
> **TDKING said:**
> thanks could you tell me whic i needto alter most of them are set to unlimated

I would alter the upload settings a little. This is especially true if you plan to use the Internet connection for other things while you are running Deluge. In my experience, to high of an upload speed can interfere with web browsing.

---

### Post by jeremyswalker on 2009-10-09
> **wojox said:**
> See this nice HowTo:

[http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

Excellent link! I'd never read that before.

---

### Post by lovinglinux on 2009-10-09
> **jeremyswalker said:**
> Excellent link! I'd never read that before.

Thank you and thanks to wojox for posting the link. Please help to spread it.

---

