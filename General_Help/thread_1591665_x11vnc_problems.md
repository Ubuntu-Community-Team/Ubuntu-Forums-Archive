---
title: "x11vnc problems"
date: 2010-10-09
forum: General Help
---

### Post by Camis on 2010-10-09
Hello all.  I recently got an older box on which I installed Ubuntu 10.04.1.  I setup ssh on it, and put it in my office.  It's currently headless, with no screen, keyboard, or mouse attached...I just ssh into it.  I'd love to setup vnc on it so I can have access to the gui as well, but I'm having a lot of problems doing so.

I'm trying to use x11vnc...it seemed like it was the best one.  Here is how I want the process to work:

1.  I ssh into my server and run a script that starts up x11vnc.
2.  I launch a vnc client on my laptop and the login screen of my server pops up.
3.  I click on my username and enter my password, then am redirected to my desktop.

The script I'm using to startup x11vnc looks like this:

```
#!/bin/sh
echo "JOB RUN AT $(date)"
echo "============================"
echo ""
x11vnc -bg -forever -auth -auth /root/.Xauthority -usepw -o /var/log/x11vnc.log -httpport 5800 -xkb

```

Then when I check the log, this is the error message I'm getting:
```
root@ubuntu-server:/var/log# cat x11vnc.log 
09/10/2010 13:17:37 passing arg to libvncserver: /root/.Xauthority
09/10/2010 13:17:37 passing arg to libvncserver: -httpport
09/10/2010 13:17:37 passing arg to libvncserver: 5800
09/10/2010 13:17:37 -usepw: found /home/corey/.vnc/passwd
09/10/2010 13:17:37 x11vnc version: 0.9.12 lastmod: 2010-09-09  pid: 17060
09/10/2010 13:17:37 XOpenDisplay("") failed.
09/10/2010 13:17:37 Trying again with XAUTHLOCALHOSTNAME=localhost ...
09/10/2010 13:17:37 
09/10/2010 13:17:37 *** XOpenDisplay failed. No -display or DISPLAY.
09/10/2010 13:17:37 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
09/10/2010 13:17:37 *** 1 2 3 4 
09/10/2010 13:17:41 XOpenDisplay(":0") failed.
09/10/2010 13:17:41 Trying again with XAUTHLOCALHOSTNAME=localhost ...
09/10/2010 13:17:41 XOpenDisplay(":0") failed.
09/10/2010 13:17:41 Trying again with unset XAUTHLOCALHOSTNAME ...
09/10/2010 13:17:41 

09/10/2010 13:17:41 ***************************************
09/10/2010 13:17:41 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

```

Can you guys help me out with this?  I'd really appreciate it!

---

### Post by krunge on 2010-10-09
Is there an X server even running on the hardware at the time you start x11vnc?  As the x11vnc output messages describe, there needs to an existing X server for x11vnc to attach to.

If you just want a virtual desktop access, why not use "vncserver" or something similar? (BTW x11vnc can emulate "vncserver" if you install the xvfb package and add -create to the x11vnc cmdline.)

---

### Post by Camis on 2010-10-09
I don't think there is an X server running.  There are no users logged into the machine.  Just the initial login page should be up and running on it.  But I believe it's possible to have the Ubuntu login page displayed using x11vnc...then I could click the username I want and enter the password.

Like you said, I tried installing the xvfb package and adding -create to the x11vnc command, but it just brought me to a command prompt.  I want the actual graphical display showing.

How can I get an X server running on my machine?  It would probably have to be running on boot for x11vnc to connect I guess...

---

### Post by krunge on 2010-10-10
> **Camis said:**
> I don't think there is an X server running.  There are no users logged into the machine.  Just the initial login page should be up and running on it.  But I believe it's possible to have the Ubuntu login page displayed using x11vnc...then I could click the username I want and enter the password.

To show the login greeter, see the section marked 'Continuously' here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

> 
Like you said, I tried installing the xvfb package and adding -create to the x11vnc command, but it just brought me to a command prompt.  I want the actual graphical display showing.

Hmmmm, that doesn't sound right.  I don't think you understand how it would work.

---

### Post by Camis on 2010-10-14
Thanks guys.  I ended up installing NoMachine's NX software.  It was much simpler to install, it worked well, they had a client that worked with my OS X laptop, and it was super fast!  It is definitely faster than X forwarding or VNC.  I was impressed and very happy with it.  But thanks again for your help.

---

### Post by tehowe on 2010-10-27
> **krunge said:**
> To show the login greeter, see the section marked 'Continuously' here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

Thanks for posting this...! I think you just solved a problem I've been seeing too.

When I login in from work via Putty to use liferea, at least once a day I experience a system freezup when I hit enter to pass a URL to Firefox - the system spawns a seemingly inexhaustible supply of firefox-bin (according to *top*).

Sometimes *killall firefox-bin* works, but not always, so being able to *shutdown -r now* and have x11vnc load up all by itself while I wait patiently to ssh back in would be perfect.

Will let the thread know.

PS I've a recent copy of x11vnc so key autorepeats are already disabled. It seems to be a latency issue.

---

### Post by tehowe on 2010-10-27
(duplicate post deleted)

---

### Post by tehowe on 2010-10-28
> **tehowe said:**
> Thanks for posting this...! I think you just solved a problem I've been seeing too.

When I login in from work via Putty to use liferea, at least once a day I experience a system freezup when I hit enter to pass a URL to Firefox - the system spawns a seemingly inexhaustible supply of firefox-bin (according to *top*).

Sometimes *killall firefox-bin* works, but not always, so being able to *shutdown -r now* and have x11vnc load up all by itself while I wait patiently to ssh back in would be perfect.

Will let the thread know.

PS I've a recent copy of x11vnc so key autorepeats are already disabled. It seems to be a latency issue.

:( Hmmmn... Well I added ...

```
/usr/local/bin/x11vnc -auth guess -xkb -ncache 10 -safer -localhost -nopw -once -display :0
```... to */etc/gdm/Init/Default*, right before the line that says exit 0 ...

(That's the command line I would normally just type in by executing *!x11* via an ssh connection in PuTTY, with the addition of the */etc/gdm/Init* path and the *-auth* guess)

... and tried to ssh in from a machine hooked up to the same router, which has been tested prior. No go, refused connection.

Okay, well maybe the ssh server hasn't been executed yet. To test that theory, I wheeled back over to the Unix box and logged in manually, then was able to ssh in from the other machine. Now, instead of typing *!x11* in PuTTY, I just ran vncviewer, reasoning that if the efforts above successfully ran *x11vnc* when the gnome display manager ran, then I shouldn't have to, right?

Sadly, vncviewer wasn't able to connect. I switched -once to -forever and that didn't work either.

Where do I go from here? Thanks... :confused:

---

