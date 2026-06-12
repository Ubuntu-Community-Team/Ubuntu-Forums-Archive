---
title: "Automount DVD for all users"
date: 2011-11-10
forum: General Help
---

### Post by mrreload on 2011-11-10
Long time Ubuntu user here. Currently 11.04 64bit
I use NoMachine server to develop on my system remotely. This machine also is the frontend for XBMC for my TV. I use 2 different logins for each purpose. But need access to the DVD drive from both.
The Problem: DVDs automount but only per user, no other users can access. /etc/mtab shows umask=077
Questions: 
1. Is it possible to get Automount to work with multiple users? 
2. Why is umask=077 used? What harm could with at least allowing group read access to the drive?

---

### Post by Mark Phelps on 2011-11-10
If you're asking, can several different users access the same DVD drive at the same time, I don't see how that could work.

---

### Post by mrreload on 2011-11-10
> **Mark Phelps said:**
> If you're asking, can several different users access the same DVD drive at the same time, I don't see how that could work.

Why shouldn't that work? It is just another filesystem. 
I could bypass automount and get it read-only to all users, so why and or how can I get the same access with automount? 

What mechanism is Ubuntu currently using for automounting? hal, udev, etc. It seems the way this is done has changed multiple times and I cannot find anything about the more recent releases.

---

### Post by mrreload on 2011-11-11
Maybe I should rephrase the issue. I want multiple users to be able to be able to read the automounted DVD drive. 
Is this possible?

---

