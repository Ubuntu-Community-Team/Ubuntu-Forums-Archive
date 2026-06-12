---
title: "Beowulf cluster for game hosting?"
date: 2011-05-24
forum: General Help
---

### Post by Gakumerasara on 2011-05-24
I'm active in a low-tech internet game development community and am currently hosting several developers' games on a single decent-but-not-great computer. I have several more decent-but-not-great computers sitting around, and I was thinking of perhaps tying them together into a cluster. This would make server management a LOT easier for me than the current setup, which consists of one user account per developer and having to teach each new user how to use SSH and the Linux terminal.

But I'm here because, despite having read a great deal about clusters, I still have some unanswered questions. Since these are network games, I need to know exactly how a cluster handles open ports. If I forward port 12345 to the head node, and then host a game on slave node 101 using port 12345, will the outside world be able to access the game on the slave node? Is this the default configuration or would I need to do some fancy iptables manipulations on the head node as jobs are submitted? Is it possible to submit multiple jobs to a single node? (Most of these games only use about 5-10% CPU and 10-20% RAM.) Are there any other considerations for game hosting of this type? Thanks for your help!

---

