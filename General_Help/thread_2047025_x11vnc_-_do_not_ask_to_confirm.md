---
title: "x11vnc - do not ask to confirm"
date: 2012-08-24
forum: General Help
---

### Post by StormyRain on 2012-08-24
Hi all,

After I establish an SSH tunnel (using Putty) from my Windows machine at work and then try to connect using tightvncviewer to my ubuntu 12.04 machine at home all I get is a black screen. Meanwhile the client machine pops up a message asking to "allow" or "refuse" my connection. And that's it, I get stuck there and am unable to connect remotley.

What's interesting is that if I try to connect to the same machine from another machine at home i.e. over LAN (without the need for SSH) it connects without asking me to confirm the connection.

Can anyone please help? It seems useless to me to have to be there to allow myself to connect when the whole point is so I can manage it without being there :/ - surely there is a way to force auto-accept?

Thank you all in advance

---

### Post by Old_Grey_Wolf on 2012-08-24
I'm not sure this is the problem you have.

Have you added the work machine using hosts.allow in the iptables?

Googling on *hosts.allow iptables* may give you some ideas.

---

### Post by StormyRain on 2012-08-25
> **Old_Gray_Wolf said:**
> I'm not sure this is the problem you have.

Have you added the work machine using hosts.allow in the iptables?

Googling on *hosts.allow iptables* may give you some ideas.

Thanks gray wolf, but unfortunately it didn't help. I even allowed (temporairly as a test) ALL and still no joy.

Any one else have any ideas or any shell scripts they use to get x11vnc running that they'd like to share? Thank you

---

### Post by steeldriver on 2012-08-25
What did you do on the ubuntu end of things to configure / invoke the x11vnc server? can you post your x11vnc command line?

Have you tried connecting on the LAN *with* ssh tunneling?

---

### Post by StormyRain on 2012-08-25
> **steeldriver said:**
> What did you do on the ubuntu end of things to configure / invoke the x11vnc server? can you post your x11vnc command line?

Have you tried connecting on the LAN *with* ssh tunneling?

Hey guys, thank you for all your help but it seems I was being stupid, I figured out what the problem was. It's very good of you to mention SSH over LAN steeldriver. I actually tried that earlier and was having issues which led me to think that the problem was my SSH configuration and not x11vnc (if only your reply came sooner! ;) ) 

The image below shows the option that needs to be enabled in Putty, which I neglected to enable initially. This has been tested from work and over LAN and it now works flawlessly :) 

Many, many thanks for taking the time to respond, this community is so great.

[[img]http://s13.postimage.org/t3sg83ftf/Config.jpg[/img]](http://postimage.org/image/t3sg83ftf/)

I'd like to mark this thread as resolved, but not sure how to do this, should I just edit the title?

EDIT: nevermind, I've marked it as resolved.. hmm I really should go poking around more before asking! ;)

---

