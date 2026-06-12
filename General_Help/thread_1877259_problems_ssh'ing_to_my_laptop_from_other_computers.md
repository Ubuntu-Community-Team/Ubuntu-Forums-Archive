---
title: "problems ssh'ing to my laptop from other computers"
date: 2011-11-07
forum: General Help
---

### Post by Mahkoe on 2011-11-07
I've looked everywhere for this and surprisingly came up with nothing. I managed to set up an "openssh-server" ssh server, but when I try to use ssh to log in ( ssh -p [myport] myusername@mylaptop'sIP ), it just shows a blinking cursor and after while says the connection timed out. I'm pretty sure it's because I don't know how to use ssh properly and probably didn't end up configuring it so I could reach it from anywhere (I can't even reach it using the above command from the mac on my network). I've read ssh tutorials, but they all assume I've been able to establish a connection and start talking about copying files and other uses, which would be nice to have access to. 

Anyway, a link to a good ssh tutorial or one of those oh-my-god-how-did-I-not-notice-thats would be nice. Also, I am running 10.10 64 bit and the mac has leopard if that has to do with anything. Thanks a lot

---

### Post by duke.tim on 2011-11-07
If you haven't done this yet
You might want to double check that any firewalls between the two computers are configured to accept ssh connections

It uses TCP port 22

---

### Post by Mahkoe on 2011-11-07
So you're saying that if my firewall allowed my port to go through, the above command should work?

---

### Post by duke.tim on 2011-11-07
It could be the problem, and would be fairly simple to fix if it is. It's worth a look.

---

