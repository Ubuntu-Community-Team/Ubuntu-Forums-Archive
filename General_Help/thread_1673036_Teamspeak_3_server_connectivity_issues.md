---
title: "Teamspeak 3 server connectivity issues"
date: 2011-01-21
forum: General Help
---

### Post by arewethereyet on 2011-01-21
Hi, I have Ubuntu 10.04 x86 installed, trying to get teamspeak 3 beta30.

I have followed this guide:
[http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/](http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/)

And can not get my network setup correctly to allow people to connect externally from my LAN. I have forwarded every relevant port I could find to the computer hosting TS, I forwarded them first as their respective protocols, and then as the combined UDP/TCP. I tried Forwarding single port numbers, and then port ranges.

I have also tried uninstalling selinux. I have tried connecting directly to my cable modem with the server.

What is really frustrating, is I had this working perfectly three months ago with all the same software, using the same guide I listed above.

The only thing I can imagine has changed is my operating system itself with system updates.

My network looks like:

Comcast cable modem--->Netgear WNR3500L Router----->Ubuntu 10.04 x86 desktop edition

Anyone have any idea's what else I could possibly check? I can connect to and manage the TS server fine using localhost:9987 or 192.168.1.x:9987, it just wont allow any connections from outside the network.

---

### Post by earthmeLon on 2011-01-21
When you connected your server directly to the cable modem, did you test and make sure that the server was still able to connect to the internet successfully?  If you are 100% sure everything except the teamspeak server was working, then it sounds like your problem exists within your computer's setup.  Find out [exactly] what ports TeamSpeak uses and add them to your firewall. (google iptables for more information).

If this is not true, it's possible that your problem exists within your router.  DMZ forwards all incoming traffic to a specific client.  You *could* set your server up as DMZ to test some issues (such as seeing if you're forwarding the wrong port).  Leaving DMZ open is 'insecure' and you should do some more reading if you plan on doing it for any long duration of time.

Also, TCP connections can create "SESSIONS" within your router.  These sessions can last for days and can cause problems.  I'm not sure that this could be causing an issue for you, but be sure to turn your router off for ~30 seconds every time you make any significant changes.  This *should* reset anything within itself as well as timeout anything cache'd on your computer.

Good luck!

Offtopic:
Mangler is an open-source Ventrilo client that works wonderfully.

---

### Post by arewethereyet on 2011-01-22
> **earthmeLon said:**
> When you connected your server directly to the cable modem, did you test and make sure that the server was still able to connect to the internet successfully?  If you are 100% sure everything except the teamspeak server was working, then it sounds like your problem exists within your computer's setup.  Find out [exactly] what ports TeamSpeak uses and add them to your firewall. (google iptables for more information).

If this is not true, it's possible that your problem exists within your router.  DMZ forwards all incoming traffic to a specific client.  You *could* set your server up as DMZ to test some issues (such as seeing if you're forwarding the wrong port).  Leaving DMZ open is 'insecure' and you should do some more reading if you plan on doing it for any long duration of time.

Yes, the computer did connect to the Internet well when connected directly to the hub/modem.

I have flushed all the iptables and as far as I know disabled it completely. I realize that probably isn't a good idea, but I'm just trying to figure what is wrong here. The problem really can't be the router, because I had this working about 3 months ago perfectly, no issues at all. I also did try bypassing the router, as well as opening up all security on it.

> **earthmeLon said:**
> 
Also, TCP connections can create "SESSIONS" within your router.  These sessions can last for days and can cause problems.  I'm not sure that this could be causing an issue for you, but be sure to turn your router off for ~30 seconds every time you make any significant changes.  This *should* reset anything within itself as well as timeout anything cache'd on your computer.

Good luck!

I did shut the router down over night and try it in the morning, still didn't work(and this also is sort of irrelevant where I have tried bypassing the router altogether)

> **earthmeLon said:**
> 
Offtopic:
Mangler is an open-source Ventrilo client that works wonderfully.


Yes sir, I use that for ventrilo. I am setting up my own teamspeak server because it is free for non-profit use, and I personally think teamspeak 3 is better then vent, it is far more configurable, with more options in general....just my opinion 8)

---

### Post by earthmeLon on 2011-01-24
iptables is a filter/firewall that prevents unauthorized incomming requests (blocks your computer from being a 'server').

I have a free (8man) Ventrilo server set up on my server.  In order for anybody to connect, I had to modify my '/etc/sysconfig/iptables' file to have:
-A INPUT -i eth0 -p tcp -m tcp --dport 3306 -j ACCEPT

3306 is the ventrilo port, and eth0 is the device to allow through the firewall.  Do you have something similar set up within your system to allow connections on whatever port it is you are using for TeamSpeak?  Also, make sure the port you are using isn't already taken (but I'd imagine TeamSpeak would warn you if this was actually happening).

[I believe] it is important to put this towards the top of your configuration, above your REJECT statements.  Make sure you restart the iptables service once you've made your changes.


You may find [[COLOR="Plum"]this post[/COLOR]]("http://forum.teamspeak.com/showthread.php/48969-Open-Close-Ports") relevant.

---

### Post by arewethereyet on 2011-02-01
> **earthmeLon said:**
> iptables is a filter/firewall that prevents unauthorized incomming requests (blocks your computer from being a 'server').

I have a free (8man) Ventrilo server set up on my server.  In order for anybody to connect, I had to modify my '/etc/sysconfig/iptables' file to have:
-A INPUT -i eth0 -p tcp -m tcp --dport 3306 -j ACCEPT

3306 is the ventrilo port, and eth0 is the device to allow through the firewall.  Do you have something similar set up within your system to allow connections on whatever port it is you are using for TeamSpeak?  Also, make sure the port you are using isn't already taken (but I'd imagine TeamSpeak would warn you if this was actually happening).

[I believe] it is important to put this towards the top of your configuration, above your REJECT statements.  Make sure you restart the iptables service once you've made your changes.


You may find [[COLOR=Plum]this post[/COLOR]]("http://forum.teamspeak.com/showthread.php/48969-Open-Close-Ports") relevant.

 Thank's for the response. As it turns out I believe it was something to do with IPtables, because I uploaded the TS server directly to my server downstairs and it worked immediately just needing the router to forward 9987. I don't believe the server has IP tables installed. If i remember correctly that was a aftermarket install I did on this computer to make web browsing as secure as possible.

---

