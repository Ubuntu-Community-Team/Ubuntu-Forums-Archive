---
title: "newbie need ssh help"
date: 2010-01-23
forum: General Help
---

### Post by morage_key_ring on 2010-01-23
Hi guys, 

been having some real trouble with ssh setup on my ubuntu 9.10. 

when i 'm testing for my ssh connection i typed in:

ssh localhost

but all i got back was read from socket failed: Connection reset by peer

And when i get on my macbook trying to connect i typed in:
ssh <user>@<ip>

and all I got back was:
connection closed by 192.168.xx.xx

can someone help?

---

### Post by denarced on 2010-01-23
sounds like a firewall .. maybe

---

### Post by denarced on 2010-01-23
Or you don't have ssh server .. maybe

---

### Post by n0dix on 2010-01-23
Did you start the daemon??

---

### Post by jamesisin on 2010-01-23
You have to enable ssh before you will be able to ssh into a machine.  By default Ubuntu ships with ssh disabled (even the server version).

I think all you'll need to do is edit your ssh config file:

gksudo gedit /etc/ssh/sshd_config

Find this:

PermitRootLogin no

Can you guess?  Change no to yes...

Then this:

sudo /etc/init.d/ssh restart

Should be good to go.

---

### Post by zollie on 2010-01-23
post the output of **service ssh status**:
```
$ service ssh status
 * sshd is running

```

---

### Post by blackened on 2010-01-23
> **jamesisin said:**
> You have to enable ssh before you will be able to ssh into a machine.  By default Ubuntu ships with ssh disabled (even the server version).

I think all you'll need to do is edit your ssh config file:

gksudo gedit /etc/ssh/sshd_config

Find this:

PermitRootLogin no

Can you guess?  Change no to yes...

Then this:

sudo /etc/init.d/ssh restart

Should be good to go.

Yeah, don't do this. You absolutely do not need to enable PermitRootLogin in order to use ssh.

As mentioned already, check that you have openssh-server installed and check that the service is running.

There are tons of great guides on both the web and these forums to help you get ssh going. Start there.

---

### Post by jamesisin on 2010-01-23
Maybe there is a different solution then, because I don't have either ssh-server or openssh-server on my machines.

$ which openssh-server
$ which ssh-server
$ clear

(I am able to ssh if I change that entry to no so there is clearly some other way to turn ssh on for a fresh installation.)

---

### Post by jamesisin on 2010-01-23
Odd.  Synaptic *does* list openssh-server.  Which, you failed me!

I concede.  I think that is made yes by default then.  You should check yours to make sure it is changed to no.  (I tested sudo and sudo does work with this set to no.)

---

### Post by blackened on 2010-01-23
Ideally, since the root user is disabled by default on a stock server or desktop install, then enabling PermitRootLogin should have no effect. That said, if you do not lose functionity with it disabled, why create a potential security liability?

---

### Post by d3v1150m471c on 2010-01-23
>  /etc/ssh/sshd_config
are you sure this is right? I tried opening that with gedit and got a blank .txt. On second thought you were probably correct about it not being installed by default.

---

### Post by jamesisin on 2010-01-23
> **blackened said:**
> Ideally, since the root user is disabled by default on a stock server or desktop install, then enabling PermitRootLogin should have no effect. That said, if you do not lose functionity with it disabled, why create a potential security liability?

Agreed.  That's why I conceded above.  I did change it to no.  Sorry if that wasn't clear above.

> **d3v1150m471c said:**
> are you sure this is right? I tried opening that with gedit and got a blank .txt. On second thought you were probably correct about it not being installed by default.

I checked on a machine that hasn't been ssh enabled and that file does exist and in that location.  (It has much less text, however.)  I only meant that it was set to yes by default and that ssh was not enabled (read: openssh-server was not installed) by default.

---

### Post by d3v1150m471c on 2010-01-23
That file does not exist on my machine. I'm not worried about it because I don't use ssh

---

### Post by jamesisin on 2010-01-23
Oh, not suggesting you should worry.  Just a curious soul.  Which Ubu ya running?

---

### Post by d3v1150m471c on 2010-01-23
I have 9.10 and Lucid. Neither of them have it.

---

