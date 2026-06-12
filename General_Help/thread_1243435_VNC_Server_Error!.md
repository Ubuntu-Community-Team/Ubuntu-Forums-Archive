---
title: "VNC Server Error!"
date: 2009-08-18
forum: General Help
---

### Post by antdgar on 2009-08-18
I have followed the instructions on the ubuntu VNC wiki page.

It says to enter the following command to start VNC Server
```
x11vnc -safer -localhost -nopw -once -display :
```[FONT=Verdana]

I get this response:
```
18/08/2009 16:53:52 -safer mode:
18/08/2009 16:53:52    vnc_connect=0
18/08/2009 16:53:52    accept_remote_cmds=0
18/08/2009 16:53:52    safe_remote_only=1
18/08/2009 16:53:52    launch_gui=0
18/08/2009 16:53:52 x11vnc version: 0.9.3 lastmod: 2007-09-30

18/08/2009 16:53:52 ***************************************
18/08/2009 16:53:52 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.
```**Any ideas how to fix this issue? I really need to connect to my server as NX is not good for my uses.**

[I](there is someone already logged into an NX session on my server, not sure if this is why the error is happening?)
I also skipped this part of the VNC installation because I don't want to use keyfiles, I will use password verification:
> [/I][/FONT]

[LIST=1]
[*][Choose an SSH client]("https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo") for the computer you'll log in from, and create a public key for that computer 
[*]In a text editor on your PC, open the file *<home>*/.ssh/authorized_keys, then add the public key you just created to the bottom of the file
[/LIST]

---

### Post by krunge on 2009-08-18
> **antdgar said:**
> 
```
x11vnc -safer -localhost -nopw -once -display :
```

That's not correct, I'm guessing the display part for you must be:```
-display :0
```

Are you logged into an X session, i.e. session :0,  on the machine you are running x11vnc on?  x11vnc does **not** start an X session for you, it connects to an existing one.  

Read the full description printed after "XOpenDisplay(:0) failed", i.e. 'tips and guidelines', that explains it.

---

