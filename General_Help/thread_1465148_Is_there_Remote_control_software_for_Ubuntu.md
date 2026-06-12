---
title: "Is there Remote control software for Ubuntu?"
date: 2010-04-29
forum: General Help
---

### Post by schwabdale on 2010-04-29
I'm looking for something like Logmein or showmypc.com
Please post

---

### Post by jonny163 on 2010-04-29
In Lucid, go to Systems > Preferences > Remote Desktop and set it up
Is that what you mean?

---

### Post by Grenage on 2010-04-29
I would recommend staying away from remote desktop, look at Nomachine NX.  Very responsive and secure.

---

### Post by schwabdale on 2010-04-29
I want to be able to remote control a Ubuntu PC. Sorry for the misunderstanding.

---

### Post by Ryan Dwyer on 2010-04-29
Set up Remote Desktop as suggested above. If you're connecting from another Ubuntu machine, go to Applications > Internet > Remote Desktop Viewer. If you're connecting from a Windows machine, download VNCviewer.

---

### Post by Grenage on 2010-04-29
If you're going to use Remote Desktop, make sure you use a damn good password; it's nowhere near as secure (or speedy) an NX.

---

### Post by AntiBodies on 2010-04-29
alas Ubuntu doesn't really have an easy equivalent to logmein, showmypc etc. I can hear people now say wtf vnc, nx!! I say easy equivalent for a reason and both words are relevant "easy" and "equivalent".

But ubuntu and linux does have the king of remote access.. SSH.. which is a simple apt-get install ssh-server (maybe openssh-server) away. it is the king of remote access but it is command line but command line in linux means everything and using it you can, say, install and start a vnc server so you can see the desktop of the active user (or start a new session) and also tunnel your vnc traffic through the already established encrypted ssh connection. freeNX is also great if not a bit harder to install and configure correctly but it has better response but requires a different client on the other end.

all of the above is great but somewhat moot if you cant forward the port in your firewall so you can get access from the outside. Which is one of the big pluses to a service like Logmein or Showmypc or gotomypc whichever.

all of the above services work because you are routing your traffic through a third party (through logmein servers etc) in a man in the middle type encrypted arrangement (lookup Reverse SSH Tunnel also). unfortunately there doesn't seem to be any company willing to support linux/ubuntu as the target PC (you can be the viewer).

I think if it would be great if Canonical offered such a service (perhaps pay, perhaps free) as I think a lot of people would use it.

---

### Post by schwabdale on 2010-04-29
Talk about the Nail on the Head. I want to be able to pass right through a firewall/Wireless router to 
control the desktop. It sounds like there is no easy way to do this?

---

### Post by Grenage on 2010-04-29
Yes, if you have access to the router then it's quite easy to forward a port. You might not even NEED to forward a port manually, if uPnP is enabled.

---

### Post by schwabdale on 2010-04-29
No, I will not have access to the router.

---

### Post by AntiBodies on 2010-04-29
Yeah if you dont have access to the firewall and it isnt uPnP you are a bit stuffed.

Not completely though, I would suggest if you are willing to put the work in you should investigate Reverse SSH Tunnels. this is effectively what the ShowMyPC service does, which is pretty stink that although using all this very linuxy technology for free under GPL, they do not support linux at the end of it.

You need a third party server (so "you", "middle man" and "target")that has SSH open to tunnel your traffic through to the target server. effectively both you and the target connect to the middle guy and he joins you together so you are talking to each other. This gets around firewalls as both yourself and the target are making outgoing connections and don't require incoming connections (which would be blocked by the firewall)

works very well I have set it up for some customers.

---

### Post by AntiBodies on 2010-04-29
here is a good post on explaining the procedure

[http://toic.org/2009/01/18/reverse-ssh-port-forwarding/](http://toic.org/2009/01/18/reverse-ssh-port-forwarding/)

as you can see SSH is the king of remote access

---

### Post by egalvan on 2010-04-29
> **AntiBodies said:**
> 
 which is pretty stink that although using all this very linuxy technology for free under GPL, t**hey do not support linux at the end of it.**

The reason I boycott companies... 

No Linux support -> I don't use them, nor do I recommend them.

And I write a (paper) letter explaining exactly that.

My two cents worth at supporting FOSS/OSS.

See my sig line below...

---

### Post by 2hot6ft2 on 2010-04-29
> **schwabdale said:**
> No, I will not have access to the router.
If you have no control over the router you'll have to set it up to a port that the router doesn't block for incoming connections to the server. Perhaps 80 (web browsers) or 443 (ssl), I really don't know on that but as you've already been told ssh and freenx are a great way to do a secure remote desktop.
See the guide below if you want to go that route.
> **schwabdale said:**
> I want to be able to remote control a Ubuntu PC. Sorry for the misunderstanding.
That can be done too with it.

True that it takes some setting up but once it's done I wouldn't trade the security and speed for your so called easy equivalents.
> **AntiBodies said:**
> alas Ubuntu doesn't really have an easy equivalent to logmein, showmypc etc. I can hear people now say wtf vnc, nx!! I say easy equivalent for a reason and both words are relevant "easy" and "equivalent".
If you want an easy equivalent then give this a try
[TeamViewer is ready to use, right after downloading! Download, execute, and get started! - Your first session will start in less than a minute.]("http://www.teamviewer.com/download/index.aspx?os=linux")

Oh wait you said there was nothing for ubuntu.
:popcorn:

---

### Post by AntiBodies on 2010-05-06
Thats good news about Teamviewer. I knew of them but didnt know they had a linux client. could use that although I think Teamviewer is about helping out a team member or remote support etc so you would need a person at both ends to initiate the connection etc so not a always on connection etc but still useful and Teamviewer similar to the other services gets around firewalls by making outgoing connections.

> a port that the router doesn't block for incoming connections to the server. Perhaps 80 (web browsers) or 443 (ssl)

unless you are running a web server behind the router all incoming connections will be blocked. a standard/default setup for all routers/firewalls is all incoming blocked (internet can not get into your LAN on any port) and all outgoing is allowed (your LAN can get to all ports/addresses on the internet). so the only way that the internal server/workstation you are wanting to get connected to can be contacted from the internet directly is to have the firewall open incoming for the ports you want to use AND have the packets NATed (or Port Forwarded) to your internal server/workstation IP.

---

