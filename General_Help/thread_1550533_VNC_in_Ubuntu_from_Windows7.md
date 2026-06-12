---
title: "VNC in Ubuntu from Windows7"
date: 2010-08-11
forum: General Help
---

### Post by SanSingh on 2010-08-11
Hi

I am trying to VNC into Ubuntu via a local network and not sure if i am doing this correctly and securely.

Currently i have TightVNC viewer and Putty installed on my Windows machine. i use Putty to log into Ubuntu and start VNC server (i think its X11). I then start VNC viewer on the windows machine and log into Ubuntu as normal, however this is really slow and it takes a long time
to refresh.

My local network is connected to the internet so i want to be sure
that this is all secure even thought my router has a firewall.

Can anyone offer me any advice or where i can obtain a guide on how to set this up securely, i cant seem to find anything on the internet. I have read something about tunneling but not sure how to set this up, and about vino server.

Your help will be much appreciated

---

### Post by b.bugra on 2010-08-11
Why not try Ubuntu's own remote desktop? It is also VNC and you can use passwords, confirmation etc for security. TightVNC on Windows can connect to Ubuntu with no problem on my machines. You'll have to disable compiz, though. If you do not, screen will seem to freeze on Windows machine.

---

### Post by anglican on 2010-08-11
> **SanSingh said:**
> Hi

I am trying to VNC into Ubuntu via a local network and not sure if i am doing this correctly and securely.

Currently i have TightVNC viewer and Putty installed on my Windows machine. i use Putty to log into Ubuntu and start VNC server (i think its X11). I then start VNC viewer on the windows machine and log into Ubuntu as normal, however this is really slow and it takes a long time
to refresh.

My local network is connected to the internet so i want to be sure
that this is all secure even thought my router has a firewall.

Can anyone offer me any advice or where i can obtain a guide on how to set this up securely, i cant seem to find anything on the internet. I have read something about tunneling but not sure how to set this up, and about vino server.

Your help will be much appreciatedSee this thread:

[http://ubuntuforums.org/showthread.php?t=1544847](http://ubuntuforums.org/showthread.php?t=1544847)

H

---

### Post by SanSingh on 2010-08-11
Thanks
 
I will give this a try and let you know how it went.
 
However, will this resolve the problem i am having with it all running real slow on my windows machine, or do i have to configure x11vnc.

---

### Post by krunge on 2010-08-11
> **SanSingh said:**
> 
However, will this resolve the problem i am having with it all running real slow on my windows machine, or do i have to configure x11vnc.
For x11vnc you may need to provide the "-noxdamage" option to improve the refresh.  This works around a bug in the Xorg server and some video drivers.

---

### Post by SanSingh on 2010-08-11
Hi


How do i go about providing the "noxdamage" option to improve refresh.

I am a beginner, so have no idea

---

### Post by krunge on 2010-08-11
> **SanSingh said:**
> 
How do i go about providing the "noxdamage" option to improve refresh.

Do you know how the x11vnc command is being run?

Do you know if it is the x11vnc command you are using or perhaps it is 'vino' (gnome) or 'krfb' (kde)? You mentioned 'x11vnc' so I thought I would help you with that.

---

### Post by anglican on 2010-08-12
> **krunge said:**
> Do you know how the x11vnc command is being run?

Do you know if it is the x11vnc command you are using or perhaps it is 'vino' (gnome) or 'krfb' (kde)? You mentioned 'x11vnc' so I thought I would help you with that.Sorry Karl, the instructions I referred SanSingh to are where the mention of x11vnc came in, they are:

> 1) Login via ssh:
     
     ssh -L5900:localhost:5900 username@remotehost 

2) On the remotehost use sudo to run x11vnc:
     
     sudo x11vnc -ncache 10 -display :0 -usepw -q 
You should see something like (in the ssh terminal):
     
                                                 The VNC desktop is:      remotehost:0
PORT=5900 
                                
3) Run the vncviewer on your localhost and connect to  "localhost:0" which should then show you the gdm login screen. You can  login and use remotehost as normal.

Sorry: just noticed that your local computer is windows. You need to install "putty" (from [http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/"))  on the windows computer then set up a tunnel in putty. In the  SSH->Tunnels menu enter 5900 as "Source port" and "localhost:5900" as  destination port then click on "Add". You may need to check the "Local  ports accept connections from other hosts" box - I don't use Windows so  I'm not sure on that - try it either way.
So, to add the "-noxdamage" option you change the command that runs x11vnc to:
```
sudo x11vnc -ncache 10 -display :0 -usepw -noxdamage -q 
```Note that the "sudo" command is only necessary if you have not already logged in on the linux computer console, if so just omit the word "sudo" from the command (the context of that thread was to login on the remote computer via the gdm login screen using vnc).
I should perhaps also mention that you will need to have set a vnc password on your linux computer to use the "-usepw" option:
```
vncpasswd
```H

---

### Post by SanSingh on 2010-08-12
Cheers thanks for help

It seems to be working a bit faster now (uninstalled compiz).

I will try the process you have outlined above. However i have been starting VNC server linux without the ssh command, does this mean it not tunneling via ssh and is not sure.

I want to know that this is secure, is there any tools i can use to monitor access to my linux box.

---

### Post by krunge on 2010-08-12
> **anglican said:**
> Note that the "sudo" command is only necessary if you have not already logged in on the linux computer console
Also note that "sudo" being enough to access display :0 is only a relatively recent development (a year or so.) It won't work on older systems, and may not work on some configurations and/or distros.

Traditionally (for the past 25 years or so) one would need to set the XAUTHORITY environment variable to point to the X secret cookie file for display :0 .  For x11vnc the "-auth" option is equivalent to doing this.

---

### Post by Samulus on 2010-08-12
If you want to use VNC "securely" then you'll want to tunnel your VNC traffic through SSH.
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
That should help you.

---

### Post by Samulus on 2010-08-12
If you want to use VNC "securely" then you'll want to tunnel your VNC traffic through SSH.
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
That should help you.

---

