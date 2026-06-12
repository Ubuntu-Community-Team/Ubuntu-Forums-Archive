---
title: "Evolution freezes during fethching email"
date: 2009-08-19
forum: General Help
---

### Post by Stoneface on 2009-08-19
During fetching Email Evolution freezes every time there is a network time-out. It sort of gets into a loop. I read here:[https://launchpad.net/ubuntu/+source/evolution-data-server](https://launchpad.net/ubuntu/+source/evolution-data-server) that 
#546444: Don't loop infinitely when the network connection is lost while
fetching a message.
was a low priority issue for Intrepid last year. But now I have the (sort of) the same issue using Jaunty Jackalope so I guess it has not been solved. Anybody any ideas about this?

---

### Post by webdebbyjoss on 2010-03-22
Hi, I have a same problem here.
Were you able to resolve this?

---

### Post by Stoneface on 2010-03-23
No, I have not. I use Mozilla Thunderbird for now as Evolution does not (yet) suit my needs.

---

### Post by Nelbomber on 2010-04-15
Is anyone still having this problem, because I am.  t seems the last post here was two years ago.  If I can't find a fix I will have to change email clients.

---

### Post by Stoneface on 2010-05-31
@ Nelbomber Did you have any luck figuring this out yet or did you switch email client?

---

### Post by Nelbomber on 2010-06-28
I did not :(

I may have to grab the source and try to figure it out.  It shouldn't be hard to change 'try forever' to 'try three times and throw an error'.  On the stack of projects it goes!

---

### Post by jwood1961 on 2010-09-08
I'm not sure if it is the same origin, but at some point in the last couple of weeks, presumably after an update, my Evolution (2.28.3 - in the core, with all updates applied) on Lucid Lynx has started freeze intermittently and temporarily.

It seems to be every 15 minutes or so, if I'm using Evolution, it will lock up - screen and keyboard becomes unresponsive (not seen in other applications) - and it remains that way for a few  seconds then comes back to life.

It does not appear to be fetching email many times when this occurs and I can't see it's a network problem as most of the time I'm connected by cable to my router and there are no signs of network going up and down from the router or from network manager.

Needless to say it's very annoying.

Anyone experiencing the same thing, or got any workarounds?

Kind Regards,
JW

---

### Post by spaceship9 on 2010-09-21
same problem for me on Lucid, bumping.
Occurs apparently randomly, for me at any rate. It's always "fetching email", but not every fetch email results in failure. I have to kill evolution and restart it, at which point it usually immediately fetches mail and works perfectly fine.

---

### Post by gandaran on 2010-09-21
could be a DNS problem, I remember once using the default ubuntu attributed DNS to my mobile internet connection would sometimes result during network overload evolution would have problems and I would have to force close Evolution.
try the OpenDNS 208.67.222.222, 208.67.220.220
if it is the DNS it will fix the issue.

---

### Post by spaceship9 on 2010-09-21
I am already using OpenDNS

---

### Post by jiex on 2010-09-23
Hi I have a similar - and another problem with Evolution. After using it for 12 months or so to access Gmail via IMAP, it suddenly stopped allowing emails to be sent via Gmail. Now, it will not even download them. The wheels just spin. i was receiving an authentication error message, but that is simply masking some other - possibly authentication, but more hidden - than I can discover.
I have tried all the different configurations for IMAP but it does not work. 
I think this problem commenced after and update.
I downloaded Kmail and it sent and received the mail OK. 
I wonder whether KDE wallet has anything to do with my Evolution issues?
I have absolutely no idea how to resolve this problem.

---

### Post by ricardisimo on 2010-09-30
I do so want Evolution to become my main mail option, but the truth is that it just cannot get out of its own way, and this freezing up (which has indeed intensified these past months) is just the latest problem. Is anyone following the bug tracking? Any word on a fix?

---

### Post by bearcubpa on 2010-11-01
I'm still having this issue. I find that after I run backup, Evolution fetches all my mail. Does anyone  have any idea why its doing this?  Thanks

---

