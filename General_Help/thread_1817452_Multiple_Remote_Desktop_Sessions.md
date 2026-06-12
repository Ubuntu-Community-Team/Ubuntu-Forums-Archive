---
title: "Multiple Remote Desktop Sessions"
date: 2011-08-03
forum: General Help
---

### Post by RatTub on 2011-08-03
Is it possible to start a second remote desktop session from a windows machine?

I currently have a machine at home with 2 users. A gnome session starts for *user1 *automatically on boot. I can then use an ssh tunnel to connect remotely with the RealVNC viewer. This connects to the same *user1* session.

What I'd like to do is start a second session for *user2* so that I can connect to it instead of the *user1* session.

How can I do that?

If possible, I'd like to keep using the built-in Remote Desktop feature in Ubuntu, and not x11vnc.

---

### Post by RatTub on 2011-08-03
I should've mentioned: I'm using Maverick

---

### Post by philryan on 2011-09-12
1. Start Cygwin/X by running

$ startxwin

on the Cygwin command prompt.

2. From within the xterm, run ssh

$ ssh -Y <username>@<servername-or-server-ip-address>

give your password when prompted.

3. From within the xterm that starts up when cygwinx is started, start up a gnome desktop session, e.g.

$ gnome-session &

And you should have a second X-windows GUI to your Linux box, now running as an Xwindows client on your MS-Windows PC.

---

