---
title: "what is a single point of failure?"
date: 2012-06-18
forum: General Help
---

### Post by imachavel on 2012-06-18
in load balancing all requests into an incoming network, to distribute evenly to several servers, what is a single point of failure?
 
[http://forum.springsource.org/showthread.php?89785-Load-balancer-single-point-of-failure](http://forum.springsource.org/showthread.php?89785-Load-balancer-single-point-of-failure)
 
I know it's a somewhat simple question, that will probably result in a very complicated answer. But according to that article, it asks, how does apache front end work with a single point of failure? I'd imagine apache would be more back end, working on each individual node in a network, or at least each server in a network. I thought it was 
 
apache - web data base
my sql - query to web data base
php - interpreter
 
am I wrong? Ok, so let's say it's front end, which is something I have a hard time defining it as really. Either way, what does it have to do with a single point of failure? Thanks very much

---

### Post by hwttdz on 2012-06-18
They mean it in the sense that if that one thing breaks (failure at a single point) the whole system comes crashing down.  This is a bad thing, as when possible systems should be set up in such a way such that one thing going wrong doesn't break everything.

[http://en.wikipedia.org/wiki/Redundancy_%28engineering%29](http://en.wikipedia.org/wiki/Redundancy_%28engineering%29)

---

