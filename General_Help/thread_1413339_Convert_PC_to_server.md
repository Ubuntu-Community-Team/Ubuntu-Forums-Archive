---
title: "Convert PC to server"
date: 2010-02-22
forum: General Help
---

### Post by DogWalker on 2010-02-22
I have a desktop PC running Ubuntu 9.04.  It has an AMD Athlon 3000 processor and 2G of RAM with two HDDs, one 450G, the other 110G.  All my data on the desktop is backed up on the 2nd disk, together with data from 3 laptops.  My plan is to use the desktop as a file and print server for the other machines and in the process free up some work space on my desk as I'll no longer need the screen and keyboard for the desktop.

So, I think, all I have to do is download the 32bit version of Ubuntu 9.10 Server Edition and install it on the desktop.  Then I'll be able to access the backed-up data on the 2nd drive, and have an in-house web server as well.  I will be able to administer the new server from one of the other machines, hence the free desk space.

Have I got something badly wrong?  Am I overlooking anything?

Ollie K

---

### Post by e24ohm on 2010-02-22
> **DogWalker said:**
> I have a desktop PC running Ubuntu 9.04.  It has an AMD Athlon 3000 processor and 2G of RAM with two HDDs, one 450G, the other 110G.  All my data on the desktop is backed up on the 2nd disk, together with data from 3 laptops.  My plan is to use the desktop as a file and print server for the other machines and in the process free up some work space on my desk as I'll no longer need the screen and keyboard for the desktop.

So, I think, all I have to do is download the 32bit version of Ubuntu 9.10 Server Edition and install it on the desktop.  Then I'll be able to access the backed-up data on the 2nd drive, and have an in-house web server as well.  I will be able to administer the new server from one of the other machines, hence the free desk space.

Have I got something badly wrong?  Am I overlooking anything?

Ollie K

If you are only using this for HDD space, I would recommend FreeNAS [http://freenas.org/freenas;](http://freenas.org/freenas;) however, if you need a webserver you look good.

Learn RSYNC, CRON, and TAR commands and you will be rocking.

J

---

### Post by Neezer on 2010-02-22
I recently did the same thing with my old computer from college. I use it as a media server/file server. 

I got a few shiny new hdds from new egg and set up RAID 1 so that I have some securty from failing hdds, but it is pretty straight forward. 

I use ssh, and ssh tunnels to access the server from on and off my LAN. If you do that, using key authentication is the best way to go. 

I have even found that winscp works great as a file sharer between my windows laptop from work, and my ubuntu server. All of my connections go through the ssh port.

good luck and have fun.

---

### Post by e24ohm on 2010-02-22
> **Neezer said:**
> I recently did the same thing with my old computer from college. I use it as a media server/file server. 

I got a few shiny new hdds from new egg and set up RAID 1 so that I have some securty from failing hdds, but it is pretty straight forward. 

I use ssh, and ssh tunnels to access the server from on and off my LAN. If you do that, using key authentication is the best way to go. 

I have even found that winscp works great as a file sharer between my windows laptop from work, and my ubuntu server. All of my connections go through the ssh port.

good luck and have fun.
Cheers Mate!!! great thinking about SSH. 

SSH is a must to learn.

---

### Post by leg on 2010-02-22
I did this with an old pc I had lying around and I used Debian. I use it as a print and web server at the moment but intend to extend it to do some file serving as well.

---

### Post by DogWalker on 2010-02-22
Many thanks... here I go!

---

