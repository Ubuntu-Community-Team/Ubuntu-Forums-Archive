---
title: "X11 Forwarding, Fluxbox, problems"
date: 2009-09-28
forum: General Help
---

### Post by deranjer on 2009-09-28
I have a server running debian, and it was by default using gnome.  I usually manage the server remotely, and run apps from that server remotely, so I set up X11 forwarding over SSH.  However, I wanted a lightweight GUI so that I could save some processor and RAM load from using gnome. X11 was working fine with GNOME, so I installed fluxbox and flushed GNOME.  However, now when I try to use X11 forwarding nothing appears.  If i run "xclock &" it shows the PID that it started but nothing appears.  If I run "xclock" it goes to the next line, and nothing happens."#echo $DISPLAY" gives "localhost:10.0" which is exactly what it showed for gnome. My sshd_config file shows X11 forwarding is enabled.  I dont think anything else has changed... what can I do to get this working?

---

