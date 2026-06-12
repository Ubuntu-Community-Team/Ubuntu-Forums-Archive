---
title: "Help with SSH Tunneling"
date: 2009-07-08
forum: General Help
---

### Post by champi0n on 2009-07-08
Basically from (workstation) I want to tunnel HTTP traffic via tunnel to (box1).

And then be able to tunnel from (box1) to (box2) so that (box2) is tunneled back to (workstation)

So for example. I tunnel to (box1) from (workstation).

(workstation) reports ip of "box1" when browsing

I tunnel from (box1) to (box2) while tunneled from (workstation) to (box1) already.

(workstation) reports ip of "box2" when browsing.

Make sense? Can anyone help me?
Thanks.

---

### Post by munky99999 on 2009-07-08
If you simply want your ip to appear like box 1. Why not just install a proxy on box 1? 

[http://en.wikipedia.org/wiki/Squid_web_proxy_cache](http://en.wikipedia.org/wiki/Squid_web_proxy_cache)

Ought to do that job.

---

### Post by t4thfavor on 2009-07-08
So what are you really trying to do? that sounds like alot of tunneling. I believe though that "gstm" would help you keep some of this stuff straight.

But I agree there are plenty of Proxy packages that will make it appear that traffic is coming from somewhere else. As noted above Squid comes to mind. Its not super easy to configure, but you only need to do it once.

---

### Post by champi0n on 2009-07-17
Well i'm only able to access a specific external IP from within the current network.

So I can only SSH into that box. But from that box I want to ssh into the 2nd box and be able to browse to a web interface (which only allows access from the network of the 2nd box).

So i need my tunnel to be able to do that.

for instance if i use foxy proxy i can use local port 5555 and run the ssh command to the first box.

ssh user@box1 -D5555

and then in the browser i'm "browsing" from box1.

but what I want to do is ssh from that box to box2 and have box2 traffic work as if i ssh'd right to box2 in the first place.

make sense?

---

### Post by LightningCrash on 2009-07-17
> **champi0n said:**
> Well i'm only able to access a specific external IP from within the current network.

So I can only SSH into that box. But from that box I want to ssh into the 2nd box and be able to browse to a web interface (which only allows access from the network of the 2nd box).

So i need my tunnel to be able to do that.

for instance if i use foxy proxy i can use local port 5555 and run the ssh command to the first box.

ssh user@box1 -D5555

and then in the browser i'm "browsing" from box1.

but what I want to do is ssh from that box to box2 and have box2 traffic work as if i ssh'd right to box2 in the first place.

make sense?

Tsocks might help.

ssh user@box1 -D5555
edit tsocks.conf to proxy access to box2 via box1
tsocks ssh box2 -D6666

point firefox to socks localhost:6666 (or tsocks firefox)

---

