---
title: "Error: getaddrinfo: Name or Service not known"
date: 2009-10-30
forum: General Help
---

### Post by nmyrick on 2009-10-30
I'm on a Windows domain, and I keep getting the following error when trying to remote in to other computers on the domain using terminal server with RDP or RDPv5.

Error: getaddrinfo: Name or Service not known 

Please help me with this.

Thanks,
nmyrick

---

### Post by cforceleritas on 2010-05-12
I'm having the exact same problem with "Terminal Server Client" trying to remote desktop to my Windows machine at work.

Ubuntu 10.04.

If it helps, "gnome-rdp" successfully connected with the same settings.  Strange...

---

### Post by nmyrick on 2010-05-12
It's been a while since I wrote this post, but I believe what fixed this for me was joining Active Directory.

Go to your Ubuntu Software Center and install 'Active Directory Membership', then join Active Directory.  This should fix your problem.

nmyrick

---

### Post by nmyrick on 2010-05-12
Of course you have to bring your home computer to work and get on the network with it to join AD.

---

### Post by nmyrick on 2010-05-12
Also, another program that I have found works well for remote desktop is TeamViewer.  It is free, just go to [http://www.teamviewer.com](http://www.teamviewer.com) . It works on Windows, Mac, and Linux.

---

### Post by gcbzzzz on 2010-05-24
[http://ubuntuforums.org/showthread.php?p=9352827#post9352827](http://ubuntuforums.org/showthread.php?p=9352827#post9352827)

---

### Post by greenerpole on 2010-08-15
Dear all, 

I had the error message "Error: getaddrinfo: Name or Service not known" trying to log in to the Windows server at my work, from my laptop (Ubuntu 10.04, fresh install) using rdesktop. I tried tsclient and gnome-rdp and had the same message.

I also tried to connect from a Windows computer and had no problem, so I know that the connection information (machine name, gateway hostname, username, password) are correct. 

Reading through this post, I conclude that i should provide an IP address instead of a machine name. Indeed, when i use 'dig', it fails to give me any answer for the IP. The question is: where can i find such an IP address? (And how can Windows find it and not Ubuntu?)

Thanks for any answer to this. 
Cheers.

---

