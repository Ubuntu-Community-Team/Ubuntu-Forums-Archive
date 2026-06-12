---
title: "Run a graphic application on the remote PC with SSH"
date: 2006-05-09
forum: General Help
---

### Post by albox on 2006-05-09
Hi,
Usually, when we make a SSH connection, we want to run applications on the PC we are using (the client that will connect itself on the remote PC) but I want to do the opposite : I'd like to run a graphic application on the remote PC with SSH.

So, after the connection on the remote PC, I tried to set the DISPLAY variable and to authorize 127.0.0.1 but it doesn't work :
> 
$ export DISPLAY=:0
$ xclock
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0
$ xhost + localhost
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xhost:  unable to open display ":0"
$ xhost + 127.0.0.1
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xhost:  unable to open display ":0"


Can you help me ?

Thank you ;)

---

### Post by dolny on 2006-05-09
I can't help you cause I have a similar problem. 

I know that running XFCE or KDE through SSH would be really slow, but I would need to do it in order to help my mom with her computer, remotely. 

So if someone knows what to do, please reply.

---

### Post by mexlinux on 2006-05-09
Same problem here.

From Mandrake It was simply run and it works.....
But since I'm in kubuntu I can not run graphical applications in ssh sessions.....

---

### Post by elwingert on 2006-05-09
1) Edit on the remote computer: /etc/ssh/sshd_server and change X11Forwarding to yes
2) restart the ssh service on that computer

You should now be able to launch graphical applications from the remote computer to your client

---

### Post by GNUrag on 2006-05-10
While making ssh connection, one should do this:
[B]
$ ssh -X  201.100.88.84[/B]

this enables X forwarding over ssh, and one should be able to run apps on remote comp.

Also doesnt VNC solve your purpose (in case you're trying to demonstrate someone on a remote location?)

---

### Post by albox on 2006-05-27
Hi,
I solved a lot of problems to install ubuntu on my laptop for 2 weeks but I'm still stuck with this problem here ](*,) 

When I try to start kde (after having launched ssh with -X), I get the following errors :
> X11 connection rejected because of wrong authentication.
X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).

If I try to use xhost + mylocalip, i get :
> X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).


Here is the config file on my client :
>      Host *
     ForwardX11 yes
     ForwardAgent yes

Config file on my server : 
>  
X11Forwarding yes
    GatewayPorts yes
    X11DisplayOffset 10
    X11UseLocalhost yes
    AllowTcpForwarding yes

Can you help me ?
Thanks ;)

---

### Post by Randomskk on 2006-05-28
If you want to be able to control the other end's screen, launch apps on it etc, I think VNC may be what you're after.
If you want to only do VNC over SSH, you could tell SSH to forward the VNC ports, but just plain VNC should suffice.
Why do you need SSH?

---

### Post by albox on 2006-05-28
I tried vnc but I have some troubles too :

> Xvnc version 4.0 - built Apr 19 2005 04:26:49
Underlying X server release 40200000, The XFree86 Project, Inc


Sun May 28 18:01:23 2006
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 8754
 vncext:      created VNC server for screen 0
Removing empty element from the valid list of fontpaths
Option --login is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new --window-with-profile option

(gnome-terminal:9257): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:9257): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Window manager warning: Log level 32: could not find XKB extension.
The program 'gnome_segv' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 435 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


---

### Post by albox on 2006-06-05
up !
I can start X applications on my client now. How can I do if I want to display on the server (just change $DISPLAY ?) ?

VNC try to start GDM but I use KDM. Do you know why ?

Thank you :grin:

---

