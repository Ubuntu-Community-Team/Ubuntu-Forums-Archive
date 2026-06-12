---
title: "Launch GUI Applications Remotely On Host"
date: 2010-05-11
forum: General Help
---

### Post by dillzz on 2010-05-11
I recently acquired an android device and would like to be able to ssh into my machine and launch certain X applications ( Amarok, other video players)  
This works well when I launch server tasks that don't require an interface, however when trying to launch Amarok on the host from a remote session, I get an error about DBUS and display obviously.  Just to clarify, I do not want them to launch on the phone itself but on the host, If I start them manually while at the host II can then control them remotely fine once they are started. . . 

Thoughts?

---

### Post by quadproc on 2010-05-11
> **dillzz said:**
> I recently acquired an android device and would like to be able to ssh into my machine and launch certain X applications ( Amarok, other video players)  


I think that you are looking for the X windows display capability.  To use it from bash, do export DISPLAY=stationname:0 where stationname is the name of the system where you want the display to occur.

quadproc

---

### Post by dillzz on 2010-05-12
I have tried that, no go...

---

### Post by sedawk on 2010-05-12
When logged in remotely try something like this:
```

export DISPLAY=:0
xterm

```
Assuming xterm is installed an xterm should open on the
desktop.

Normally X does not allow tcp/ip connections with default
settings, therefore "DISPLAY=localhost:0.0" will not
work.
You must login as the same user that is running the desktop,
otherwise you have to change access rights to the desktop.
(see "man xauth" or examples on the web).


What I normally do is this:
On the "server" I start a second desktop with VNC, e.g.
"vncserver -geometry 1280x1024 :1"
I can use a viewer like vinagre to see that new desktop.
When I desperately need to access that desktop from
remote I can do this with ssh, an ssh-tunnel inside
the ssh-session, and a local VNC viewer.
E.g. I run the ssh-session with
```

ssh -L 3333:localhost:5901 myself@myserver.net

```
5901 is the VNC-port of display ":1" on the server.
The string "localhost" refers to the machine to talk
to from the server-side of the ssh-session. We want
to talk to the server itself, so "localhost".
3333 is the local port on my local client.

When starting a local vnc client I will tell it to talk
(locally) to port 3333. The traffic to 3333 will travel via the
running ssh-session to my server and from there
to port 5901 of localhost.

This desktop should stay up and running even if you
logout from the "real" :0 desktop on the server or someone
else logs in and uses the "real" desktop.

---

### Post by dillzz on 2010-05-12
sedawk,

Thank you for the detailed post.  Two things, I can't enable tcp/ip on X for security reasons, and I want to run this within the current desktop and not have to start a VNC session.  Picture the scenario, someone calls and says this isn't working, or I don't know how to launch this.  I can simply click and bam.  Like I mentioned prior this is what is being done with server tasks which is great.  

Thanks,

-Dillzz

---

### Post by x-shaney-x on 2010-05-12
ssh -X  ??

<EDIT>
Nevermind, misread slightly.

---

### Post by sedawk on 2010-05-12
The short export "export DISPLAY=:0" should do the trick.

Only the longer versions "export DISPLAY=hostname:0.0" or
"export DISPLAY=localhost:0" or ... need tcp/ip.

Have you tried the short export?

---

### Post by dillzz on 2010-05-13
*Smacking head.

Sedawk, worked like a charm!  A million thannks!

-Doran

---

