---
title: "Account synchronization between multiple Xubuntu 12.04 systems"
date: 2012-05-09
forum: General Help
---

### Post by Sijmen on 2012-05-09
Here's the challenge: there are three Xubuntu 12.04 systems on one network: one HTPC, one workstation and one notebook. On each machine there is an account named 'Simon' that is maintained individually. I would like however, to make one account on the workstation, and sync that account to all other systems, or to any new system that is added to the network. When I create a file-server for instance, I would like to be able to just push my account to that machine so I can log in with all my stuff already on the system.

I have tried file synchronization with SSH and Unison, but that is giving me headaches with privileges that need to be reset after every synchronization.

I've searched for 'user account synchronization' via DuckDuckGo and on this forum, but with no results. What do I need to set up this user account push service?

Thanks in advance.

---

### Post by papibe on 2012-05-09
Hi Sijmen.

Are you looking for 2-way, or just 1-way (mirror) synchronization?

Are you looking to set it up as background service, or just to run it when you need it?

Regards.

---

### Post by Sijmen on 2012-05-10
Hi papibe, I would like to have a background service that synchronizes all the machines. I wonder if one machine could run an occasional backup service for security sake.

---

### Post by papibe on 2012-05-10
Then I wouldn't give up on Unison just yet.

The best way to automate Unison is setting up public-key authentication with no passphrase (so the scripts can run unattended).

After setting the profiles, I would do the first sync using the GUI since you could see what's going on (the first time it will take a lot of time).

After that I would set up unison scripts on crontab.

Here's a [video]("http://www.youtube.com/watch?v=fOxTh6um1p0") tutorial that I found very useful. Although it is on OSX syncing to FreeNAS, it is practically the same thing on Linux.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Sijmen on 2012-08-20
So, if account pushing isn't possible, I could do it the other way around. I guess a private cloud is better solution. I haven't got the hardware to get that operational, so I'll stick with NFS shares and Unison. Thank you for the info papibe.

---

