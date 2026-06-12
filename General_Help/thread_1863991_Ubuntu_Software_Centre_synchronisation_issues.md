---
title: "Ubuntu Software Centre synchronisation issues"
date: 2011-10-18
forum: General Help
---

### Post by Dr3Daemon on 2011-10-18
Hi,

I am trying to use the new Ubuntu Software Centre synchronisation feature to sync between a couple a machines.

However I think I have created a new Software Centre account on one, and re-used my Launchpad account on the other. I've certainly done something wrong.

I'd like to reset the account info so I can use the same account on both machines, but I can't find out where / how to change this. Stopping synchronising and then starting again doesn't do anything and a quick grep for my e-mail doesn't turn up anything promising in the .config directory etc.

Any ideas?

---

### Post by Dr3Daemon on 2011-10-18
OK, I fixed the first problem - just go to Passwords and Keys, find Ubuntu Software Centre and delete the password. 

Next go to login.ubuntu.com and if (like I did) you have multiple entries under Applications for "Ubuntu Software Center @ machine_name", delete all of them.

Then trying to sync will ask for a username / password combo and you can start again.

Finally I had to use the "new" account I had created accidentally. If I used my existing Launchpad account I could login but I guess there was no "backend" Software Centre account.

Anyway, all working now - hope that helps someone else

---

