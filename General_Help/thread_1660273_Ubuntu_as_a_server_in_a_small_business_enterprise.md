---
title: "Ubuntu as a server in a small business enterprise"
date: 2011-01-05
forum: General Help
---

### Post by Peter Alien on 2011-01-05
Hello to everyone,

can someone tell me if Ubuntu 10.04 LTS or Ubuntu 10.10 is free for me to put him as a Server in a Small Business Enterprise here in Portugal.

My ideia is to connect Ubuntu as a File Server to 3 or 4 PCs with Win7 to share files with them.


Many thanks.

---

### Post by Drenriza on 2011-01-05
As far as i know, your free to use the Ubuntu server edition as you want. But support for the system, costs money.

Kind regards.

---

### Post by mastablasta on 2011-01-05
you kidding? check out the server edition. it's free.
 
and go for 10.04 since it's server edition from has 5 years support.
 
if you know how to set it up yourself or if you are ready to read soem manual you don't need to pay anything. epsecially for small business. maybe for osme large system it would be more complicated.

---

### Post by Peter Alien on 2011-01-05
The only problem is that i don´t know how to do everything in the Console, so i thought i could use Ubuntu 10.04 LTS Desktop Edition as a Server.

What do you think?


I want to use Samba (File sharing), ClamAV/ClamTK (check for virus in the directories that are shared with Win7's), ufw (firewall) and sbackup (auto-backup of the directory with the shares files).

For a file server service only and with those apps that i wrote above, maybe the Server could not become much slower using the Desktop Edition.

I think Server Edition is only Console based, right?

---

### Post by seawolf167 on 2011-01-05
The server does not have a GUI, and that is the biggest difference (also some package differences) between the desktop and server versions (you don't need a GUI taking your cpu cycles in a server environment). 

However, you can install a GUI on the server version.

You said you only have 3-4 other machines that you are going to connect too, so I don't see why you would have any problems using the desktop version instead of the server version, especially since all you are doing is file sharing, scanning and backups.

---

### Post by BbUiDgZ on 2011-01-05
Instead of installing the GUI (ubuntu desktop) on the server edition look here
[http://webmin.com/](http://webmin.com/)

---

### Post by KdotJ on 2011-01-05
As a side note, using the server edition with no GUI is a great way to learn. It will teach you about how to move around the file system in the terminal, move files and also how to use/edit configuration files to your needs. 

Obviously if you don't have time or interest in this, then go with the GUI version. But bear in mind, no GUI means it is less load on your system (as mentioned above). Also, I had an issue trying to run the desktop edition as a server with no monitor connected. It kept saying "no visual output" or something to that effect and wouldn't load up to desktop properly

---

### Post by restorator on 2011-01-05
For what you are doing the desktop edition would be just fine, unless you have an old slow machine and even then you could run a lighter distro something like xubuntu or puppy etc. 

By the way, where in Portugal are you, I am hoping to move near Porto in a few years from now!

---

