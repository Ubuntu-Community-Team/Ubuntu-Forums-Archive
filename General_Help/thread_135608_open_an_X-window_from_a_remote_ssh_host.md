---
title: "open an X-window from a remote ssh host"
date: 2006-02-24
forum: General Help
---

### Post by lucascr on 2006-02-24
Dear (K)Ubuntu users,

I would like to open an X window from a remote unix host to my linux machine.
In a different linux box, I used to do for example

Linux > xhost +unix.remote.host
Linux > ssh [email]user@unix.remote.host[/email]
Unix  > export DISPLAY=my.ip.address:0.0
Unix  > firefox &

and get the firefox window open on my linux box but running on the remote unix host. 
If I try the above procedure in (K)Ubuntu 5.10 I get the following :( :
firefox: Cannot connect to X server my.ip.address:0.0.

Can you provide some help?

Luca

---

### Post by hw-tph on 2006-02-24
Make sure that a) you have enabled X forwarding in /etc/ssh/sshd_config and b) that you use "ssh -X user@host" when connecting.


Håkan

---

### Post by lucascr on 2006-02-27
I already have X11Forwarding set to yes and using the -X flag. 
Furthermore, I noted that if I set DISPLAY (by default equal to :0.0) to my.IP.address:0.0 I get the same error as I'm using ssh. For example:

> export DISPLAY=141.250.x.xxx:0.0
> nedit
NEdit: Can't open display

There are some tuning parameters to set in X11?
Ciao,

Luca

---

### Post by RAOF on 2006-02-27
If you run "ssh user@remotemachine -X" you shouldn't need to set DISPLAY yourself - ssh does it for you.  You don't even need to do anything to the X server.

---

### Post by lucascr on 2006-02-28
> If you run "ssh user@remotemachine -X" you shouldn't need to set DISPLAY yourself - ssh > does it for you. You don't even need to do anything to the X server.

In principle this is what I expected to see (and this happened with Mandrake, a year ago).
I mentioned the way I set $DISPLAY to point out that even in my linux box I'm not able to send any X-window via IP. I guess there is something to set in the X11.

Luca

---

