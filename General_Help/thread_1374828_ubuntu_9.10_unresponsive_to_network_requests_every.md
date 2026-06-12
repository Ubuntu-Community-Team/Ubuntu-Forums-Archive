---
title: "ubuntu 9.10 unresponsive to network requests every couple days"
date: 2010-01-07
forum: General Help
---

### Post by terevos on 2010-01-07
So I upgraded to Mythbuntu 9.10 from 8.10 and things went fairly well. No major problems during the upgrade.

The system is just a mythbackend server. The only things that access it are for myth and for the smb mounts for mythtv.

The Problem:
Every couple days, the system stops responding to network traffic. No myth connection, no smb, no pings even. All I have to do is wiggle the mouse on the system and everything comes back up instantly. I noticed that after it comes back up, the time is off by hours (maybe for how many it's been sleeping for).

Anyone have any ideas for what might be happening?

Thanks!

---

### Post by terevos on 2010-01-09
Found a solution. Looks like there's a bug in Ubuntu 9.10 with power management.

Here's the workaround: 
[http://ubuntuforums.org/showpost.php?p=8258628&postcount=6](http://ubuntuforums.org/showpost.php?p=8258628&postcount=6)

---

