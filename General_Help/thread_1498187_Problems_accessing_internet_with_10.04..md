---
title: "Problems accessing internet with 10.04."
date: 2010-05-31
forum: General Help
---

### Post by KeithSloan on 2010-05-31
I am having some problems accessing the internet. I had to change some Firefox setting as guided by the web to access any site other than google.

I had to disable ipv6 in thunderbird to get it to work.

I followed some instructions to disable ipv6 [http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

Now when I try and ping the sites the applications are trying to access ( for example boinc ) I do not get a response yet if I put the same info into firefox I can access the site

---

### Post by blazemore on 2010-05-31
Right-click on the network manager icon in the notification area.
Select Edit Connections.
Find the connection you use.
Select it and click Edit.
Press IPv6 settings, and choose Ignore for the type.

---

### Post by KeithSloan on 2010-05-31
IpV6 setting is already set to ignore.

Still have the problem

---

### Post by Bobhuber on 2010-05-31
> **KeithSloan said:**
> I am having some problems accessing the internet. I had to change some Firefox setting as guided by the web to access any site other than google.

I had to disable ipv6 in thunderbird to get it to work.

I followed some instructions to disable ipv6 [http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

Now when I try and ping the sites the applications are trying to access ( for example boinc ) I do not get a response yet if I put the same info into firefox I can access the site
Exactly what was your original problem and why did you do all this to start with ?

---

### Post by KeithSloan on 2010-05-31
Original problem was that Firefox would only access google and not any other sites.

Thunderbird would not pick up my mail until I set its option to not use ipv6

Now it seems I have problems with any other application that uses the internet.
e.g BOINC, Crossover's install.

Driving me mad - Contemplating dumping Ubuntu and going back to Windows

---

### Post by KeithSloan on 2010-05-31
Okay found some stuff related to IPv6 in /etc/hosts took a backup and got ride of it. Rebooted and it seems to have solved things

---

