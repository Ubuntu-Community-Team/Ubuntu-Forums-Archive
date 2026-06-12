---
title: "problems with ufw"
date: 2010-06-04
forum: General Help
---

### Post by cuf99 on 2010-06-04
I've been having some problems with ufw on ubuntu 10.04.  I didn't realize until just recently that the problem was ufw.  I couldn't access gmail, or yahoo, or delicious, or gwibber -- or really most things that required logging in -- properly.

Then I noticed that disabling ufw made all the problems go away.  But I'd like to have a firewall in place.  I can't figure out what rules I need to put in ufw so that I can keep ufw active.  I enabled http, https, imap, a few other ports too -- but nothing seemed to do the trick.  So long as ufw was active, I couldn't access a bunch of sites.  Anyone have any ideas?

---

### Post by hansdown on 2010-06-04
Welcome to the forum cuf99.

I don't know a lot about UFW, but I can give you a useful link,

[https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html)

I hope this helps.

---

### Post by wojox on 2010-06-04
If you have a router just use that as your Firewall.

---

### Post by cuf99 on 2010-06-04
Thank you for the quick reponses.  I have seen the reference pages for ufw, and I've seen the wikipedia page for which port number that corresponds to what.  I have tried allowing lots of different service.  I'm really surprised more people aren't having this issue.  Do most people not run ufw?  I thought it is enabled by default now.

Will my router really work well enough?  I remember going to [www.grc.com](www.grc.com) once to check my system, and it made a difference whether I had ufw running or not.

---

### Post by wojox on 2010-06-04
Yes your router will work. You should be able to Port Forward any application if needed.

---

### Post by hansdown on 2010-06-04
> **cuf99 said:**
> Thank you for the quick reponses.  I have seen the reference pages for ufw, and I've seen the wikipedia page for which port number that corresponds to what.  I have tried allowing lots of different service.  I'm really surprised more people aren't having this issue.  Do most people not run ufw?  I thought it is enabled by default now.

Will my router really work well enough?  I remember going to [www.grc.com](www.grc.com) once to check my system, and it made a difference whether I had ufw running or not.

Most users don't use ufw.

They probably should, though.

---

### Post by cuf99 on 2010-06-04
Well, I went to a few different sites to test my router's firewall, and it passes (and all I ever did was check a box on its configuration page for it to be a firewall when I first got it -- I guess it's magic I don't need to know about).  BUT, if I ever take the laptop anywhere I'll want a personal firewall in place.   Plus, I feel like the software firewall must be important -- Windows will forever bother you about its importance if you don't have one.

Anyway, I think it's a big deal if ufw isn't working properly.  If it's just that I'm missing something in how to use it, it's still a big deal -- but just for me, and I'd like to know what I'm doing wrong.

I'd use iptables directly if I knew how -- but it seems very complicated.

---

### Post by wojox on 2010-06-04
Have you tried looking here [UFW]("https://help.ubuntu.com/community/UFW")

Good point about the laptop. I never thought of that for mine. Will have to install UFW as well.

---

### Post by hansdown on 2010-06-04
> **wojox said:**
> Have you tried looking here [UFW]("https://help.ubuntu.com/community/UFW")

Good point about the laptop. I never thought of that for mine. Will have to install UFW as well.

It is installed, already.

It just needs to be enabled.

[https://help.ubuntu.com/9.04/serverguide/C/firewall.html](https://help.ubuntu.com/9.04/serverguide/C/firewall.html)

---

### Post by cuf99 on 2010-06-04
I've seen the ufw help pages.  If you all are going to enable it, you can let me know what luck you have trying to send an email from yahoo or gmail.  If you come up with the right port to allow, let me know.  I suspect something is not quite right with ufw.  I remember it being very easy to use on past versions of ubuntu.

---

### Post by hansdown on 2010-06-05
Wow! Thanks for pointing that out cuf99.

I should probably practice what I preach.

Stand by for further details.

---

### Post by cuf99 on 2010-06-05
Standing by then.  Thank you again for devoting your time to this.  It's been baffling for me.

---

### Post by hansdown on 2010-06-06
There is gufw.

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

I don't know if that is any easier, though.

---

### Post by bodhi.zazen on 2010-06-06
How did you configure ufw ?

The default settings should not cause the problems you describe.

Are you trying to block outbound connections ? That is more difficult.

---

### Post by cuf99 on 2010-06-06
At first I didn't configure ufw at all.  I just enabled it.  Then I tried to allow more services to see if I could open gmail messages with firefox, etc.  I tried sudo ufw allow http, sudo ufw allow https, sudo ufw allow imap --maybe other things too.  It didn't matter.  Gmail, yahoo, etc did not work right.  Once I disabled ufw, everything worked fine.  (Well, not quite everything.  I'm having problems with nfs too, but that's a different story.  Everything on the web works fine.)  I'd like to be able to enable ufw again, and still be able to use web based email.

---

