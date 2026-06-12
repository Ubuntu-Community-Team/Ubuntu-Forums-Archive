---
title: "How to create a virtual display??"
date: 2010-09-11
forum: General Help
---

### Post by bel3atar on 2010-09-11
Hey, I'm trying to add another virtual display for X (eg. :1) so I can use VNC on it instead of :0
I have x11vnc installed for that.
Need help

---

### Post by krunge on 2010-09-11
> Hey, I'm trying to add another virtual display for X (eg. :1) so I can use VNC on it instead of :0
I have x11vnc installed for that.
You probably want to use the program 'vncserver' instead of 'x11vnc'.

That said, x11vnc can do what you want if you install the package xvfb and then run 'x11vnc -create' and then connect to it with a vncviewer. When you do that it will start the Xvfb X server and your desktop.

---

### Post by bodhi.zazen on 2010-09-11
> **bel3atar said:**
> Hey, I'm trying to add another virtual display for X (eg. :1) so I can use VNC on it instead of :0
I have x11vnc installed for that.
Need help

I agree, it is probably easier to use an alternate VNC server, FreeNX is a nice alternate as well.

To answer your question , see :

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

It is a bit of an old thread, but it still works (you need to edit a configuration file , read past the script).

---

### Post by bel3atar on 2010-09-12
Thanks for your answers but still:

```
~$x11vnc -create
12/09/2010 09:46:02 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 1985
12/09/2010 09:46:02 
12/09/2010 09:46:02 wait_for_client: WAIT:cmd=FINDCREATEDISPLAY-Xvfb
12/09/2010 09:46:02 
12/09/2010 09:46:02 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
12/09/2010 09:46:02 
12/09/2010 09:46:02 Autoprobing TCP port 
12/09/2010 09:46:02 Autoprobing selected port 5900
12/09/2010 09:46:02 

The VNC desktop is:      pc:0
PORT=5900

```


I've Xvfb installed...

---

### Post by bel3atar on 2010-09-12
I also tried
```
$ sudo startx -- :1
x11vnc -display :1
```
It works, but black screen only

---

### Post by krunge on 2010-09-12
For your 'x11vnc -create' usage, to create a RAM-only virtual framebuffer with Xvfb you next need to connect to x11vnc with a vnc viewer after you have started 'x11vnc -create'.  When you first connect to x11vnc it will start Xvfb for you.

BTW  through a vncviewer will be the only way you ever see what is on Xvfb's screen.

For the physical graphics display on a different Linux VT (virtual terminal) using startx -- :1 you will never be able to see what is on :1 thru x11vnc unless you make that Linux VT with :1 the active VT.  More details here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc](http://www.karlrunge.com/x11vnc/faq.html#faq-linuxvc)[/INDENT]

---

### Post by bel3atar on 2010-09-13
TightVNC does it, thanks anyway :)

---

### Post by krunge on 2010-09-13
> **bel3atar said:**
> TightVNC does it, thanks anyway :)
You mean what I suggested in my first post in this thread? Or something else?

---

### Post by bel3atar on 2010-09-13
actually, x11vnc is for real X servers
while tightvnc can create virtual ones for you

---

### Post by krunge on 2010-09-13
> actually, x11vnc is for real X servers
while tightvnc can create virtual ones for you

For reference to others reading this thread: x11vnc can do both, as I have described above.

Glad you have vncserver/tightvncserver working for your machines.

---

