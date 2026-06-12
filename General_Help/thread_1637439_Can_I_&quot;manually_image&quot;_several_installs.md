---
title: "Can I &quot;manually image&quot; several installs?"
date: 2010-12-04
forum: General Help
---

### Post by jrowland on 2010-12-04
I bought 4 laptops for my 4 teenagers for christmas.  These came with Win7 Starter Edition, and I plan to fully wipe and load Ubuntu Desktop 10.10.  I will install these with a "Parents" account, and then create a "Kid" account (in their name, not "kid").

What I hope to do is get one laptop fully set up - permissions, software loaded, etc., and then somehow "transfer" the settings to the next laptop.  I assume that I would install the next latop, using the "parents" account to start.  Create the "Kid2" account, and then.... ?

Is there some way to copy all of the settings and what-software-is-installed-list to the next computer?  

Appreciate any advice and discussion.

---

### Post by The Cog on 2010-12-04
One neat way to do this I saw once was to use netcat.

On the destination machine, run a live CD, note its IP address that it comes up with. Then use these commands to listen on port 999 and copy everything received to the hard disk:
```
sudo -i
nc -l 999 > /dev/sda
```
Then on the machine you are copying the image from, use the commands (replace 1.2.3.4 with the target machine's address) to send the hard disk contents to the destination machine:
```
sudo -i
nc 1.2.3.4 999 < /dev/sda
```
The choice of port 999 was arbitrary, almost any number would do.

---

