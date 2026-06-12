---
title: "Crashed system, how to recover MySQL databases?"
date: 2010-02-27
forum: General Help
---

### Post by osiszh on 2010-02-27
Hello, 

I was running a small home server to host a few websites of my own. I have recently purchased dedicated hosting and no longer need this box for that. 

The problem I am having is that the power supply on my box has gone dead and I have no spares to retrieve my data. 

I am running Ubuntu 9.10 and had some data in the /var/www directory that I can easily recover.

My question is, I am going to pop this hard drive into a machine running Windows XP to recover the data in /var/www

How can I go about getting the MySQL dumps out of this linux drive through Windows?

Thanks so much for the help.

---

### Post by cjhabs on 2010-02-27
if the drive was formatted as ntfs or fat then you should be able to access the drive under windows like any other data drive.
if it was ext or something else then you will probably need to boot the machine using a live cd and copy the data that way, mounting the ext file system and the windows disk and copying that way.

---

