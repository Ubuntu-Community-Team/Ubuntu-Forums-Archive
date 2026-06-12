---
title: "Remote Desktop and openSSH confusion newbie"
date: 2010-08-22
forum: General Help
---

### Post by drillerccg on 2010-08-22
Hi, newbie here but quick learner. Using Lucid

Set up my mom with Ubuntu and want to be able to connect to her computer remotely to help her out when she has a question. I did some search and it seems that everyone recommends using openSSH. I used this link 

[http://www.jonathanmoeller.com/screed/?p=1585](http://www.jonathanmoeller.com/screed/?p=1585)

to install it on my mom's computer (changed the port to 16 instead of 22 and added those lines he suggested to the end of that file). Now what? I can't seem to find any instruction to connect the two computers. Looking around I also found:

1- Remote Desktop Viewer 
2- Terminal Server Client 

under applications/internet and

3- Remote Desktop under preferences

It looks like I can use those to connect also. But are they related to openSSH? Should I uninstall openSSH and use 1,2 or 3? Which is moe secure or are they the same. TIA

---

### Post by drillerccg on 2010-08-23
anyone?

---

### Post by earthpigg on 2010-08-23
hi,

ssh is plenty secure, and what i use to manager my own mom's computer.

```
ssh -p 16 username@123.123.123.123
```

where 123.123.123.123 is her ip address.

you will need to have enabled port forwarding on her router for port 16.

---

### Post by drillerccg on 2010-08-23
> **earthpigg said:**
> hi,

ssh is plenty secure, and what i use to manager my own mom's computer.

```
ssh -p 16 username@123.123.123.123
```where 123.123.123.123 is her ip address.

you will need to have enabled port forwarding on her router for port 16.

 I guess what I'm asking is if I use the protocols  found under Application/Internet menu (terminal server client and remote desktop viewer), am I using SSH by default or do I have to setup ssh separately?

---

### Post by drillerccg on 2010-08-23
I guess what I'm asking is if I use the protocols  found under  Application/Internet menu (terminal server client and remote desktop  viewer), am I using SSH by default or do I have to setup ssh separately?

Also, once connected, would a GUI open up and I see her desktop or do I have to fire up something else to use through the open SSH to see her desktop? Any simple guide on this?

---

### Post by earthpigg on 2010-08-23
> **drillerccg said:**
> Also, once connected, would a GUI open up and I see her desktop or do I have to fire up something else to use through the open SSH to see her desktop? Any simple guide on this?

if you want to see her graphical desktop, you want to use the remote desktop viewer tool. i've never used it, unfortunately, so cannot offer specific advice on it's use.

---

