---
title: "SSH only allow some IP's to connect?"
date: 2006-02-21
forum: General Help
---

### Post by ianfilms on 2006-02-21
Ok, this is a really strange issue, and it is bugging me beyond belief. I have installed Breezy before, and not run into this situation... with the same network setup. So something must be wrong... anyway, to the problem.

I have sshd installed and can connect with putty through some computers, but not others. For example, I can connect through my wireless network, but not my local network. Well, SOME local IP's can connect (with the same subnet), but outside of that subnet, the local computer will get a connection refused error.

So what it boils down to, is xxx.xxx.111.xxx can connect locally, xxx.xxx.222.xxx cannot connect locally. Remote IP's can (which are completely different from, while being on the same network) Wireless computers with completely different IP's can as well. I asked a few friends located in different places throughout the country to see if they would get even a login prompt with putty, and they all did. It just seems that the desktop computers I'm using (LAN - Different subnet - as in the 222 example above) are being refused.

I have made sure that ALL is set in my allow list. I have tried removing and re-installing it from scratch numerous times, with the same results. Hopefully this makes sense, because my explanation seems nonsensical when I read it.

Does anybody have any suggestions? I have searched for almost 2 days now, and I cannot come up with a similar topic...

---

### Post by ianfilms on 2006-02-21
Also, I can VNC into it from any computer without a problem, so I really doubt it's a networking issue (as far as reaching the machine from anywhere is concerned).

---

### Post by eyes_on_the_net on 2006-05-03
I had the same issue with a RH 4 install.  I found this suggestion on linuxquestions.org.  Pablo suggested that the firewall was the cause and to try these commands

iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

I had already tried the -F option and it still would not let putty in from different subnet.  Adding the other options did work though. The next step is to understand the firewall and add a rule for ssh.  I hope this helps.

---

### Post by ianfilms on 2006-05-03
It's probably a network issue/problem, because different distro's cause the same result. :(

I doubt they all have the same firewall settings that are disallowing SSH access through specific subnets... but I guess it's possible. I'll try it anyway, and let you know what happens. Thank you :)

---

