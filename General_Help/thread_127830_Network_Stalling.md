---
title: "Network Stalling"
date: 2006-02-09
forum: General Help
---

### Post by cdano on 2006-02-09
Symptom:

Install was fine from ISO image.  However, after install, I've noticed that any large file transfer stalls after a few seconds.  I first noticed this when I tried to run the update.  It would start and then just get stuck and finally just report "Failed."  I then tried to download a 40M file from another server in Firefox- it gets about 200K in, then fails.  On a laptop on the same network in the same switch, no problems.  A redhat install on another server in the same network, no problems.  Ifconfig is reporting no errors, dropped, overruns, collisions, etc.  All just receive and transmit packet counts.

Hardware:

Dell Dimension L800r with its built-in Intel ethernet chipset.
I've also tried inserting an old generic PCI ethernet card in it which works fine in another version of Linux and was able to configure it, but then I received the same result.
I've tried different switches, ethernet cables, etc.
I'm on broadband and I have no other problems.
On the same switch, I have a redhat install on the exact same type of machine with no problems.

Anyone have any ideas?

---

### Post by dcstar on 2006-02-10
[QUOTE=cdano]Symptom:

Install was fine from ISO image.  However, after install, I've noticed that any large file transfer stalls after a few seconds.  I first noticed this when I tried to run the update.  It would start and then just get stuck and finally just report "Failed."  I then tried to download a 40M file from another server in Firefox- it gets about 200K in, then fails.  On a laptop on the same network in the same switch, no problems.  A redhat install on another server in the same network, no problems.  Ifconfig is reporting no errors, dropped, overruns, collisions, etc.  All just receive and transmit packet counts.

Hardware:

Dell Dimension L800r with its built-in Intel ethernet chipset.
I've also tried inserting an old generic PCI ethernet card in it which works fine in another version of Linux and was able to configure it, but then I received the same result.
I've tried different switches, ethernet cables, etc.
I'm on broadband and I have no other problems.
On the same switch, I have a redhat install on the exact same type of machine with no problems.

Anyone have any ideas?[/QUOTE]

Search for "disable IPv6", or post the question in the Networking forum.

---

### Post by cdano on 2006-02-10
Hey I did both, there, David, and still doesn't work.  
UBUNTU:

linux for people who know how to use

sudo
how to use gedit
understand su-

and know

how to edit module files
how to rem out ipv6
how to post on forums


is this worth it?

---

### Post by dcstar on 2006-02-10
[QUOTE=cdano]Hey I did both, there, David, and still doesn't work.  
UBUNTU:

linux for people who know how to use

sudo
how to use gedit
understand su-

and know

how to edit module files
how to rem out ipv6
how to post on forums


is this worth it?[/QUOTE]
You are obviously having problems few (if any) other Ubuntu users are experiencing, so you make up your own mind on the question, other than that this may help:

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Also the **ethtool** command can show the settings that your network card is working with, if it is an auto-negotiation issue then you may be able to experiment with different settings.

---

### Post by cdano on 2006-02-12
blah  - i'm going to try a knoppix live cd and see if i have the same issue - if yes, then it's hardware, if no, then i'll try ubuntu on a future rev.

---

### Post by ttallos on 2006-02-12
I had a similar problem on one of my machines in my case I had a IDE controller problem. I am going to replace the system board when I get a little extra $$ Just flashed the BIOS with the newest and it seems to work better but I still have the large file problem.

---

### Post by cdano on 2006-02-16
Doing a netinst of Debian with the exact same machine, purring along at super high speeds.... Hmm..  Looks like a bug or something in Ubuntu at this point.

---

