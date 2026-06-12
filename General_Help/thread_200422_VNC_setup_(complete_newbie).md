---
title: "VNC setup (complete newbie)"
date: 2006-06-20
forum: General Help
---

### Post by bedog on 2006-06-20
So, I've installed Linux for the first time in my life, and I've managed to far enough to get mysql, apache and hamachi running on this machine...

Now, I'd like to get a VNC running, that I can control from my windows machine.
I've noticed that vino comes preinstalled, but I cannot find where the conf files are or if it's running.

Anybody out there who can help a total newbie setting this up so that I have a running VNC server (that will start automatically with a reboot) that can be reached with TightVNC (or similar free, opensource program)?

---

### Post by severedspirit on 2006-06-20
VNC should be installed with it, type in 

vncviewer [ip address]

thats it

---

### Post by bedog on 2006-06-20
Hi,

Thanks, but it's not really what I asked for.

I'd like to run a VNC server on my Ubuntu machine, that I can reach from my vncviewer on my windows machine.

---

### Post by severedspirit on 2006-06-20
sorry, didnt understand.

Go To System -> Preferences -> Remote Desktop

then change your settings

---

### Post by bedog on 2006-06-20
thanks!

That did the trick :D

---

### Post by bizitmap on 2006-06-22
This trick helped me too, I wasn't aware that Remote Desktop was in fact vnc. 

However, in use, it's SO slow. I remember working with vnc servers for windows that would let you change the color color settings it pushed out, setting it down to 16bit color or 256 would make the connection go significantly faster.

Any way to do this in Ubuntu? I'm not afraid of poking config files and general command line tomfoolery if need be.

---

### Post by will_in_wi on 2006-06-22
You can set the settings of size, depth color etc.. in the client.

---

### Post by scxtt on 2006-06-22
you can set it for the server as well ... do a "man" for whatever server you're using ...

btw, IMO vino (which is what "remote desktop" is using) isn't a good server ... check out vncserver or x11vnc ...

---

### Post by bizitmap on 2006-06-22
Ha, I'm dumb. Turns out that indeed you do configure the color settings on the client. I assumed you didn't because the client I was using didn't offer that option. I get faster performance even on the highest setting out of VNCViewer for OS X, so STAY AWAY from ChickenOfTheVNC (what I was previously using). Cute name. HORRIBLE APP.

Thanks you lovable little punks you. I am now quite a happy child.

---

### Post by msak007 on 2006-06-23
Does the built-in server give you the option of connecting using a web browser? I saw the option to use a specific port in the 59xx range for a VNC client, but when I had a VNC server set up in Windows there was also an option to specify a port in the 58xx for the using a web browser if you didn't have a VNC client on the machine.

---

