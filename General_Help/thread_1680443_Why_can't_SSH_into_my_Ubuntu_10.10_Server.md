---
title: "Why can't SSH into my Ubuntu 10.10 Server?"
date: 2011-02-02
forum: General Help
---

### Post by reddogut on 2011-02-02
So maybe someone can point me into the right direction.
 
I installed openssh-client on my Ubuntu server and Putty on my Windows laptop. When at home I can SSH into my server just fine. But I also want to be able to SSH into my server from work (the internet).
 
So I forwarded port 22 on my Linksys/Cisco router to the server and then I start Putty and try to SSH in by putting in the IP address my router/modem is pulling from my ISP. But the connection times out everytime.
 
I know I can reach my router from the internet... I can log right into it. But either it isn't forwarding the port or the server isn't accepting it.
 
Any ideas?

---

### Post by montini on 2011-02-02
I think you should install openssh-server.

---

### Post by Jlayman on 2011-02-02
i am a moron

---

### Post by papibe on 2011-02-02
A few thoughts:

Most ISPs lease you an IP address that may change over time (around 24hrs). To simplify this problem, I would recommend subscribing to a Dynamic DNS service (like DynDNS), and installing the ddclient on your server.

Since the port 22 is a very well known port for ssh. I would suggest changing it for a higher number for several reasons:
[LIST=1]
[*]Security. So your home server and network would be a little more hidden.
[*]Your IT team at work may be blocking the port (not necesarily because they want to prevent you from sshing)
[*]Your ISP may be blocking incoming connections using that port. A rare case, but not unlikely.
[/LIST]

Also, make sure your server has always the same local IP address, either by setting it as static, or configuring your router so it gives the server always the same IP (reserve).

I hope it helps,
Regards.

---

