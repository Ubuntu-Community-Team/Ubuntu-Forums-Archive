---
title: "Log in as root"
date: 2010-09-12
forum: General Help
---

### Post by GrantStoner on 2010-09-12
How do I go about logging in as root during start up? Is there a way to change it permanently so I always log in as root? I like the way BackTrack does it how you always log in as root but can change the password.

---

### Post by kerry_s on 2010-09-12
not recommended, use the sudo/gksudo system for root tasks.

---

### Post by sikander3786 on 2010-09-12
> **sharathcshekhar said:**
> Here is your solution.
<snip>

PS: Do it at your own risk. For me, sudo will always do!
[COLOR="Red"]**NOT RECOMMENDED**[/COLOR]

Have you read the forums FAQs? Posting links for enabling root account is not allowed.

To the OP:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Sudo and gksu does everything for me. I have never needed to login as root in my 3 years connection with Ubuntu.

---

### Post by GrantStoner on 2010-09-12
> **kerry_s said:**
> not recommended, use the sudo/gksudo system for root tasks.
Duly noted. I've read this lots of places. And I am aware of the risks, however, It hasn't caused a problem for me yet. I always do ```
sudo su
```in the xTerm so I don't have to type ```
sudo
``` and then my password all the time. Thank you "sharathcshekhar" I am about to try that right now.

---

### Post by Elfy on 2010-09-12
Logging in as root is not advised, nor supported on the forum.
> 
Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.

Closed.

---

