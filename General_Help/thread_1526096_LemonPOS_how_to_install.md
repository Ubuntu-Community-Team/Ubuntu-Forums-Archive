---
title: "LemonPOS how to install?"
date: 2010-07-07
forum: General Help
---

### Post by telmore007 on 2010-07-07
I have Ubuntu 10.04 when I try and install from Ubuntu Software Center I get an Error. I have searched the forums. Is there a free easy to install Point of Sale Program? I am somewhat familar with Ubuntu. My laptop will also boot into Windows 7. Be lately it has been crashing. That is why I went back to Ubuntu, and b/c of Open Source. :) 

Thanks, I hope someone can help me. :)

---

### Post by QIII on 2010-07-07
What error are you getting?

Is that a KDE app?

---

### Post by telmore007 on 2010-07-07
Package operation failed

The installation or removal of a software package failed.

---

### Post by telmore007 on 2010-07-07
I think I read that it is a KDE app. But I think I have that installed. Not sure.

---

### Post by Motovista on 2011-10-20
I have tried without success to install Lemon POS in Ubuntu, LinuxMint, Zorin OS, and Fedora. Finally, I installed Kubuntu, and got it to work right away, just by following the directions posted online. Unless you own Walmart, a POS system should need less than 20 gigs to operate and store your inventory, so do yourself a favor and load Kubuntu onto a partition, and load the POS system there.

---

### Post by Motovista on 2011-10-20
Here is how I did it in Kubuntu:

Terminal command- sudo apt-get install mysql-client mysql-server

download Lemon POS from Software Repository

Terminal command- cd /usr/share/kde4/apps/lemon/

Terminal command- cat lemon_mysql.sql | mysql -u root -p

Reboot and open Squeeze. There will be a username and password on the screen that logs into the database. **Leave that alone. **I think this is where most people (I did) have issues with the program, because they think they are supposed to put their mysql password or the default lemonpos username and password there.

Where you are asked for a user name and password, use admin and linux.

---

