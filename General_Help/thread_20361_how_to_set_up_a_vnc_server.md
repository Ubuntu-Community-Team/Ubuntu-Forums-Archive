---
title: "how to set up a vnc server?"
date: 2005-03-16
forum: General Help
---

### Post by rookie on 2005-03-16
guys, i am lost

i searched this forum (and others), i googled, i visited the offical web-sites, but i am just too dumb to get vnc to work

i have installed on my ubuntu-box:

vncserver
tightvncserver

could someone please tell me how the heck i can configure one of them? Why can't there be an easy to use graphical interface where i can specify uername, password etc?

what did i do so far?

- opened ports in my firewall (5800, 5900)
- enabled remote desktop
- installed tightvnc on my notebook

any suggestions?

thx in advance

---

### Post by -Rick- on 2005-03-16
Here is how I did it:
* Install tightvnc(with synaptic).
* Edit/check vnc.conf (I didn't change anything there)
* Run vncpasswd and type a password
* Run 'vncserver :1' (When you want to stop it run 'vncserver -kill :1')
* Go to the client machine and let it connect to your server ip(In gnome just start 'Terminal Server Client', otherwise it would be 'vncviewer youriphere' I think)

---

### Post by rookie on 2005-03-16
thanks a lot for your input, I got it running. I'ts slow, but okay. May be,in time, there will be other methods to remotely control a ubuntu box from a windows system

---

### Post by az on 2005-03-16
Computer > Desktop preference > Remote desktop

---

### Post by brousch on 2005-03-16
*thanks a lot for your input, I got it running. I'ts slow, but okay. May be,in time, there will be other methods to remotely control a ubuntu box from a windows system*

The speed of VNC depends on a few things:
1. connection speed
2. display size (800x600 is faster than 1024x768)
3. number of colors (16bit is faster than 24bit)
4. vnc compression settings

You can change settings for 2, 3, and 4 in the vnc config file.

With 4, the higher the compression you use, the uglier things will get (jpeg artifacts and such). Also, if you go too high on compression on a server with a slow processor, you can actually make vnc run slower than with lower compression.

So fiddle around with settings until you get a combination you like. Personally, I use 800x600 with 16bit color and low compression. But I usually connect over 100mbps lan or 4mbps cable.

---

### Post by rookie on 2005-03-17
The speed of VNC depends on a few things:
1. connection speed
2. display size (800x600 is faster than 1024x768)
3. number of colors (16bit is faster than 24bit)
4. vnc compression settings

You can change settings for 2, 3, and 4 in the vnc config file.

With 4, the higher the compression you use, the uglier things will get (jpeg artifacts and such). Also, if you go too high on compression on a server with a slow processor, you can actually make vnc run slower than with lower compression.

So fiddle around with settings until you get a combination you like. Personally, I use 800x600 with 16bit color and low compression. But I usually connect over 100mbps lan or 4mbps cable.[/QUOTE]

that's the only remaining problem. i have no idea how to access the vnc config in ubuntu. until now, i used the vnc viewer to define these things, but this is only possible with the windows vnc client.

---

### Post by brousch on 2005-03-18
The command I use to start the VNC server is:
**# vncserver -geometry 800x600 -depth 16 -name Ryoko**

**-geometry** sets the resolution
**-depth** sets the number of colors
**-name** sets the VNC session name (not really necessary)

My VNC server's IP address is 192.168.0.2 So from my lan, I open tightvnc on my windows computer and connect to **192.168.0.2:0**

It is a bit trickier coming in from the Internet, since I have to forward a port on my firewall. You mention a firewall in your post, but it is not clear if you mean a software firewall on your Ubuntu server, or a hardware firewall on a LAN.

---

### Post by Spank on 2005-03-23
Hello i'm new here i've gone and read as much as i can About this VNC Having recently linstalled Ubuntu on my system i am eager to try it out however searching google i cannot find how to connect using to this VNC using Windows XP
Thanks for any help.

---

### Post by brousch on 2005-03-23
*how to connect using to this VNC using Windows XP*

You need to install a VNC client on Windows XP.
Here a couple you can use for free:
[TightVNC](http://www.tightvnc.com/) 
[RealVNC](http://www.realvnc.com/)

---

### Post by Gtaylor on 2005-03-27
I got VNC working but when I connect to a remote machine, it isn't accepting my keyboard input. It appears that anything I type is going to the client machine rather than the server. My mouse works just fine though. Any ideas?

---

### Post by wolfwood2x on 2005-03-30
I got mine working sorta, when i setup vncserver -geometry 800x600 -depth 32 i can connect but when i do i see a solid grey screen with an x on it, kind of looks like when knoppix doesnt boot righton an older machine. is this a primitive x windows? im still a linux noobie so can anyone help me? i was hoping for my typical gnome desktop i get when i log directly into my ubuntu box

---

### Post by noiz on 2005-03-30
this is kinda off-topic, but i have my vnc server set up and everything works the way i want it to, just i have one thing about when people connect.  im using the remote desktop from the desktop preferences menu, and im wondering how after i let someone gain control of my system, how do i stop them from controlling my desktop without them just exiting their vnc client?

-noiz

---

### Post by MarkLP on 2005-03-31
Hi all, just signed up here as yesterday i installed Ubuntu, i have set it up fine apart from the only problem being how do i install programs? Like TightVNC? I have the .py files and .ini files etc.. but if i double click and then click on run nothing happens? Any help is appreciated. Thanks Mark

---

### Post by noiz on 2005-03-31
to install as type 'su' and then enter the password for root at the command prompt.  then type 'apt-get install synaptic' and let that install.  then you should have a program called 'Synaptic Package Manager' under apps->system tools.  that program shows what things you can easily install.

-noiz

---

