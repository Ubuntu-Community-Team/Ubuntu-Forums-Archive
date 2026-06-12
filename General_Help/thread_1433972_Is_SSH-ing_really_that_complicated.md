---
title: "Is SSH-ing really that complicated?"
date: 2010-03-19
forum: General Help
---

### Post by blur xc on 2010-03-19
If not, can someone point me to a idiots guide to SSH?  All I want to do- just as an experiment for my own education, is to SSH into command line only Ubuntu install from my Crunchbang VM.  I just want to log in and run some commands to play around.  Once I get grips with that, I'll stat looking at doing the whole remote desktop thing.  It would be nice to log into my home computer to access my personal files from work.

I have both systems up and running, installed open ssh on both of them - but after that the instructions start getting really complicated.  I know next to nothing about networking once they start off on ports and junk, as if I knew what those were, they might as well be written in Chinese.

Thanks
BM

---

### Post by Iowan on 2010-03-19
I presume you've seen the SSH help pages on [https://help.ubuntu.com/]("https://help.ubuntu.com/") so I won't post links (unless you ask). When I built my last server (hardy), I had it install SSH initially - it seemed to work fine with this workstation... but, then, I'm not running a VM.
You will probably want to set the machine up for local access first. If/when that works, you can port-forward to it from your router (and set up dyndns/no-ip account).

---

### Post by blur xc on 2010-03-19
> **Iowan said:**
> I presume you've seen the SSH help pages on [https://help.ubuntu.com/](https://help.ubuntu.com/) so I won't post links (unless you ask). When I built my last server (hardy), I had it install SSH initially - it seemed to work fine with this workstation... but, then, I'm not running a VM.
You will probably want to set the machine up for local access first. If/when that works, you can port-forward to it from your router (and set up dyndns/no-ip account).

Actually, I did look at that.  I have those pages printed out right in front of me...  but, I did just look again and found this [https://help.ubuntu.com/9.10/serverguide/C/serverguide.pdf](https://help.ubuntu.com/9.10/serverguide/C/serverguide.pdf) which has a section on remote administration.  

btw- case in point- I'm reading your post along and once you get to "port-forward" etc... etc.., I'm lost.  I have no idea what port forwarding is, or what a port even is, let alone a dyndns....deal acount thingy...

What I'm afraid of doing, is starting this out, not knowing fully what I'm doing, and leaving my system open to be hacked.  That would make me very unhappy.  

Eventually I intend to build a home file/proxy server.  I just have a steep learning curve in front of me.

Thanks,
BM

---

### Post by Girya on 2010-03-19
try sshing into your own machine instead of a vm. 

```
ssh 127.0.0.1
```

if you have open ssh server running you'll get a response about the host not being able to be verified and do you want to continue type

```
yes
```

and you will have ssh'ed into your own system after entering your password.

---

### Post by Girya on 2010-03-19
as far as leaving your system open to hacking through ssh. if you are connected to the internet through a router you are probably ok the ssh port 22 is not open by default on any router I've seen. but if you want to be sure you can remove the link to start ssh by running **[COLOR="Red"]update-rc.d[/COLOR]**

```
sudo update-rc.d -f ssh remove
``` 

and rebooting.

this will leave open ssh installed on your system but it won't start on startup. 

to reinstall the init srcipt run 

 ```
update-rc.d ssh defaults
```

---

### Post by 2hot6ft2 on 2010-03-19
Setting up SSH and securing it is not that hard normally. The VM part I don't know anything about. I did a how to for ubuntu to ubuntu by SSH and FreeNX which is in my sig. below. Would it be an idiots guide since I wrote it?

For learning about SSH and port forwarding and assigning static IP Addresses here are some links:

Installing OpenSSH
[http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html](http://help.ubuntu.com/9.10/serverguide/C/openssh-server.html)

I wanted stronger keys so I followed this for the keys
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Strong Passwords
[http://help.ubuntu.com/community/StrongPasswords](http://help.ubuntu.com/community/StrongPasswords)

DD-WRT Port Forwarding
[http://www.dd-wrt.com/wiki/index.php/Port_Forwarding](http://www.dd-wrt.com/wiki/index.php/Port_Forwarding)

DD-WRT Static IP Address Leases
[http://www.dd-wrt.com/wiki/index.php/Static_DHCP](http://www.dd-wrt.com/wiki/index.php/Static_DHCP)

And for finding a non-standard port to run SSH on:
Port Lists
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)
[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)
[http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html](http://www.neohapsis.com/neolabs/neo-ports/neo-ports.html).

P.S. When you don't need or want the SSH Server running you can stop and start it easily with:
How to start/stop/restart the SSH Server
```
sudo /etc/init.d/ssh stop
```

(Replace stop by start for starting it again)

---

### Post by blur xc on 2010-03-19
Thanks for all the info- I'll do some reading and see what I can do.  Maybe I'll try ssh-ing into my desktop from my wife's netbook...

That might actually be useful to have set up, as we will be going on a week long vacation in May, and will most likely bring the netbook to dump photos on to.

BM

---

