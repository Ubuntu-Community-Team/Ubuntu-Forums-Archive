---
title: "where to start on network issues (VNC+SSH)"
date: 2010-02-10
forum: General Help
---

### Post by PermNoob on 2010-02-10
ok so I don't really know where to start with this one.   I started playing with SSH to move files between two computers on my network.  Both are running ubuntu, all up to date.  I can see the other machine fine, and I tried to copy a few gigs using SCP, and it ran at 2mbs, then staalled out, ran for a split second, stalled, lather repeat for about 600 megs before I gave up and pulled the plug. the pause is about 25 seconds, and the bursts are maybe a second, then the xfer rate drops steadily to zero, i assume as its an average not an actual transfer speed.  I then tried VNC viewer to just compare, and it takes maybe a full 9 seconds to pan down the whole screen, using -encodings tight
I am not sure where to start with this problem, port forwarding popped into my head, but I really am clueless as to how to procede.  Let me know if this is the wrong forum for this question.
not looking to get my hand held all the way through, but if someone could give me a dircetion to attack this problem from, and point me to a resource I will happily try and do it myself.
the router is the one I got with verizon FIOS, model 	MI424WR-GEN2

---

### Post by bbqau on 2010-02-10
if you are planning on transferring files from one to the other why not install and configure ftp ? It is a simple solution to the file transferring, once the files are there then simply SSH into the home server and move files via terminal commands.

---

### Post by PermNoob on 2010-02-10
aside from the fact it didn't work properly, SCP is so simple I really like it.  If I can't make it work right, I will just try something new, but I don't want to quit too early.

---

