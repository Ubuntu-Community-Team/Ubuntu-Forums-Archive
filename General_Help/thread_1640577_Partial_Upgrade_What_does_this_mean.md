---
title: "Partial Upgrade What does this mean ??"
date: 2010-12-08
forum: General Help
---

### Post by arunb on 2010-12-08
Hi,

What does partial upgrade mean ?? I am running 10.04, I just got a message asking for a partial upgrade, I donot want to change from 10.04, is it Ok to  cancel this message ??

thanks
a

---

### Post by karthick87 on 2010-12-08
Run the following commands in terminal,

```
sudo dpkg --configure -a 
```

```
sudo apt-get update
```

---

### Post by sikander3786 on 2010-12-08
Partial Upgrade means that some packages have been held back and are not going to be upgraded to the new versions.

It is not a distro or release upgrade, just regular Updates being installed there.

You can see which packages are being held back by running this command.

```
sudo apt-get update && sudo apt-get upgrade
```

If it is asking for some packages to be removed, or if you don't feel confident, say No by pressing 'n' and post the complete output here.

See this.

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

---

### Post by dcstar on 2010-12-08
> **sikander3786 said:**
> Partial Upgrade means that some packages have been held back and are not going to be upgraded to the new versions.

It is not a distro or release upgrade, just regular Updates being installed there.
.......

That's right, but **there is no need whatsoever to tell people to use the command line** in this circumstance. It is just unnecessary.

---

### Post by dcstar on 2010-12-08
> **arunb said:**
> Hi,

What does partial upgrade mean ?? I am running 10.04, I just got a message asking for a partial upgrade, I donot want to change from 10.04, is it Ok to  cancel this message ??


If you want to remain on 10.04 change the Update Manager settings - Release Upgrade to "Long term support releases only".

---

### Post by sikander3786 on 2010-12-08
> **dcstar said:**
> That's right, but **there is no need whatsoever to tell people to use the command line** in this circumstance. It is just unnecessary.
That was meant to see the output of that command. So the OP can easily copy/paste the data between Terminal and Forums.

---

### Post by arunb on 2010-12-08
I did the upgrade, I did not use the terminal for this, everything works OK.

everyone thanks a lot for the help.

---

