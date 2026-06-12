---
title: "Help with port forwarding."
date: 2011-12-07
forum: General Help
---

### Post by Mr. ViC on 2011-12-07
Hey there, I was hoping that someone could help me out with port forwarding.

So, the problem is this filter and firewall that my university has, I cannot browse on a whole number of websites (many of them have nothing wrong/ilegal), can't play WoW, can't access Steam, it's damn annoying. So I heard that port forwarding or HTTP tunelling could work. Problem is, I'm a n00b with this, and I do not know much about it.

I have tried with something called AutoTunel GG (on Windows), and it worked, got it from here:

```
http://www.artofping.com/autotunnel-gg-pricing.php
```

Problem is that this is not free.

So a friend told me that I should set up an SSH client on my PC, and then a client on my laptop and forward those ports to my PC and be able to get rid of the filter.

So I'm thinking of installing an SSH server on my Ubuntu desktop at home so I can somehow access it from my Windows laptop in school and be able to browse with freedom.

Can anyone give me a hand here on what should I do? Also, I use OpenDNS, if that's worth knowing for anything.

Thanks in advance.

---

### Post by Mr. ViC on 2011-12-07
Update:

Ok, so I installed the SSH server on the Ubuntu machine and PuTTy on the Windows one. Connected, and seems it worked:

[img]http://i.imgur.com/Dq4qk.jpg[/img]

I just need help now with the port forwarding...

---

### Post by Lars Noodén on 2011-12-07
You don't need to forward ports for this.  It is better to run a [SOCKS proxy](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding#Dynamic_Port_Forwarding).  You'll have to look around how to do dynamic port forwarding (SOCKS proxy) with PuTTY, but it's doable.

(Note that the example there uses (-C) for compression, but depending on the power of your processor, it might be faster without compression.)

---

