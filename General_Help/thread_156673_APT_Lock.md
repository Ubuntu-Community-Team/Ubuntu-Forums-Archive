---
title: "APT Lock"
date: 2006-04-07
forum: General Help
---

### Post by Joetheodd on 2006-04-07
I've searched the forums and all I've seen is people trying to use Synaptic and apt-get at the same time. My computer actually crashed (just froze, out of nowhere, but that's beside the point (I think)) while running apt-get, and now it's perminantly locked. Even worse, I tried to fix it by /var/lib/dpkg/ and deleting lock.

Anyone had this problem before? How do you fix it?

---

### Post by Declan on 2006-04-07
I just navigate to the directory in question and issue the following command: 
sudo rm lock
It works for me.
Hope it does for you.

Declan

---

### Post by Joetheodd on 2006-04-07
joe@deadmeat:~ $ cd /var/cache/apt/archives
joe@deadmeat:/var/cache/apt/archives $ sudo rm lock

Thanks. I was almost sure I tried that before, but I guess not. This community is awesome, almost instant tech support, thanks.

---

### Post by fryxIHodi on 2006-04-10
Hi,

I have the same problem like Joetheodd (my computer froze while running apt-get and now it's locked) . I tried to delete the lock files, but I can't (I tried it in konquerer and console with sudo rm lock).

---

