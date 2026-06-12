---
title: "Help with Wireless Card in Ubuntu"
date: 2006-03-05
forum: General Help
---

### Post by purecomper on 2006-03-05
Hey All.

I am currently using an Ubuntu Live CD for testing purposes. (I will download an install CD if all turns out well.)

Anyways, I have a Dell Inspriron 1150 with a Dell 1350 wireless card. I have searched the WiKi for answers but have come out short for (Simple) answers, so I have gone that route.

My question is: How can I set up my wireless card to access the internet in Ubuntu? Can you please answer in simple terms? I am pretty avid within Windows but Linux is new ground for me.

Thanks in advance...

---

### Post by beck24 on 2006-03-05
you can use windows wireless drivers in ubuntu, in fact it's really easy because it's even done through a gui.

1. Download the windows drivers from the Dell website
2. Unzip to wherever you want to keep them
3. Go to "System"-->"Administration"-->"Windows wireless drivers"
4. Put in your password
5. Click "Install New Driver"

Browse the file system and find where you unpacked the drivers you downloaded.  In the unzipped folder will be a file with extension .inf (mine is bcmwl5a.inf).  Select that file and click "install"

6. Click "Configure Network" to activate your wireless network.


I hope this works for you, it did for me.  I would also recommend getting a small program called "netapplet", you can get it through synaptic (just type "sudo synaptic" at the command line) and do a search for "netapplet".  It'll allow you to switch back and forth from wireless to ethernet, and from one wireless connection to another (even with WEP keys etc) graphically.

Good luck

---

