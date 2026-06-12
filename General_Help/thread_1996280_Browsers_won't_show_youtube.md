---
title: "Browsers won't show youtube"
date: 2012-06-04
forum: General Help
---

### Post by porchrat on 2012-06-04
Kind of a strange problem.

I'm running Chrome and Firefox. For a few weeks now both browsers won't navigate to youtube.com. Even embedded stuff doesn't show. They basically just instantly tell me when I click a youtube link or enter the address in the address bar that the cannot reach the server.

I know the Internet connection is fine and I can reach youtube on other machines, just not this one. It is very strange.

Clearing all the history (cache and everything) doesn't seem to solve the problem.

Any idea what could be causing this?

---

### Post by carl4926 on 2012-06-04
Are you the administrator to your router/access point?
Could someone have blocked it?

---

### Post by inashdeen on 2012-06-04
May I suggest trying other browser too. just in case to make sure it is not a browser only problem

---

### Post by porchrat on 2012-06-04
> **carl4926 said:**
> Are you the administrator to your router/access point?
Could someone have blocked it?

There are a few routers between me and the Internet but I have access to all but one.

Still I doubt that the one I don't have admin access to is blocking youtube as other machines on the same IP range using the same routers can access youtube at the same time that my machine refuses to connect. :(



> **inashdeen said:**
> May I suggest trying other browser too. just in case to make sure it is not a browser only problem
I've tried Chrome and Firefox so far. Maybe I should try a 3rd one... Opera maybe. I looked at the software centre and frankly the browsers it is offering are garbage but I could fetch another one. Not a bad idea let me try that.

---

### Post by porchrat on 2012-06-04
OK downloaded Opera and tried to access youtube. Got similar response - network problem.

Chrome tells me it fails DNS lookup etc. etc.. Other folks here can access youtube no problem. Man this is annoying.

It must be something to do with my connection to the network... :(

---

### Post by porchrat on 2012-06-04
OK I have realised this problem goes far deeper than merely not getting to youtube.

I cannot get to the google linux repositories at all. dl.google.com does not resolve in apt.

I can't access support.google.com etc.

What on Earth is going on here?

---

### Post by dino99 on 2012-06-04
if the DNS cant be resolved, then :


 gksu gedit /etc/resolv.conf

and add : nameserver 8.8.8.8

then 

sudo service network-manager restart

---

### Post by porchrat on 2012-06-04
Followed the seemingly strange advice in this thread [here]("http://ubuntuforums.org/showthread.php?t=1174508") and it seems to work now. Youtube is accessible as is the Google Linux repository.

I'm still totally stumped as to why it was a DNS issue for my machine but no other on the same network. Crazy.

---

### Post by porchrat on 2012-06-04
> **dino99 said:**
> if the DNS cant be resolved, then :


 gksu gedit /etc/resolv.conf

and add : nameserver 8.8.8.8

then 

sudo service network-manager restart
I changed my DNS to 208.67.222.222 and my Search domains to 208.67.220.220.

It worked, though I have no idea why considering the rest of the machines on the exact same network don't seem to have a problem.

What would changing DNS to 8.8.8.8 do?

EDIT: oh wait I see that 8.8.8.8 is the public Google DNS while 208.67.222.222 is OpenDNS.

So now I know what the heck I did :P. I'm still stumped though... why was this required for my machine alone and not the others on the same network?

---

### Post by inashdeen on 2012-06-04
is this a shared network? just a theory, maybe something blocked it, maybe? Well, last time, i too had a similar problem, but it doesn't affect my linux only. it also affect my windows. yeah, changing to opendns fix my prob. well, that's for me. yours might be another issu

---

### Post by buzzingrobot on 2012-06-04
For unknown reasons, obviously, something blocked your access to some of Google's domains. (That includes youtube.) Do you use any browser extensions that are supposed to block ads or do some other kind of filtering?  If so, next time it happens you might disable them one by one to see what happens.

Also, changes to /etc/hosts could block access to specific domains.

---

### Post by porchrat on 2012-06-05
> **inashdeen said:**
> is this a shared network? just a theory, maybe something blocked it, maybe? Well, last time, i too had a similar problem, but it doesn't affect my linux only. it also affect my windows. yeah, changing to opendns fix my prob. well, that's for me. yours might be another issu
There are plenty of subnets on this network. I'm just in one corner of it :P. Everything from normal everyday network traffic to security camera feeds routes through.

Looks like their is another Linux machine here (it is very seldom used) that is exhibiting the same problem. Looks like it is confined to Linux though as the Windows machines don't have this problem. So weird...


> **buzzingrobot said:**
> For unknown reasons, obviously, something blocked your access to some of Google's domains. (That includes youtube.) Do you use any browser extensions that are supposed to block ads or do some other kind of filtering?  If so, next time it happens you might disable them one by one to see what happens.

Also, changes to /etc/hosts could block access to specific domains.
I use noscript and actually now that you mention it I think this issue is confined to the machines running noscript. I will have to take a look at that.

I checked /etc/hosts right in the beginning and it looked fine to me. Nothing but localhost info and some IPv6 stuff for allhosts etc..

Thanks for the info guys. I'm still stumped as to what exactly has caused this but at least you dudes have given me somewhere to start looking. The geek inside me just won't let this drop until I at least have an idea of what is going on :P.

---

