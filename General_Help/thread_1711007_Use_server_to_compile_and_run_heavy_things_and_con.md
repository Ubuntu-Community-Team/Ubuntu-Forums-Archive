---
title: "Use server to compile and run heavy things and control it with another machine"
date: 2011-03-20
forum: General Help
---

### Post by GTMoraes on 2011-03-20
Hey there, 

tl;dr version:

Can I run/compile programs on my remote server and control it using LAN? How do I do it?

Long Version:

I have a spare computer here. It's rather powerful for my daily needs (Athlon X2 6000) and I want to set it as my HTPC/Server.
Don't worry about HTPC, it got Digital Audio output and a Radeon HD3200 with HDMI out, outputs 1080p pretty well under Windows (I'll setup it for Ubuntu when I get everything straight).
So, I thought "Well, I think it's going to be overkill to let such machine as a HTPC only. I'll use it as a server too!". So far so good, but I don't know anything about servers or such. I would like it, as a server, to compile huge programs and handle big compressions (I'm actually with a Celeron ULV 1.2GHz netbook for such tasks, takes ages).
Also, it would be pretty nice if I could control the server with my netbook. Like, Start/Stop music/movies with my netbook, control the Boxee/XBMC (Media Players) with the netbook, and, if possible, control its mouse. 

Btw, will Ubuntu 10.10 support Hardware Acceleration for ATI Radeon HD3200? Over Windows' DXVA it works OK.

I'll be waiting for an answer =)
Thank You

P.S.: Sorry if I posted on the wrong section, feel free to move the thread to its proper place

---

### Post by abyrne on 2011-03-20
I tried to compile a kernel on a 1.6Ghz AMD before. Hell on earth.

I don't know about controlling the media players. Maybe someone else can help you with that.

As for controlling the compilers, you could always use [SSH]("https://help.ubuntu.com/community/SSH") for the terminal or [VNC]("https://help.ubuntu.com/community/VNC") for the graphical interface.

---

### Post by tgalati4 on 2011-03-20
You can simply forward x using the appropriate switches:

ssh -2 -Y gtmoraes@myhtpcserver
gnome-panel

---

### Post by GTMoraes on 2011-03-20
Thanks =)

I'll try those when I have set up the computer here.


So far, looks like I'm able to control the machine with my netbook through LAN, but not the media players specifically.
More help will be appreciated =)

---

### Post by tgalati4 on 2011-03-20
After you log in, you can simply set up a launcher on the desktop/laptop with:

ssh -2 -Y user@machinename rhythmbox

That will bring up rhythmbox and you can play music on the htpc server.  There is also a cli client and you can run any player using this method.

man rhythmbox-client

---

### Post by GTMoraes on 2011-03-20
Just thinking here...
Is ssh like a remote "Run this command" order?
Like, if I want to open, say, gedit, I should issue this: "ssh -2 -Y htpc@htpc gedit"? But how does it know where htpc@htpc is? It "just finds"?
How do I control the desktop like the Remote Desktop, on windows?

---

### Post by jerenept on 2011-03-20
> **GTMoraes said:**
> Just thinking here...
Is ssh like a remote "Run this command" order?
Yes it is, in fact, that is its purpose.
> 
Like, if I want to open, say, gedit, I should issue this: "ssh -2 -Y htpc@htpc gedit"?I don't know, really>  But how does it know where htpc@htpc is? It "just finds"?
Your router deals with this. You can also use the IP address of your media server, if you want.> 
How do I control the desktop like the Remote Desktop, on windows?
I'd say VNC.

---

### Post by GTMoraes on 2011-03-21
Thanks =) I'll try to get some time to setup the machine on the living room, then I'll be back here to report how it worked out.

Still, the question regarding the control of Media Player(s) is still open, just saying =)

---

### Post by tgalati4 on 2011-03-22
Put the numeric address in your /etc/hosts file:

sudo nano /etc/hosts

192.168.1.123  HTPC

---------------

Just about every linux-based media player has a command-line, or remote client way of driving it.  You just need to present a specific use case for additional suggestions of how to do it.

mpd is one of the more popular remote player servers:

apt-cache search mpd

It has several clients that can remotely control it.

---

### Post by GTMoraes on 2011-03-22
Hm, I can do it. I'll take a look at the mpd
Thank you very much for your tips =)

I'll be settin' up the machine tomorrow or next tomorrow, my sister wedding is messing things up around here

---

### Post by GTMoraes on 2011-04-04
Long time. Been having some issues with the fglrx and the kernel 2.6.38, I decided to keep with the 2.6.35-28 till things get fixed.

The machine is all set up, I'll be trying to run the SSH and everything on it today. I'll post back with the results

---

### Post by GTMoraes on 2011-04-07
Hey. 

I've sorta got it. SSH does the job nicely when it comes to music playing, actually even better than what I've planned, but I can't make VNC work.
Windows can right-click and play files thru XBMC, I'm still trying to figure it out for my linux computers.
With SSH, it's like I have the Media Center' command line on my Terminal. Pretty cool, 100% of what I've thought about "letting heavy things to the power machine"

I've set up VNC but the Client can't find the Server, no matter what I try.

If you guys have any tips, please tell me =)

Thanks


[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by tgalati4 on 2011-04-07
What happens when you run gnome-panel on the server (after logging in with ssh -2 -Y)?

I don't use VNC, but when I played with it, it worked out of the box.  There are at least 3 flavors and some work better than others.

---

### Post by GTMoraes on 2011-04-10
> **tgalati4 said:**
> What happens when you run gnome-panel on the server (after logging in with ssh -2 -Y)?

I don't use VNC, but when I played with it, it worked out of the box.  There are at least 3 flavors and some work better than others.

it opens the top gnome panel from the HTPC, but conflicts with my netbook's gnome-panel. It works, but isn't exactly what I want.

I simulated a Kernel compilation. Couldn't describe better than "Beautiful". It's exactly what I wanted over the CLI! Über thank you!

But I can't make VNC (Remote desktop, right?) work. It just doesn't find each other. Am I missing something?
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

