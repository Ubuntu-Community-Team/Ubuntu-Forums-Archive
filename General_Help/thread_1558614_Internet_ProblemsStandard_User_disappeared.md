---
title: "Internet Problems/Standard User disappeared"
date: 2010-08-22
forum: General Help
---

### Post by jrings on 2010-08-22
Since yesterday I had internet problems.
It might be connected to automated upgrades and a kernel upgrade to 2.6.31-22 (I run Ubuntu 9.10)

At first, while the connection was there, the name server lookups and pings all failed. I rebooted into an older kernel and once got internet access, but strangely while there was an error in the konsole, instead of my user name it said "I don't have a name yet" (or similar, translated from German).
So I thought it might be a user rights problem. And suddenly, my standard user also lost sudo privileges which had worked just minutes before.
I created a new user with admin rights to look at the log files. Logged in as the new user, the internet still didn't work. But I clicked around a bit with in the network manager (without changing anything), which triggered a reconnection - and now it works. I can also su into my standard user in the konsole and access my browser (with sux).
I'm not sure how authentication works on my machine, it is from my institute but I am abroad and anyway manage my machine myself. I looked into /etc/shadow and see the new user but not the default user. adduser on the default user tells me he exists. passwd tells me the default user is unknown.

Aany ideas how I can find out what's happened?

---

