---
title: "Error running some apps with ssh -X"
date: 2009-10-15
forum: General Help
---

### Post by OBI_Ron on 2009-10-15
Hello Everyone,

I have posted this same question on the Blender forums.
Running Ubuntu 8.04 on one machine, and 9.04 on the other.  I have ssh client and server installed and both machines configured to allow X forwarding.  I also have xauth installed.

When I login from 8.04 to 9.04 using ssh -X, I can start some apps such as gedit for example without any problem.  However, if I try to run Blender, I get the following:

```
X Error of failed request: BadWindow (invalid Window parameter)
Major opcode of failed request: 18 (X_ChangeProperty)
Resource id in failed request: 0xb76bdc34
Serial number of failed request: 30
Current serial number in output stream: 31

```

Without the -X option I get:

```
Compiled with Python version 2.5.4.
Checking for installed Python... got it!
ERROR: Unable to open Blender window

```

Can anyone help me find a way to run Blender remotely?

Thanks in advance!

---

### Post by P4man on 2009-10-16
Id be amazed if it would work.. with graphics applications run remotely, the X server rendering the applications is your local X server. Im guessing you're using SSH to make use of a fast videocard on the remote machine? Well, no such luck. Moreover, the OpenGL application cannot access to the hardware directly and so you'll get messages like "Unable to create direct context rendering".   You can use VNC but it will probably be painfully slow.

---

### Post by OBI_Ron on 2009-10-16
P4man,

Thanks for the reply!  Slow is ok in this case.  The reason I want to run it remotely is just to kick off Blender and run a script to listen for Farmer Joe network renderer.  I can just as easily reach across the home office and log in, but I wanted to be able to remotely run it so my wife could be logged in and working on the pc.

I will look in to vnc.

Thanks again!

---

### Post by XCan on 2009-10-16
Is there some special opengl apps that don't work? I can, for example, run glxgears over ssh -XC with good speed.

---

### Post by OBI_Ron on 2009-10-16
XCan,

Thanks!  I had not tried the -C option.  I will give that a go as well when I get home tonight.

---

### Post by XCan on 2009-10-16
Unfortunately the -C option only enables compression, which I use to not saturate my BW for graphical-intensive apps, it will most likely not help you getting your app to run. Sorry for the confusion.

---

### Post by dretep on 2010-02-20
Old thread but I'm having similar issues with gedit and think I found the cause but not a solution: [https://bugzilla.redhat.com/show_bug.cgi?id=209452](https://bugzilla.redhat.com/show_bug.cgi?id=209452)

If gedit is running on my Ubuntu desktop at work and I try and run gedit at home if fails. If gedit isn't running I can start it from home. 

Might have been a similar issue with Blender?

---

