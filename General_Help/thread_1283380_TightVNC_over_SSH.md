---
title: "TightVNC over SSH"
date: 2009-10-05
forum: General Help
---

### Post by CharlesA on 2009-10-05
I'm trying to setup a way get connected to my ubuntu server from over the internet.

In all the howtos I've read, they say to connect to 127.0.0.1, however I cannot connect to the VNC server at the address. 

I've got into the machine using PuTTy and SSH, but I need to use the ip address of 192.168.1.4:60 to get in.

SSH:

console@ubuntu:~$: vncserver :60 -geometry 1024x768 -depth 16

Starts the server using display 60.

I can connect using 192.168.1.4:60 from my internal network, but I cannot connect from 127.0.0.1:60.

Putty is set to tunnel port 5900 which should be the vnc port.

I'm not quite sure what I am doing wrong.

Any help is appreciated.

---

### Post by sedawk on 2009-10-05
192.168.1.4:60
Your VNC server is listening on his IP.
Connects work from inside the local network.

A.B.C.D:60
If your server is not protected by a firewall any
vnc client on the internet might be able to connect
to your internet-IP. Security risk !
As far as I understood this is not the connection
you want (although it is the easiest one, as you
only need a vnc viewer on your windows pc. No Putty, no ssh)!

127.0.0.1:60
Like above VNC listens to TCP-IP traffic but on
the loopback interface. This interface can only be
accessed from the machine itself, e.g. you have to
run the vnc client on the same machiner. To see
the VNC desktop on your windows desktop you have
to login via putty/ssh using X11-forwarding and
you need a working X-Server on that PC!
Only then can you start the vnc viewer on the server
and see the output on the windows box.
Have you X11-Forwarding enabled?
Are you running an X-Server on your windows PC?


You can run VNC in a more secure way so it doesn't
listen for TCP-IP connections (not even the local loopback
interface) but only for a "direct" local connection.
Instead of "127.0.0.1:60" or "localhost:60" you simply
use either "60" or ":60" to connect.


Port 5900:
I think to know "real" VNC ports is not really needed 
in your setup. Only for completeness:
VNC is only listening on port 5900 if you use DISPLAY :0.
But you use :60, so the VNC port in use is 5900+60=5960.
But normally the VNC software hides that from you  - you only
need to know that if you plan to open firewalls to let
VNC traffic pass directly.

---

### Post by CharlesA on 2009-10-05
I guess I got it to work, but I doubt it's optimal. Set it to forward port 5900 to 127.0.0.1:5901 (using display 1).

Connect to PuTTy, then start the vncserver. Connect using vnc.

EDIT: How would I go about setting tightvnc up so that it doesn't look for connections?

Right now I have it setup so I manuallu start the server and then connect; then kill the server/session when I am done.

Thanks :)

---

