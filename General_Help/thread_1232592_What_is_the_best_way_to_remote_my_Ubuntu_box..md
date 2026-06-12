---
title: "What is the best way to remote my Ubuntu box."
date: 2009-08-05
forum: General Help
---

### Post by lorderico on 2009-08-05
Hello,

I am trying to gain access to my machine from outside my local network.  I am behind a linksys router/firewall that is the dhcp.  Currently, I have an ssh, xdmcp, and samba servers installed and I am trying to install a thin client server, but I haven't gotten it to work yet...  Anyway, I want to get access so that I can either a)Get files to and from my pc b)control my computer's gui/ run programs or c)both (from both a linux and windows pc).  I also need it to be secure.  There is no point opening anything up that would be any easy path for a hacker.  I have heard that vnc has many holes and is very insecure.

What is the best way to securely connect to my Linux box?

If possible, specific instructions would be appreciated.

Thanks,
Eric

---

### Post by t0p on 2009-08-05
I suggest using **ssh**.  It is very secure, and cross-platform.  You can use command-line or gui, whichever suits you best.

---

### Post by zeronothing on 2009-08-05
I would try out [[COLOR="Blue"]nomachine[/COLOR]]("http://www.nomachine.com/"). This is what I use to connect remotely to my Ubuntu machine. It uses ssh to encrypt your connection, so the only port you need open on your router is 22. In their download section they supply 32 and 64 bit .deb files for a nice and easy double click install.

---

### Post by Maheriano on 2009-08-05
Another vote for NXClient by NoMachine.

---

### Post by lorderico on 2009-08-05
I am going to try nomachine.  As far as routing, do I simply have to forward port 22 from my router to my machine?  Do I have to do anything with DMZ?

Eric

---

### Post by zeronothing on 2009-08-05
Just forward port 22, to whatever IP address of the machine you want to reach (configure that in your router). that is all you have to do. Make sure you have ssh server install first. Like I said, NXclient relies on ssh for the encrypted remote session.

---

### Post by Maheriano on 2009-08-06
Don't do any port forwarding yet, your router might already be set up for it, mine was. You also might want to use a different port once you get it working, port 22 is notorious for hacking because of its uses, but follow [this guide]("http://ubuntuforums.org/showthread.php?t=736509") to get you started.

---

### Post by Bucky Ball on 2009-08-06
Safest way? Set static IP addresses. I use VNC because I like it and tunnel that through SSH. I am halfway through setting it up when I have time. I have it all working no problem on the three computers on my home network, yet to try it from outside the LAN.

Haven't looked at it since uni started a couple of weeks ago and so not fresh but try this. Gives you Vinagre and VNC methods and go to the part down the page labeled "Establishing a Secure Remote Desktop" for SSH method:

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop#Activating_Remote_Desktop_Access](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop#Activating_Remote_Desktop_Access)

Good luck with it. It's a thrill when you suddenly (finally) see the desktop of your remote machine on your local! Hope this helps ya get there.

(ps: VNC is automatically port 5900 but you can change that. Whatever port you use, it needs to be forwarded.)

---

### Post by lorderico on 2009-08-06
Hello again,

I have gotten nomachine working and I am able to access my PC from outside my local network!  A couple of things:

Probably the most important: I am headed off to college, where I won't have control of the routers.  Does that have to mean the end of my servers, or won't it matter (going to UWW Madison)?

The icons on my desktop are the "old" linux icons, not the new ones (synaptic, for instance, looks different).

Can I transfer files between the two computers?

I am looking into remote wake on lan.

Changing from port 22 definetly seems like a good idea.  I am going to give it a try when I have time.


If you have any input about these topics, please let me know.

Thanks,

Eric

---

### Post by Bucky Ball on 2009-08-07
Definitely change 22 to a custom port.

Most Universities will definitely NOT allow a server (rogue server it is called) that belongs to a student or anyone else to operate within the University network. Lots of reasons, main one being they have no control or access to the server and cannot incorporate it into their security protocol. You might be lucky, but doubtful.

Icons are irrelevent, it is the software and protocols that count (think custom icons ... your network icon could be a penguin, wouldn't matter - SSH is SSH etc).

Finally, congratulations on the breakthrough. Persistence is usually the key. If you ever have time maybe you could write a HOWTO.

Cheers and good luck. :)

---

### Post by khelben1979 on 2009-08-07
> **lorderico said:**
> Hello,

I am trying to gain access to my machine from outside my local network.  I am behind a linksys router/firewall that is the dhcp.  Currently, I have an ssh, xdmcp, and samba servers installed and I am trying to install a thin client server, but I haven't gotten it to work yet...  Anyway, I want to get access so that I can either a)Get files to and from my pc b)control my computer's gui/ run programs or c)both (from both a linux and windows pc).  I also need it to be secure.  There is no point opening anything up that would be any easy path for a hacker.  I have heard that vnc has many holes and is very insecure.

What is the best way to securely connect to my Linux box?

If possible, specific instructions would be appreciated.

Thanks,
Eric

Using ssh is probably more secure than any VNC client, although if the VNC client is configured correctly I think it's pretty secure. Any application or operating system is unsecure if it's badly configured.

---

### Post by Bucky Ball on 2009-08-07
> **khelben1979 said:**
> Using ssh is probably more secure than any VNC client, although if the VNC client is configured correctly I think it's pretty secure. Any application or operating system is unsecure if it's badly configured.

Yes, if you tunnel VNC through SSH as I mentioned in post #8 in this thread and provided a link on how to do it. :)

---

