---
title: "Remote desktop over WAN using vncviewer? Possible?"
date: 2009-07-21
forum: General Help
---

### Post by Bucky Ball on 2009-07-21
Hi all,

I have just spent four days working on the in-laws computer which I built at christmas. When I built it, I set up Remote Desktop to work on it (I live 750kms away and drove back today). After working on it, there are a couple of things that still need tweaking and I would like to get the remote desktop happening so I can work on it from here.

Is this possible? I am trying with vncviewer and the correct details, am assuming the computer is on (at their end, not mine(!), usually is 24/7) and that it is switched to share the Desktop in 'Remote Desktop'.

I am using:

```
vncviewer RemoteMachine:0

and 

RemoteMachine:0
```... where 'RemoteMachine' is the name of the ... the remote machine. The first gives me:

> Connection to host "vncviewer GreenMachine:0:5900" was closed.The second:
> 
Connection to host "GreenMachine:0:5900" was closed.Any ideas? I have no experience whatever with this. What I can figure is that if I was trying to connect to a machine on my LAN, I would probably be doing it by now, but because I am trying to get out of my LAN (on Port 5900) and into another machine on another LAN 750kms away I am going to need a little more detail and tweaking (and may not have set it up quite right at the other end).

I am going to experiment with my laptop on the LAN and get familiar, then see if I can transfer that to the WAN concept.

All ideas, clues, tips and tweaks gratefully appreciated. :)

---

### Post by Bucky Ball on 2009-07-22
Okay, I have been experimenting with the machines on my LAN and not having much success. I think I have the right things installed but when I open 'Remote Desktop Viewer' and try to connect to a machine, I get this message:
> 
Connection to host "localhost:1:5900" was closed.

I can ping machines okay and last night was trying to figure if I needed to open port 5900 on my router but couldn't figure how to do it. D-Link 704P.

Any ideas?

---

### Post by kg4cna on 2009-07-22
Yep....you'll need to open port 5900 in order for VNC to work. I routinely log into my home machine from work using the Terminal Services Client from the Internet menu.  In a former job, I had to log into the radio station automation system and the reception desk system periodically.  Port 5900 must be open on the target router (for remote access) when you use VNC. It's a different port for MS Remote Desktop....but I can't remember which one.

Allen

---

### Post by Bucky Ball on 2009-07-22
Figured. Thanks. Trying to figure out how to do that. I have just managed to finally get the three machines on static IPs and not getting DHCP served from the router, so there is a breakthrough. I have been trying on and off for ages.

I am now finding the remote shares (except my Xubuntu box but getting that working is long and involved as I have just discovered so leave that for now) but yea, getting closed. Odd thing though; when I try to connect to my Xubuntu box from another machine (it is the only one that doesn't show up when I do a 'Find' in Vncviewer), it seems to connect, there is just no remote desktop. But there is also no error message. ?!?

Anyhow, I'll keep going with it and keep any ideas coming. :)

---

### Post by Bucky Ball on 2009-07-22
kg4cna, do you remember at all which section of the router setup you used to assign the port as open? I am trying everything on the d-link and getting nowhere. (so far).

---

### Post by Bucky Ball on 2009-07-23
So far, I can open 'Remote Desktop Viewer', in 'Find' both the machine I am working on and my laptop appear. I click the laptop, attempt to connect and gets closed as usual.

I read from one page that 'localhost:1' would test to see if things were working correctly. Well, port 5900 gets closed there too. Syntax? Do I need to set that port 5900 as open on the local machine somewhere in Ubuntu?

I figure if the two machines are appearing okay in 'Find', then must be a problem with the way the D-Link 704P router is set up and port 5900 being closed. I have tried a million things with the router to no avail. Just wondering: when I change the router and test something out, do I need to restart a service for the Remote Desktop setup?

Last thing I tried was setting the router so the laptop is a virtual server and opening port 5900 that way. Same as.

Why am I having so much trouble opening that port on the router? I guess it is simple and I am just missing something. Can anyone fill me in on what?

:)

Result of trying 'localhost:1' or anything else:

> Connection to host "localhost:1:5900" was closed.

---

### Post by Bucky Ball on 2009-07-23
I tried changing the port in "Virtual Server" on the router to something else. Exactly the same message and no connection. I checked the D-Link help pages for opening a port on the router and I am doing it the way they describe. 

Do I need to open a port on the local machine? Can see the other machine, just won't connect on any port number it seems. :(

---

### Post by Bucky Ball on 2009-07-23
* Update: Success .. sort of. Not quite at the cigar stage yet.

I fiddled with the laptop for awhile, installed vino and xinetd properly (they didn't seem to be all there when I used 'apt-get' to install them), opened a terminal and ran:

```
vncviewer :1
```... and what do you know, I was informed someones was attempting to control my machine, will I accept and enter a password! 

So, that one seems to be up so made sure vino and xinetd were installed on the desktop, but still can't connect from the desktop by running:

```
vncviewer :1
```... or trying with the ip of the laptop.

Halfway there. Give me that final shove ...

---

### Post by Bucky Ball on 2009-07-25
* Update: It is working. I can connect to and from either machine on my LAN and access desktop and machine. Quite a learning curve. For some peculiar reason it is using port 5901 to do so rather than 5900 as it should, but there you go, it works. If anyone can let me know how to change this (I have it set up in the GUI and config for both machines and router as 5900!) please let me know.

So now I am back to my original question: How do I get into my HOME network from outside the LAN, for instance when I am at uni or travelling?

I looked at a million and one pages to get this going and spent about 10 hours a day for three days. In the end [THIS PAGE]("http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop#Activating_Remote_Desktop_Access") got me over the line. It links to a few pages, one of which is setting up SSH for vncviewer over a secure SSH connection. Preliminary for getting in from outside the LAN (imperative). 


Yet another thread where I ramble on to myself but get there in the end. No matter; it all helps to ramble, I know your out there so thanks everyone. \\:D/

---

