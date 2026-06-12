---
title: "Apport not working?"
date: 2009-11-02
forum: General Help
---

### Post by ricardisimo on 2009-11-02
Would someone do me a favor try selecting Applications >> System Tools >> Report a problem... and tell me if anything happens. I'm trying to do just that - report a problem - and can't do so. Nothing happens at all when I click to launch apport.

Thanks for your help.

---

### Post by DavidFourer on 2009-11-06
I am trying to get apport to work also.  It worked in Jaunty.
> david@david-desktop:~$ sudo force_start=1 /etc/init.d/apport start
[sudo] password for david: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start apport
start: Job failed to startthen> 
david@david-desktop:~$ sudo service apport start
start: Job failed to start
david@david-desktop:~$ sudo start apport
start: Job failed to start

I don't have [COLOR="Red"]System Tools[/COLOR] in my applications menu so I don't know what you are referring to.  I did check synaptic package mgr to see that apport is installed.  Are there some new instructions for apport in Karmic?

---

### Post by ricardisimo on 2009-11-07
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/438847](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/438847)

---

