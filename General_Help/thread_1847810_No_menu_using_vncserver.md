---
title: "No menu using vncserver"
date: 2011-09-21
forum: General Help
---

### Post by AlexBooton on 2011-09-21
Hi,

New 11.04 installation. I installed vncserver and when I connect from a remote PC I get an all grey screen but with a console window.

The console appears to be fully functional.

But there is no menu; status bar or anything else.  Worse, if I type a "d" the console window closes!  There doesn't seem to be any way to get the normal ubuntu screen.

I've tried tightvnc server; uninstalled it and installed vnc4server.  Both have exactly the same problem.

What am I doing wrong?

BTW, which is the preferred vncserver?

Thanks

---

### Post by AlexBooton on 2011-10-10
Hi,  I posted this message a couple of weeks ago but never got an answer.

I'm still having the same problem.  vncserver shows me only a grey window with a terminal.  Nothing else.  No menu.  So I can't do very much.

I did find the solution to the "d" key closing the terminal window.  The "d" key by itself is a shortcut.  How unfortunate!

I've now tried editing ~/.vnc/xstartup to comment out the first two lines as suggested on-line and in the file itself. 

That made matters worse!  I gives an empty screen with a big "X" for the cursor.  I've reversed that trial.

So how do I get vncserver to work.

This is U11.04 and tightvnc.  I get the same result with vnc4server.

Thanks in advance.

---

### Post by robvas on 2011-10-10
You have to tell VNC to launch GNOME or whatever you want for your desktop. Read this link for instructions:

[https://help.ubuntu.com/community/VNC/Servers#Customising_your_session](https://help.ubuntu.com/community/VNC/Servers#Customising_your_session)

---

### Post by AlexBooton on 2011-10-11
Thanks!

Works great!

---

### Post by lotsofish on 2011-10-15
I've followed the instructions on "Customizing your session" page for tightvncserver, but I am getting the following error when trying to view 'Could not acquire name on session bus'

Any ideas? I'd like to get this working again. (It hasn't worked for me  since upgrading to 11.10.)

---

### Post by mathuin on 2011-10-17
> **robvas said:**
> You have to tell VNC to launch GNOME or whatever you want for your desktop. Read this link for instructions:

[https://help.ubuntu.com/community/VNC/Servers#Customising_your_session](https://help.ubuntu.com/community/VNC/Servers#Customising_your_session)

I was bit by this when I upgraded to oneiric.  It "just worked" in previous versions and suddenly stopped working on this one.  Unfortunately, using the xstartup supplied by this link did not work as expected for me.

I started vncserver and moments later I got a malloc() memory corruption in vino-server.  I can save the output via typescript if it'll do any good.

I'm running oneiric on an x86_64 system, if that helps.

Jack.

---

### Post by Dexx4d on 2011-10-19
I'm having the same problem and it started after my upgrade to 11.10.  Using TightVNC viewer on Windows 7 to connect to TightVNC 1.3.9 on Ubuntu 11.10.

I've tried the xstartup linked above, with the same results.
Here's my current xstartup, with a few things I've tried:

:~/.vnc$ cat xstartup
#!/bin/bash

# gnome-session &
# gnome-shell &
# unity &
startkde &

I've also tried re-installing the vnc server and connecting with a different client.  So far, nothing works.

---

### Post by Nexxo on 2011-10-19
Hey guys,

I'm getting the same problem since updating to 11.10.

I have however had some limited success where I do have the menu bar, but it is not as full featured as it use to be (right clicking doesnt work). This is what I did:

I first did a rollback to gnome classic (I got no idea if this did anything, but I have done it)
```
sudo apt-get install gnome-classic-fallback
```I then messed around with the .vnc/xstartup file
```
$ cat .vnc/xstartup 
#!/bin/sh

xrdb $HOME/.Xresources
#xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
## Fix to make GNOME work
#export XKL_XMODMAP_DISABLE=1
#/etc/X11/Xsession

gnome-session-fallback &

```This has got me to a basic vnc page, however I do want it back the old way when I was launching it with /etc/X11/Xsession or something else??

If anyone comes up with anything else, I would love to hear it.

Cheers,

Nexxo

---

### Post by Dexx4d on 2011-10-19
Thanks, that's fixed the grey screen for me.

I added:
gnome-session-fallback &

to the bottom of the xstartup file, restarted vncserver, and I get gnome fallback.

Unfortunately, trying to run anything gives me what sounds like the same error as mathuin above:
*** glibc detected *** /usr/lib/vino/vino-server: malloc(): memory corruption: 0x00000000022cef10 ***

---

