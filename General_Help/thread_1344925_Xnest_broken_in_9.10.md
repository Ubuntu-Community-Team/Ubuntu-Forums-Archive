---
title: "Xnest broken in 9.10?"
date: 2009-12-03
forum: General Help
---

### Post by sderrick on 2009-12-03
Ubuntu 9.10 X86 AMD64

I have a LTSP server I want to connect to using Xnest or some other X in a window client. 

I can connect to the server using ssh, fine.. 

When I try using Xnest I get a black Xnest window, thats it.  Xnest reports the following problem. 

scott@scotts-laptop:~$ Xnest :1 -ac -geometry 1024x768 -query 128.123.50.41
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 188 requests (188 known processed) with 0 events remaining.

I get the same error trying to connect to localhost on the server it self.

I have heard about some problems with DBus????

Scott

---

### Post by lxme on 2010-01-22
up

---

### Post by humilleitor on 2010-01-23
I'm in Xubuntu 9.04, xnest 2:1.6.0, xserver-xorg 1:7.4, and I'm experiencing exactly the same thing:
my@user:~$ Xnest :1 -query localhost
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)
(EE) config/hal: NewInputDeviceRequest failed (2)

Then, if I ctrl-C, no more messages. But if I close the opened black dead window that was born to be a gorgeous xnested client, then I get another message in the console:

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 152 requests (152 known processed) with 0 events remaining.

Funny, every time is exactly 152 requests. No more, no less. I wonder why not 43, or 286, or 84698? But, well, the thing is that it doesn't work.

---

### Post by Micha401 on 2010-02-20
Me to!
It seems to me that all remote X progs/variants are very buggy for karmic64.
Hopefully, many problems will be fixed in 10.04.
If someone knows a solution now, please help out.

---

