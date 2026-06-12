---
title: "Automatix Uninstall"
date: 2006-06-09
forum: General Help
---

### Post by cjhardie on 2006-06-09
What is the easiest way to uninstall all my automatix programs if I use ubuntu 5.10???

---

### Post by Macchi on 2006-06-09
I believe that the best solution for this is to backup your /home and /etc and start over with a clean install of Ubuntu 6.0 6 Dapper.

With all respect that Automatix is quite useful for many pepople, my personal experience is that it messed up my system up to a point that I had to reinstall everything. Unfortunately those scripts have not been designed for long term maintenance, when you wish to easily upgrade software or be able to revert the system back to a previous stable state.

My alternatives to Automatix are EasyUbuntu and BUMPS.
And by the way, while installing other software directly from tarballs we may be  also doing irreversible changes to the system. It is better to use checkinstall and produce a .deb package that may be easily installed, removed or upgraded later on.

---

### Post by bluevoodoo1 on 2006-06-09
[QUOTE=Macchi]I believe that the best solution for this is to backup your /home and /etc and start over with a clean install of Ubuntu 6.0 6 Dapper.[/QUOTE]

That sounds somewhat drastic, though I have not used Automatix. 

What about this thread? 

Removal of softwares installed by automatix
[http://www.ubuntuforums.org/showthread.php?t=90797](http://www.ubuntuforums.org/showthread.php?t=90797)

---

### Post by Macchi on 2006-06-09
Yes I agree that it is quite drastic to reinstall the whole system. But is is not at all so difficult if you get well prepared for it.

The perspective of a manual removal with over 40 different steps is probably not worth the effort considering that it may not guarantee a clean system.

If the goal is to upgrade the system to Dapper I would not hesitate and reinstall. 
Then I would enjoy the freshness of a clean install for a few minutes, just before I restart to reinstall a lot of stuff.

---

### Post by matt_risi on 2007-01-27
Kinda related, I installed the wrong version of automatix2 from the website, as I'm running dapper not edgy. How do I remove the edgy version so I may use automatix?

---

### Post by r4ik on 2007-01-27
sudo apt-get remove automatix2
and install the version you need.

---

### Post by matt_risi on 2007-01-28
Tried that, it didn't remove anything. Said it had 0 bytes to remove, etc. Don't know why.

---

### Post by jackrobinson on 2007-01-28
> **matt_risi said:**
> Tried that, it didn't remove anything. Said it had 0 bytes to remove, etc. Don't know why.

you need to edit your sources.list and make sure the right repo is added.
make sure you DO NOT have the following line in /etc/apt/sources.list
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by matt_risi on 2007-01-31
Ahhh shoulda known that. Thanks man.

---

