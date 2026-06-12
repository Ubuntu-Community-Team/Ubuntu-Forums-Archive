---
title: "Running LXDE session over VNC"
date: 2009-09-29
forum: General Help
---

### Post by IanB2 on 2009-09-29
I've installed the LXDE desktop and have it running on my main desktop machine.

I'd like to be able to connect remotely to the desktop machine via VNC and have not managed to find any xstartup configuration files during my 'googling' that I can place in the ~/.vnc folder

I've tried a number of different commands to try and start the lxde session by hacking the xstartup file used to launch a gnome session - with no success so far.

Has anyone managed to do this?

---

### Post by sedawk on 2009-09-29
Instead of creating a new Desktop that runs LXDE you can
also connect to the existing desktop using tool "x11vnc".

Configuring a second virtual Desktop to run with the
same setup as the local one is not always easy, as
there is so much background stuff running nowadays.
E.g. the default startup on a secondary (virtual) desktop
might report lots of errors and warnings (sound not working,
3D extension not working, etc, etc, etc.).

I find it easier to start with a mini-setup on the virtual
desktop (e.g. a simple window manager and an xterm) and
then to start other tools and see what happens (like
gnome-panel, etc.).

---

### Post by IanB2 on 2009-09-29
> **sedawk said:**
> Instead of creating a new Desktop that runs LXDE you can
also connect to the existing desktop using tool "x11vnc".

Configuring a second virtual Desktop to run with the
same setup as the local one is not always easy, as
there is so much background stuff running nowadays.
E.g. the default startup on a secondary (virtual) desktop
might report lots of errors and warnings (sound not working,
3D extension not working, etc, etc, etc.).

I find it easier to start with a mini-setup on the virtual
desktop (e.g. a simple window manager and an xterm) and
then to start other tools and see what happens (like
gnome-panel, etc.).

Thanks ..... I've been trying this out but am struggling to find a simple 'how to x11vnc'. Can you recommend a good site?

---

### Post by sedawk on 2009-09-30
As far as I can remember I simply start x11vnc
and have a look at the error messages.
If I remember right with Ubuntu there are two things
to do:

1) create a vnc password with vncpasswd (and if x11vnc doesn't
   use a default file provide the location via command line
   switch

2) x11vnc needs to know your xauth file. On Ubuntu this is
   /tmp/.gdm* I think ...

Now x11vnc should start properly and you can access
the desktop from a remote PC with a vnc client.

---

