---
title: "How to remote into Ubuntu 10.04?"
date: 2011-11-13
forum: General Help
---

### Post by rollin77 on 2011-11-13
I'm having some trouble setting up a PC running Ubuntu 10.04 as a remote desktop, maybe I'm doing things wrong but this simple task seems to be overly complex and currently isn't working.

Right now I have this PC setup to automatically log in without requesting a password.  As far as I know this is required because VNC server doesn't work until after being logged in, (which I have no clue why it is set up this way).

So the problem is that as soon as I initiate a remote session from another PC, (using TightVNC), the remote Ubuntu PC asks for the keyring password.  Because of this, I have to walk over to the PC and enter the password before I can start a remote session.  As soon as I enter the password physically at the remote PC then the remote session begins and I can go back to my room and work on the PC remotely.

It seems like this shouldn't be that difficult of a question, but how the heck do you set up a truly remote PC on Ubuntu 10.04?  The only solution I've read so far requires completely removing the keyring password, but then wouldn't that remove a major security feature?  I still want root privileges password protected, I just need the keyring to stop requesting a password for VNC to work.  I have no clue why this would be a requirement in the first place as it completely breaks the remote process.

Any ideas?  There's got to be at least one person out there that knows how to setup a remote PC on Ubuntu!  Am I going about this the wrong way?

---

### Post by raja.genupula on 2011-11-13
this is a step by step guide

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

### Post by rollin77 on 2011-11-13
That is from 2006 and doesn't even address the problem with the keyring I'm running into.

---

### Post by mendhak on 2011-11-13
The way I've gotten this to work is with x11vnc and SSH.  

First, I edit the network connections and ensure that the checkbox "Available to all users" is checked.

Then I installed SSH and x11vnc.  You'll find plenty of guides on installing SSH, that shouldn't be a problem for you.  

Then, I log out.  From another computer, I ssh to the main computer.  Then,

sudo x11vnc

This starts the x11vnc process, but you'll have to find out what port number it's listening on.  In your SSH setup you'll have to forward a port from localhost:something to maincomputer:X11VNCPort.  I've done this before in Putty, but I don't know how to do this in any other SSH client. 

Finally, remote to it with TightVNC.

---

### Post by rollin77 on 2011-11-18
^^Thanks for the help but this doesn't resolve the keyring password request that is breaking the remote process.
I am able to successfully VNC into this remote pc through an SSH tunnel, HOWEVER, just as before the remote PC asks for a keyring password before allowing the VNC session to begin.

So in other words, remote access doesn't work through VNC because of the keyring problem.  How do I resolve this issue?

---

