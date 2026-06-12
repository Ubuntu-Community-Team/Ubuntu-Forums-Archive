---
title: "Remote desktop"
date: 2011-04-18
forum: General Help
---

### Post by eddie3000 on 2011-04-18
HELLO!! 

I have managed to control a computer with ubuntu 10.10 from another computer with ubuntu 10.10, both at home connected to a modem-router using vinagre. 
Could anybody help me in figuring out how to access the same computer from another location?? (Away from home) I have two IPs, the DSL's and the computer's IP in the home network. I know that a static ip would be desirable. I know what my adsl ip is at the moment, and as long as I don't reset the connection the ip should remain the same.
Thanks!

---

### Post by rez182 on 2011-04-18
you can do this with TeamViewer. google it. it works like a charm in windows pc, but i was not able to connect to another ubuntu from my ubuntu with TeamViewer. you can give it a try though.

---

### Post by eddie3000 on 2011-04-18
Thanks. I've just taken a look at teamviewer. But can't this be done using ubuntu "as is" without having to install anything else? Can't it be done with vinagre?

Anyhow, if I use Teamviewer (or wahtever other method) and I have dynamic DNS, is there a way of knowing my dns when it changes?

---

### Post by rez182 on 2011-04-18
as long as you have TeamViewer installed in all the pcs you want to remotely connect to, it does not matter. create an account, then you can see all the pcs that are online like in messengers and connect to them easily.

---

### Post by thecamelcoder on 2011-04-18
There are a couple of things that you need to consider. 

1) if you are trying to access your desktop from outside your LAN, home network, then you are going to need to place a route into your firewall to allow traffic on that port through and direct it to to a specific destination, your desktop.

As always with opening up your router, you increase the risk of attack, however small it may be. 

Create an ssh tunnel
[http://www.linux-geek.co.nz/2011/04/18/how-to-create-an-ssh-tunnel/](http://www.linux-geek.co.nz/2011/04/18/how-to-create-an-ssh-tunnel/)

ssh tunnels explained
[http://www.linux-geek.co.nz/2011/04/18/ssh-tunnels-explains/](http://www.linux-geek.co.nz/2011/04/18/ssh-tunnels-explains/)

This is were option two becomes useful. 

2) While a little advanced for a beginner, one of the best ways of gaining remote terminal access from outside your network is via a ssh tunnel. This means that you then only need to open up port 22 on your router and via the use of IP tables control were your connection goes. 

I have attached a tutorial for ssh-tunnels if you wanted to have a look. 

3) This is the safest and easiest of all three options. The use of web hosted services such as TeamView. Team viewer is a Client Sever installation. It has many advantages over the others options such as the use of port 80, no config changes to your firewall and no tricky routing. 

I hope this helps make it decision for remote access a bit easier. 

Good questions
):P

---

### Post by eddie3000 on 2011-04-18
Thanks for those three answers! I think I will go through them all. Although I'm no expert and only a beginner, I think going through options 1 & 2 may be worth it. If I can't get it working, I can always move on to step three.
:)

---

### Post by eddie3000 on 2011-04-18
Both tutorials are interesting. I had no idea at all about it. And it's nice to learn.

OK! So here are a few other silly questions, I'm sure! :roll:Could I activate the DMZ option on my router to send all incoming requests to my ubuntu pc? Is that risky? I guess it's best to set a single port. Why do others use port 80? Could I use any port I choose? 
I checked teamview, and I think you need somebody on the other side to accept the connection. Can it be done with nobody on the other side? I haven't been able to figure it out by myself, and if I would like to access my home pc from somewhere else, I probably won't be around to accept the connection:lol:

Well, as you can see, I have no idea!

---

### Post by rez182 on 2011-04-19
> I checked teamview, and I think you need somebody on the other side to  accept the connection. Can it be done with nobody on the other side? I  haven't been able to figure it out by myself, and if I would like to  access my home pc from somewhere else, I probably won't be around to  accept the connection:lol:
yea teamviewer does not require anyone to accept the connection if you set it to auto start and set a permanent password for it. but i tried it only in windows, dont know about linux, if it has an auto start function or not. you can go through the options to figure it out or ask in another thread. i currently don have it installed so cant tell.

---

