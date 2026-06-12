---
title: "SSH acting odd"
date: 2011-01-22
forum: General Help
---

### Post by Pontiac on 2011-01-22
Hey all;

I have a really weird one.  This may be a putty issue, or it may be a config issue in Ubuntu. I've no idea who to blame. ;)

I have four machines involved in my little issue that has me scratching my head on where to even BEGIN to diagnose what is going on.

The computer I'm attempting to connect to (For identification purposes, I'll call it the main machine) is running a relatively new install of KUbuntu 10.04, stock install of openssh daemon.  ufw is disabled, firewalls are off, etc, and I can prove that later.

The machine acting odd is a Win XP 32 bit running Putty.  Haven't had a problem until this reload of the previously mentioned machine.

A Work machine that is running RedHad of some flavour.

A Virtual Machine running a headless setup of Ubunto 8.04.

Now that the introductions are over, here is a quick map of the machines that can successfully connect with.  My major problem is that I cannot get SSH (And ONLY SSH) to work between the XP machine and the main machine.

Work -> Main = Works
Work -> VM = Works
XP -> VM = Works
XP -> Main = Fails
XP -> VM -> Main = Works
Main -> Main = Works (IE: "ssh localhost")
VM -> Main = Works

When I try to get the XP machine to connect to the Main machine, I get an error with Putty saying:
"Server sent disconnect message
type 2(protocol error):
baad service request ssh-connection"

I've changed Putty to try using SSH Protocol 1 only, but it says the protocol isn't installed on the Main machine, which is true.  I've tried setting just 1, and it gives me the error, and I've tried setting it to "2 only" and it again comes up with the error.

I went into /var/log as root on the Main machine, and did a "tail -n0 -f *" and then tried to connect, but nothing relevant shows up.

As for the proof that the firewall is disabled, three of the machines are working with Synergy, I am able to swap between all three of the machines without a problem, I can get to WebAdmin from the XP machine to the Main machine, and I can open a Samba share from the XP machine to the Main machine without a problem.

This sounds like a protocol issue, but I can't see anything in WebAdmin that'll put me in the right direction.

Anyone have any thoughts?

---

### Post by tigerstripedcat on 2011-01-22
Well it seems to be the xp machine that is the problem.  I guess it could be the Main, but I doubt it.

1) Try something else aside from putty
2) if you have something like cygwin installed run it in verbose mode (ssh -v )?
3) You can always maybe run a live cd to prove to yourself it's the xp machine.

Also synergy is not a good test to show that your firewall is down, it is VERY good at broadcasting on port/protocols that, same with samba, you can have an open port in the firewall and still have the firewall up.  That said, I don't think many firewalls block port 22 outgoing.  But to be sure, just take your firewall software (windows or whatever) and just turn it off completely.

I start by trying something else other than putty, in the very least it may give you a different error that is a bit more informative.

---

### Post by hawkmage on 2011-01-22
I am not sure if PuTTY supports this option like openssh does but it is worth a try.  Use "-vv" command line option to have give verbose output.  I usually use this when trying to debug an ssh connection issue.

Also are you using a saved PuTTY profile for the connection?  If you are try creating a new one.  

Is the version of PuTTY recent?  I have see issues with an old version of PuTTY with some versions of OpenSSH and vice versa.  

Are you using certificate authentication?

---

### Post by djeikyb on 2011-01-22
I think you can get similar information to ssh -vvv by enabling ssh packet logging. See the manual:

[http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html#config-logging](http://the.earth.li/~sgtatham/putty/0.60/htmldoc/Chapter4.html#config-logging)

---

### Post by Don Barzini on 2011-01-22
> **Pontiac said:**
> This sounds like a protocol issue, but I can't see anything in WebAdmin that'll put me in the right direction.

Anyone have any thoughts?


It's a networking problem related to incompatible buffers.

Here is some reading for you and a possible solution....

[http://www.psc.edu/networking/projects/hpn-ssh/](http://www.psc.edu/networking/projects/hpn-ssh/)

[http://www.psc.edu/networking/projects/tcptune/](http://www.psc.edu/networking/projects/tcptune/)

[http://www.psc.edu/networking/projects/tcptune/#WindowsXP](http://www.psc.edu/networking/projects/tcptune/#WindowsXP)

[http://www.psc.edu/networking/projects/tcptune/#Linux](http://www.psc.edu/networking/projects/tcptune/#Linux)

---

