---
title: "start x session from terminal?"
date: 2009-12-25
forum: General Help
---

### Post by becarexinxin on 2009-12-25
hi all,

I logged in to my Ubuntu server at work through putty from home, and the welcome message suggested me to do a restart,  so I did "sudo reboot". But then  I was unable to view the ubuntu desktop using vncviewer,  I think it's because I didn't do a X session log in.  How could I do a X session login from the terminal of putty? Thanks for help~

---

### Post by MaxIBoy on 2009-12-25
For Ubuntu 9.04 and earlier, it's ```
sudo /etc/init.d/gdm start
``` For Ubuntu 9.10 and on, it's ```
sudo service gdm start
``` For Xubuntu I think it's the same. For Kubuntu use "kdm" instead of "gdm." I think you might actually have to be on-site to type in your password and stuff, but that's probably not the case.

You can also install Xming on your windows box, so you forward X11 over SSH and have the X server running locally. This is a lot easier on the bandwidth than VNC, and it uses SSH for encryption so it's still secure, but your themes don't apply properly. Just run Xming on your windows box, then in the menus of Putty do this:

---

### Post by becarexinxin on 2009-12-25
Thanks for the reply~

I am using Ubuntu 9.10, so I tried  "sudo service gdm start" , the terminal replied "start: Job is already running: gdm".   But I just couldn't connect to the machine using vncviewer...

I am in winXP now, so I couldn't use x11 forwarding...   :(




> **MaxIBoy said:**
> For Ubuntu 9.04 and earlier, it's ```
sudo /etc/init.d/gdm start
``` For Ubuntu 9.10 and on, it's ```
sudo service gdm start
``` For Xubuntu I think it's the same. For Kubuntu use "kdm" instead of "gdm." I think you might actually have to be on-site to type in your password and stuff, but that's probably not the case.

You can also install Xming on your windows box, so you forward X11 over SSH and have the X server running locally. This is a lot easier on the bandwidth than VNC, and it uses SSH for encryption so it's still secure, but your themes don't apply properly. Just run Xming on your windows box, then in the menus of Putty do this:

---

### Post by MaxIBoy on 2009-12-25
Sorry, I should have been more specific. [Xming]("http://sourceforge.net/projects/xming/") is an X server for Windows. You just need to make sure it's running on your Windows box. (I like to hide the root window, which is like VBox's "seamless mode.") Then, connect with Putty and enable X11 forwarding. I like to run a mini xfce4-panel in the corner with autohide enabled (see screenshot.)

Also try "sudo service gdm restart," or "sudo service gdm stop" and then "start."

---

### Post by becarexinxin on 2009-12-25
_Thanks so much, MaxIBoy!_

Being able to do x11 forwarding without cygwin in windows is really great, I just learnt!!

However my configuration must still have something wrong there,  when I did "sudo service gdm restart", it complained "sudo: unable to resolve host labl; gdm start/running, process 2264", and when I tried to open a pdf file using "gnome-open abc.pdf", it does open the file but left lots of warnings: 

 Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".

** (evince:2373): WARNING **: Error connecting to D-Bus: /bin/dbus-launch terminated abnormally without any error message

** (evince:2373): WARNING **: Service registration failed.

** (evince:2373): WARNING **: /bin/dbus-launch terminated abnormally without any error message
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally without any error message)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally without any error message)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: /bin/dbus-launch terminated abnormally without any error message)


Weird.... 







> **MaxIBoy said:**
> Sorry, I should have been more specific. [Xming]("http://sourceforge.net/projects/xming/") is an X server for Windows. You just need to make sure it's running on your Windows box. (I like to hide the root window, which is like VBox's "seamless mode.") Then, connect with Putty and enable X11 forwarding. I like to run a mini xfce4-panel in the corner with autohide enabled (see screenshot.)

Also try "sudo service gdm restart," or "sudo service gdm stop" and then "start."

---

### Post by MaxIBoy on 2009-12-25
Huh, maybe GDM only works if you're "on-site." My server doesn't have GDM installed, don't have a good way to test it. Sorry. Are you doing this at work at the moment?

Still, you can get Xming to work without having an X server even installed on the remote computer, let alone running at the time. (although due to dependencies this configuration is unlikely.) This is because Xming is itself an X server. That ought to be a suitable substitute for the time being, until you can get to work or until someone else posts who can help you get your x server started.



Try this. Make sure gdm is still running, then run "gnome-session --display=:0.0" or something like that. If that doesn't work, I'm stumped. But you can probably get by with Xming until someone else comes by who has more expertise...

---

### Post by falconindy on 2009-12-25
You'll need to setup an .xinitrc file in your home directory with 'exec gnome-session' in it. Then use 'startx' to start the X server.

---

### Post by becarexinxin on 2009-12-25
To MaxIBoy:  thanks so much for all your suggestions.  I am OK with the system now using Xming, it displays warnings but it works fine~


To Falconindy:  I followed your suggestion but got something like: 
" 
hostname: Unknown host
xauth: (argv):1:  bad display name "labl:0" in "list" command
xauth: (stdin):1:  bad display name "labl:0" in "add" command

X: user not authorized to run the X server, aborting.
"

I am not sure whether this has anything to do with I changed the name of the computer once.  I hope everything will be resolved after next time I go to office and log into the computer...  Thanks for the suggestion though. 

 

> **falconindy said:**
> You'll need to setup an .xinitrc file in your home directory with 'exec gnome-session' in it. Then use 'startx' to start the X server.

---

### Post by MaxIBoy on 2009-12-25
I think it probably has something to do with the MIT-Magic-Cookie-1 or .Xauthority, but I'm not an expert on those so I can't be entirely sure how to resolve it. 

Try the command ```
xhost +
``` on the server. That should you to access an existing X server remotely (and I'm pretty sure you have one,) but I also think it might be bad for security in some way, not quite sure.
[http://www.xfree86.org/current/xhost.1.html](http://www.xfree86.org/current/xhost.1.html)

---

