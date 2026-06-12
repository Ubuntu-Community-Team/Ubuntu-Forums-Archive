---
title: "Problem with VNC - xdisplay"
date: 2009-07-12
forum: General Help
---

### Post by avb09 on 2009-07-12
hello
today i have reistalled UBUNTU on my VPS. I have got problem with x11vnc. I've installed it:
```
sudo apt-get install x11vnc vnc-java
x11vnc -storepasswd
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
```

after "x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800" there appeart sth like this:
```

root@avb09:~# x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
12/07/2009 13:55:16 passing arg to libvncserver: -httpport
12/07/2009 13:55:16 passing arg to libvncserver: 5800
12/07/2009 13:55:16 -usepw: found /root/.vnc/passwd
12/07/2009 13:55:16 x11vnc version: 0.9.3 lastmod: 2007-09-30
12/07/2009 13:55:16
12/07/2009 13:55:16 *** XOpenDisplay failed. No -display or DISPLAY.
12/07/2009 13:55:16 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
12/07/2009 13:55:16 *** 1 2 3 4
12/07/2009 13:55:20

12/07/2009 13:55:20 ***************************************
12/07/2009 13:55:20 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

 * An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the
   recent -create option if that is what you really want).

 * You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

 * Next, you need to have sufficient permissions (Xauthority)
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicity indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

 - If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Only root will have read permission for the file, and so x11vnc must be run
   as root.  The random characters in the filenames will of course change,
   and the directory the cookie file resides in may also be system dependent.
   Sometimes the command "ps wwwaux | grep auth" can reveal the file location.

See also: http://www.karlrunge.com/x11vnc/#faq

```
THere is problem with XDISPLAY. I dont know what is this and how to enable it...

I have got an access ONLY via SSH. Porty 5800-5900 are unlocked, 'cause before it worked well... 
I connect from my windows client VNCviewer. There appears an error "Connection refused 10061".

Please, help me

Regards

---

### Post by avb09 on 2009-07-12
could You?

---

### Post by krunge on 2009-07-12
An X display is what one gets when one logs into an X session (i.e. the Desktop). You can think of an X display as a monitor+keyboard+mouse unit. 

Usually a computer only has one X session at a time and the DISPLAY is ":0.0". In that case the $DISPLAY environment variable would be ":0.0" to indicate which display for applications to display on.

x11vnc needs to **attach to an existing** X display. E.g. "x11vnc -display :0.0 ...".

It doesn't look like you have any X displays running on that machine and so x11vnc has nothing to attach to.

There is a mode (x11vnc -create ...; see the x11vnc documentation) that creates a virtual (RAM-only) X display by running Xvfb.  But it is not clear to me this is what you want to do.  What do you want to achieve, BTW?

---

