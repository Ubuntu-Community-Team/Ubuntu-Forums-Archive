---
title: "X Server running only an NX client"
date: 2010-06-08
forum: General Help
---

### Post by unperson on 2010-06-08
I've been using NX to login to a remote machine (using the free NoMachine NX client).  I've been pretty happy with it, but I'd like the ability to run it as a separate desktop, rather than a window within my existing local desktop.  I think I'd like to be able to start X Windows with only the NX client running, either in another virtual console (VC) in addition to my local desktop or perhaps sometimes as the only desktop running.  

My first thought was to go to another VC and start an empty X Server with only the NX client running with the command ```
xinit /path/to/nxclient -- :1
```  That seemed to work, except that just as the remote desktop is about to appear the X server shuts down.  It seems that the nxclient process spawns the child nxssh and then exits, and at that point X Windows closes because the command it was started with has ended.  I assume there's a simple way to fix this by writing a script that will only terminate once all the child processes have terminated and calling that on the xinit command line, but I'm not sure how to do that.

Hopefully someone out there understands a little more about these things and can point me in the right direction.

---

### Post by davidmohammed on 2010-06-08
don't know - and sounds intriguing - but probably and obvious question - why not just start NXClient is another workspace.  You can then have one workspace for ubuntu and another for your remote client.

---

### Post by unperson on 2010-06-08
I had been running NX client in a maximized window on one of my 4 workspaces.  This is an okay setup, but running it in a different X Server would more effectively separate it from the other work I have spread across the various workspaces (mostly because a different key combo would be needed to switch) and allow me to use a full screen view (although I might be able to do that with my current setup if I learn appropriate NX client escape keys to get out of the full screen).  However, the main reason is so I have the option of running only the NX client and none of the rest of the desktop.  One of the "local" machines in question may end up being transitioned to serving as a thin client most of the time with only occasional use of the local desktop.

---

### Post by davidmohammed on 2010-06-09
If you want a dedicated thin-client connecting to your NX server, I think you probably want to use something like thinstation.

---

### Post by unperson on 2010-06-09
davidmohammed:  Thinstation is definitely interesting as a dedicated thinclient, but as I said in my original post my goal is to have the option at any time to start a local desktop only, a remote desktop only, or both simultaneously.  

Using xinit works if I start it with an xterm and invoke nxagent from there.  I was just hoping to eliminate the extraneous steps of calling the program from the xterm and shutting down the xterm once I'm done.

---

### Post by davidmohammed on 2010-06-09
ok - this [how to]("http://ubuntuforums.org/showthread.php?t=1265398") sounds promising...

---

### Post by unperson on 2010-06-09
Thanks, that does look helpful.  That link was talking about logging in via a display manager like GDM. I was wondering whether it's possible for the same user to log into a second session while the first one is still running (to be able to run both desktops simultaneously), but it appears the answer is yes: [http://ubuntuforums.org/showthread.php?t=504995]("http://ubuntuforums.org/showthread.php?t=504995")

---

