---
title: "ADS/Dynamic DNS"
date: 2006-03-27
forum: General Help
---

### Post by Charlatat on 2006-03-27
Set up AD in a home/test environment and would like to experiment with Linux operability.  I'm a bit of a noob, so obviously, its going a bit slow.  One particular question was:  How do you get a Linux client to automatically update DNS?  The DNS box is a W2k3 member server and is configured to allow nonsecure updates.    Any suggestions?  Thanks

---

### Post by Charlatat on 2006-04-06
Since I got no replies, I thought I'd post the answer myself...  After A LOT of digging, I found a reference to the NSUPDATE command.  All the systems I've found don't "automatically" update DNS (as was suggested by some) so I had to use this:

nsupdate -v
=> update add name.domain.com 86400 A 123.456.789.098
=> send
=> quit

I'm working on a way to make this execute automatically everytime dhclient is called.  Just a thought for those who may still be looking...

---

### Post by EdLesMann on 2007-12-11
I know this was posted over a year ago....
Anyway, thanks! This was exactly what I needed!

---

