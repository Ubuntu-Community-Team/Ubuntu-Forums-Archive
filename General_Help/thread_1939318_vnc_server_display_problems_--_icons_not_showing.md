---
title: "vnc server display problems -- icons not showing"
date: 2012-03-11
forum: General Help
---

### Post by spudtater on 2012-03-11
Hi all, I've just installed Ubuntu 11.10 on my desktop machine and am  trying to serve a remote desktop to my netbook. I'm running vnc4server  to serve a new X session on port 5901. (So, X session :1)

The  first problem I had was that nothing loaded at all, except for a desktop  background. So on the advice of a forum post I added an .xsession  configuration file into my home directory with the contents:

```
gnome-session --session=ubuntu-2d
```This  worked -- partially. But the dock icons for my home folder, terminal,  and several others are simply blank. The same holds for a number of  items inside the dash menu; for example if I type in 'gedit' the gedit  icon is missing. And what's more, clicking on it causes a busy icon to  display and the application does not get launched. I can, however,  launch it from a terminal window.

At first I thought that it  might be the client which was to blame... to test this I ran a remote  desktop client from the same desktop box that is running vnc4server, to  minimise questions of compatibility. The exact same issue occurred,  though.

Does anybody know what on earth's going on here? I've  attached a screenshot of the problem, showing the missing icons (compare  to what it should look like, on the left), and also my .xsession-errors  log, if that reveals anything useful.

Your help would be appreciated!

---

