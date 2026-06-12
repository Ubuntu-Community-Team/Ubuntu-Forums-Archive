---
title: "VNC remote desktop connection over SSH tunnel Problems"
date: 2012-01-01
forum: General Help
---

### Post by esbrinartot on 2012-01-01
I've tied so many time to connect my desktop computer (192.168.1.12) to my laptop (192.168.1.13)

I'm using putty and the default Ubuntu software to do remote connections (Vino)

If I do and standard connection I have no problems. The problems come when I ty to create and SSH Tunnel. The steps I do are next:

In order to stablish connection to 192.168.1.13 (my laptop):
[http://img207.imageshack.us/img207/8199/puttyconfiguration001.png](http://img207.imageshack.us/img207/8199/puttyconfiguration001.png)

To create the ssh tunnel:
[http://img225.imageshack.us/img225/6156/puttyconfiguration002.png](http://img225.imageshack.us/img225/6156/puttyconfiguration002.png)

and finally to stablish connection:
[http://img40.imageshack.us/img40/321/visordeescritoriosremot.png](http://img40.imageshack.us/img40/321/visordeescritoriosremot.png)

But I have next error:
[http://img140.imageshack.us/img140/8179/errormq.png](http://img140.imageshack.us/img140/8179/errormq.png)

Can anyone let me know if I forget some steps? OR if I do something wrong?

thks in advance

---

### Post by Lars Noodén on 2012-01-01
The last image gives the clue.  Try tunneling over port 5902 instead.  That's what your connection is expecting.  Do the rest the same.

---

### Post by esbrinartot on 2012-01-01
> **Lars Noodén said:**
> The last image gives the clue.  Try tunneling over port 5902 instead.  That's what your connection is expecting.  Do the rest the same.

Hi Lars

1st of all thanks to answer.

I'm already tunneling over port 5092

localhost:2 it's equivalent to localhost:5092

I guess you meant what I understood.

The translation of the last message in english is:
conection closed
connection with the computer localhopst::5092 has been closed

---

### Post by Lars Noodén on 2012-01-01
> **esbrinartot said:**
> localhost:2 it's equivalent to localhost:5092


It should be 5902 rather than 5092.

---

### Post by esbrinartot on 2012-01-01
> **Lars Noodén said:**
> It should be 5902 rather than 5092.

Sorry Lars,

I had a mistake typing. I used 5902. I still have the problem

The desktop computer is using Lubuntu 11.10 and know I've just find out that I can't autostart vino-server. To autostart I go to preferences - autostart applications and then I check the box to autostart vino-sever and accept. Onc I go again to preferences - autostart - applications vino-server is uncheked.

It's weird because a few days ago I didn't have this problem. This could be the reason of all my problems.

---

