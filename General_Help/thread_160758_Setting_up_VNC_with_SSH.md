---
title: "Setting up VNC with SSH"
date: 2006-04-15
forum: General Help
---

### Post by Danni on 2006-04-15
I would like to set up VNC so I can access my Kubuntu machine while in college. I've already set up SSH (on post 21 as the college blocks most ports) and it works great, but now I want to send my whole desktop over. Is there an easy way to do this, bearing in mind the college blocks most ports? (I'd like to continue using port 21.) The college uses Windows XP/2000 (depending on machine). Also, is there any selfcontained viewer for the college's pc? I can't install anything there.

I can set up my router to forward any ports as necessary.

---

### Post by patrixl on 2006-04-15
yes, you need to use the ssh tunneling option.

For example, on my setup, (using putty) I go in the "tunneling" panel and I add forwarding for L:5950  R:somehost:5950

so I can then, at work, connect to localhost:50 with vncviewer and it'll go to my home desktop vnc server.

AFAIK (for windows) the realvnc viewer is self-contained, you can get it without na installer just an exe file you can run.

---

### Post by Danni on 2006-04-15
OK, I've got putty available. realvnc.exe is an installer- I need a different one.

How/what do I install on the Kubuntu machine?

---

### Post by patrixl on 2006-04-15
[QUOTE=Danni]OK, I've got putty available. realvnc.exe is an installer- I need a different one.[/quote]

I did a bit of googling, ultravnc has a standalone viewer for windows. Should do the trick.

> 

How/what do I install on the Kubuntu machine?

I use x11vnc , since it can serve an already existing display, rather than start a new X display like most unix VNC servers do.

I added this line in ~/.kde/Autostart/x11vnc.sh   (executable file)

x11vnc -rfbport 5950 -display :0 -forever &

This runs x11vnc for the :0 X server, forever (till I log out or kill it), and listens on port 5950 ( :50  in vnc lingo).  You might wanna add a password, but I don't btoher since my PC's behind a router and the vnc's only accessible from a tunneled SSH session.

---

### Post by Danni on 2006-04-15
Thank you very much :)

If I can get access to my partner's pc I'll try this out :)

---

### Post by incubus on 2006-04-15
I'd also suggest [tightvnc]("http://www.tightvnc.com"). It's pretty fast, stable, plus you also have the option of accessing VNC through a Java Applet (which means no need for a standalone client and it's platform-independent).

In Ubuntu you'd need packages:
tightvncserver
tightvnc-java

incubus

PS: The suggestion is biased by my ignorance -- I bet other VNCs can also do that.

---

### Post by patrixl on 2006-04-16
tightvncserver or vncserver are both ok, and offer slightly better performance than x11vnc in my experience

However, I like x11vnc because it can take over an existing desktop

Which reminds me, KDE's integrated desktop sharing thing can do that too lol. I don't use it because, in the past, it had very poor performance and would often result in mmmmmmaannnnyyyy reeeepppeeeaaaaaatttted letters if there was any network.

Hopefully it's better by now ;)

[QUOTE=incubus]I'd also suggest [tightvnc]("http://www.tightvnc.com"). It's pretty fast, stable, plus you also have the option of accessing VNC through a Java Applet (which means no need for a standalone client and it's platform-independent).

In Ubuntu you'd need packages:
tightvncserver
tightvnc-java

incubus

PS: The suggestion is biased by my ignorance -- I bet other VNCs can also do that.[/QUOTE]

---

### Post by SadaraX on 2006-04-16
I have to say use something with a good deal of compression unless your home connection has a lot of upload pipe. My cable connection has about 40kbps upload speeds and using tightvnc its very reliable and fast. I used regular vnc for a while and it was simple terrible at how slow it was. I thoroughly recommend vnc over that SSH tunnel. I do this every single day I go to work with putty and a windows tightvnc client. :)

---

### Post by Danni on 2006-04-28
OK, I must be doing something wrong as I can't get it to work. I think it's how I'm setting up putty.

The tunnelling section looks like this:
[img]http://www.dannimatzk.co.uk/putty.JPG[/img]

What exactly to I type in there?

Is it 5950 in the source box, then <my ip>:5950 in the destination box?

The message I'm getting in vncviewer is "Cannot Connect to Server"

---

### Post by SadaraX on 2006-04-28
[QUOTE=Danni]OK, I must be doing something wrong as I can't get it to work. I think it's how I'm setting up putty.

The tunnelling section looks like this:
[img]http://www.dannimatzk.co.uk/putty.JPG[/img]

What exactly to I type in there?

Is it 5950 in the source box, then <my ip>:5950 in the destination box?

The message I'm getting in vncviewer is "Cannot Connect to Server"[/QUOTE]

If you are running VNC on a non-standard default window, then see the paragraph below. Most simply, the source port is going to be 5900, unless you have a different VNC window number. Then the destination is going to be:

127.0.0.1:5900

In the putty HostName or IP Address (the main window), you should put in your IP for your computer (or a name if you have DNS setup for it). Of course, you also need to have an SSH connection on your home system for to connect with.

Lastly, using your VNC client to then connect to your home, you should have VNC connect to 127.0.0.1, this will safely connect you to that IP through an SSH tunnel. 

A word about windows in VNC. VNC starts running on port 5900, but each window of VNC is on a subsequent incremented number. So the default startup window is on 0, the second window is on 1, and so on. Therefore, if your just running a standard VNC window, with no fancy changes, then you are running VNC on window 0. 

Let me give you an example. Say I have a VNC session on window number 5. So, in this case, your "Source port" is still 5900, but your destination is 127.0.0.1:5905, and you still use VNC to connect to address 127.0.0.1.

There is some tricks you can do with variability and port numbers, but those are more than I care to write about in this post. This should get your running with the basics.

---

### Post by Danni on 2006-05-01
Thank you very much- I think I now know where I was going wrong :)

I'll try this on Tuesday when I pop back into college :)

---

### Post by Danni on 2006-05-10
```

Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the tightvncserver script.
Couldn't start Xtightvnc process.

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000

```
I'm getting that now when I try and run tightvncserver. Any suggestions?

---

### Post by SadaraX on 2006-05-10
Yeah, that vnc font problem from ubuntu. I forgot about that one. :) I figured out a fix for my system a long time back. Here it is:

> In the file /etc/vnc.conf
set the line:

$fontPath = "/usr/share/X11/fonts/misc/"

---

### Post by SadaraX on 2006-05-10
Oops, double post....

---

### Post by Danni on 2006-05-12
I've got it working!

Thank you!

---

### Post by Danni on 2006-05-12
I've got it working!

Thank you!

---

### Post by nami on 2007-12-03
Hi Danni,

Any chance of a step by step guide please? :)

---

