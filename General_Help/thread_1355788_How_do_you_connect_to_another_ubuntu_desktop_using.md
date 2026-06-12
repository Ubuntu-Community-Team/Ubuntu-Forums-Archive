---
title: "How do you connect to another ubuntu desktop using the router?"
date: 2009-12-15
forum: General Help
---

### Post by Btheone on 2009-12-15
I have a laptop and desktop pc, I have to keep manually moving stuff to each using a usb stick. I wondering if its possiable to access each other by using the router?

The main reason i want to do this is because only one has access to a printer, so I want to be able to securely if possible connect to it.

There is 3 other windows computers on the network, but i don't want them to be able to have access.

Anyone help me please?

---

### Post by northern lights on 2009-12-15
System > Administration > Printing

right-click the printer, mark it as shared.

---

### Post by Dennis N on 2009-12-15
Use an SSH connection between computers. You need openssh-server to be installed (from Ubuntu repo) on the Ubuntu computers you want to reach (send files to).

---

### Post by audiomick on 2009-12-15
Hallo.
I did some posts recently on a thread dealing with a similar issue.
I think most of what you need to know is in there.
[http://ubuntuforums.org/showthread.php?t=1342940](http://ubuntuforums.org/showthread.php?t=1342940)

---

### Post by Btheone on 2009-12-15
When i try and connect i get this problem:

ssh: connect to host my-computer-name port 22: Connection refused

Why is this?

thanks.

---

### Post by Ordes on 2009-12-15
Seems your firewall is blocking your income request.

Open port 22 for ssh (incoming) on receiving PC. Best is you open the port only for those IPs that your requesting PCs have, like 192.168.1.100,....

Might need to setup a static IP for that (internal IP, or network IP)
System > Preferences > Network Connections  (for the ip)
---

In case you dont know how to configure the Ubuntu firewall. Try firestarter. Its a nice GUI tool to configure your firewall...

---

### Post by Btheone on 2009-12-15
Thanks all! I have now managed to connect to the computer using ssh, im just wondering now how possible would it be to connect to a windows machine on the network? Because they don't have SSH on there, is there any easy way - just wondering out of interest now, again thanks.

---

### Post by Grenage on 2009-12-15
You'll want to use samba, and I think that comes installed by default in Ubuntu.  In Nautilus:

```
smb://machine/folder
```

You can also create shares in Nautilus, shares that Windows can access.

---

### Post by audiomick on 2009-12-15
Look at this:
[https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo](https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo)

---

### Post by Btheone on 2009-12-15
Thanks, All!

---

### Post by Dennis N on 2009-12-15
> **Btheone said:**
> Thanks all! I have now managed to connect to the computer using ssh, im just wondering now how possible would it be to connect to a windows machine on the network? Because they don't have SSH on there, is there any easy way - just wondering out of interest now, again thanks.

You can still use SSH with Windows if you wish - just install a client on Windows. I have Filezilla installed on my Win XP machine. Using it, one can connect to Ubuntu computers from Windows via SSH and move files back and forth. Very easy.

---

### Post by Dennis N on 2009-12-15
**Some advice on making SSH more secure:**

[http://ubuntu-tutorials.com/2007/02/14/what-you-ought-to-know-about-securing-ssh/](http://ubuntu-tutorials.com/2007/02/14/what-you-ought-to-know-about-securing-ssh/)

---

### Post by Ordes on 2009-12-15
Please mark it [solved] than... Using Thread Tools...

Its easy to do, takes 5sec and is helpful to others...

---

