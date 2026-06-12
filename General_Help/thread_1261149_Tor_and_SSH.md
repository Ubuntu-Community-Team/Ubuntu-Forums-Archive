---
title: "Tor and SSH"
date: 2009-09-08
forum: General Help
---

### Post by hwttdz on 2009-09-08
So really out of curiosity more than anything else I've been playing with tor.  I've got it set up with firefox correctly, however it either doesn't seem to be working or doesn't do what I expect with ssh.  

So if I'm at host1, and I'm connecting to host2, I get a "last login from host1" every time I try.  I figured I'd get a "last login from randomhost"?  Am I missing something? Do I need to do a command other than 

ssh user@host2 ?

---

### Post by ckonestroh on 2009-09-08
This doesn't make sense what your saying...

1. two computers are not going to connect if one is set to run under ssh its a protocol....

2. Is one of these computers a server??? if not why would it put out a randomhost... also are your directing it to connect to one computer???


Is this for a college course?????

---

### Post by hwttdz on 2009-09-08
I'm not sure I understand what you mean "two computers are not going to connect if one is set to run under ssh its a protocol...." 

Well I have no problem logging in to host2 from host1 using ssh. I'm just working on getting the tor part working.  

2) Well yes the computer I'm connecting to is running an ssh server (otherwise connecting to it through ssh would go markedly less well).  

2b) I expect to see "last login from randomhost" because when I log in through tor, I expect tor to route the traffic through a randomly selected proxy, so host2 would see traffic as coming from randomhost.  

2c) "Am I missing something?" We're clearly not on the same page. 

3) "Is this for a college course", nope as stated above this is just for curiousity sake. Both machines are mine, and I know who's logging into either, so the whole anonymous aspect of tor is not exactly functional in this case.  My goal is to scramble ssh connections so that I cannot determine where I connected from the last time I logged in.

---

### Post by cariboo on 2009-09-08
Tor is used for privacy on the internet, ssh is a totally different protocol, the only way you might see, a randomhost is if you access the second computer remotely from outside your home network, but I really doubt it.

---

### Post by hwttdz on 2009-09-08
Just because ssh is a different protocol doesn't mean that it can't use tor as a proxy, in much the same way that http is a protocol and firefox is able to use tor as a proxy (this part is working).  I'm just looking for a way to use tor to randomize ssh connections.

So I am accessing host2 from a different network.  But it shouldn't make a difference so long as the traffic leaves the local network.

I imagine
host1 -> tor -> randomhost -> host2 (here tor could send data to a non-local network proxy even if host1 and host2 are on the same local network)
right now I get
host1 -> host2

---

