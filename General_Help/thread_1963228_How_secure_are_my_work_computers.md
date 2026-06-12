---
title: "How secure are my work computers?"
date: 2012-04-22
forum: General Help
---

### Post by CaptainMark on 2012-04-22
Ive had some help setting up a vnc network at work so one computer can access another, for the sake of tech support, although after googling about vnc I wanted to test how secure it is from people with physical access to the machine, I was able to get the passwd file for vnc easily without root privilidges and the vnc man pages say that the password can be obtained from that, how is this done? Is additional software needed?

Just to clarify this is not a malicious act, I already have a list of all the passwords including root and vnc password but I'm trying to test the security and approach the tech support people with the results, 

Regards
Mark

---

### Post by Cheesemill on 2012-04-22
[http://www.hideaway.net/2007/07/stating-obvious-vnc-is-insecure_09.html](http://www.hideaway.net/2007/07/stating-obvious-vnc-is-insecure_09.html)

---

### Post by jadtech on 2012-04-22
secure enough to keep honest thieves from taking things there not interested in ..

---

### Post by Dangertux on 2012-04-22
Don't use VNC. That's really all there is on that one. If VNC must be used (for some bizarre reason) bind it to localhost and use SSH with X Forwarding to connect to the machine then VNC in.

Hope this helps.

---

### Post by Habitual on 2012-04-22
> **CaptainMark said:**
> ...how secure it is from people with physical access to the machine, ....

Security Rule #1:
There is NO security without physical security.

---

### Post by Gremlinzzz on 2012-04-22
Total security 
unplug the computer:popcorn:

---

### Post by CaptainMark on 2012-04-23
Ha, yeah I figured this, this is what I want to change, it's not entirely my choice, I think the last two lines of the article cheesemill posted are what Im trying to prove here

---

