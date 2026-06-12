---
title: "X11 launches automatically, when ssh into Ubuntu from Mac OS X"
date: 2010-12-08
forum: General Help
---

### Post by dniq on 2010-12-08
When I ssh into my Ubuntu VM from Mac OS X as myself - everything is fine, but as soon as I sudo to root ("sudo su -", for example - Xwin app launches on my Mac. Xwin on the Mac OS X launches automagically, when there's X11 communication begins via the SSH connection. So the question is: what exactly in Ubuntu tries to start X11 communications, when I sudo into root??? I checked /etc/bash.bashrc, /etc/profile, /etc/profile.d, /root/.bashrc and /root/.profile - couldn't find anything there. As a matter of fact, I tried to remove all of these files, without any success: I still get Xwin launched on my Mac, which means something is still trying to communicate to the Xwin.

Any ideas?

Correction: only happens with "su". Simple "sudo vi" is not causing that behavior. So apparently something is up with bash session. Bash is trying to do something with the Xwin???

---

### Post by tredegar on 2010-12-08
Not sure why this is happening when you su to root, but you could try connecting with X11 forwarding disabled **ssh -x *user@hostname*** if it is annoying you.

It would be interesting to create another user, and see if you still see  this behaviour if you su to them, rather than root.

Edit:
See this, from **man ssh**
```
X11 FORWARDING
     If the **ForwardX11** variable is set to “yes” (or see the description of the -X, -x, and -Y options above) and the user is using X11 (the DISPLAY environment variable is set), the connec&#8208;
     tion to the X11 display is automatically forwarded to the remote side in such a way that any X11 programs started from the shell (or command) will go through the encrypted channel, and
     the connection to the real X server will be made from the local machine.  The user should not manually set DISPLAY.  Forwarding of X11 connections can be configured on the command line
     or in configuration files.

     The DISPLAY value set by ssh will point to the server machine, but with a display number greater than zero.  This is normal, and happens because ssh creates a “proxy” X server on the
     server machine for forwarding the connections over the encrypted channel.

     ssh will also automatically set up Xauthority data on the server machine.  For this purpose, it will generate a random authorization cookie, store it in Xauthority on the server, and
     verify that any forwarded connections carry this cookie and replace it by the real cookie when the connection is opened.  The real authentication cookie is never sent to the server
     machine (and no cookies are sent in the plain).

     If the **ForwardAgent** variable is set to “yes” (or see the description of the -A and -a options above) and the user is using an authentication agent, the connection to the agent is auto&#8208;
     matically forwarded to the remote side.

```
/Edit.

---

