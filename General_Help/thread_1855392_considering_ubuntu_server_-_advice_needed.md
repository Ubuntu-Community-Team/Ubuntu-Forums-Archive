---
title: "considering ubuntu server - advice needed"
date: 2011-10-06
forum: General Help
---

### Post by studentseedltd on 2011-10-06
Hello All

I have a very limited knowledge of what I am trying to create and how:
I am looking to create an office server for our small company (12 employees) using an HP ProLiant ML110 G5 Dual Core 2.33GHz with 4Gb RAM and 1TB SATA RAID (2 x 500Gb SATA RAID units)

I've been told Ubuntu Desktop would be ideal to run on this tower for our staff (clients) to access remotely (via remote online access) and locally using the office network in order to store/share/collaborate files and work.

Question 1: Is that right an Ubuntu and would be an ideal OS for those requirements.
Question 2: Being new to Ubuntu is it simple to setup the appropriate sharing settings on the server for the clients to access it remotely and via the network - any detail here would be much appreciated)
Question 3: is it a simply as accessing the server as a remote desktop/second desktop to navigate and save/retrieve files from its HD?
Question 4: Ubuntu Desktop or Ubuntu Server? - Not many of our staff would be comfortable using a command line to navigate
Question 5: am I missing anything obvious 

Excuse my ignorance ... any and all advice is much appreciated

Regards

Rufus

---

### Post by ejames on 2011-10-06
Sounds like you just want to use it as a file server ?
In that case I'd reccommend you go for Ubuntu server and set up Samba on it.
WIndows and Mac computers will then be able to access the Samba shared disk as a normal network drive.
For collaboration you could also look at setting up subversion on it - there are easy tools for using subversion on windows (tortoise) and mac.
A wiki is good for collaboration too - look into moinmoin for that.
If you just go with ubuntu server, install webmin so you can administer it easily with a web front end - makes things very simple.
Another thing you might want to look into - trac. It's a combination of a wiki, subversion and a forum - another handy tool for collaboration.

---

### Post by studentseedltd on 2011-10-06
Thanks!

---

### Post by lcman on 2011-10-06
> **studentseedltd said:**
> Hello All

I have a very limited knowledge of what I am trying to create and how:
I am looking to create an office server for our small company (12 employees) using an HP ProLiant ML110 G5 Dual Core 2.33GHz with 4Gb RAM and 1TB SATA RAID (2 x 500Gb SATA RAID units)

I've been told Ubuntu Desktop would be ideal to run on this tower for our staff (clients) to access remotely (via remote online access) and locally using the office network in order to store/share/collaborate files and work.

Question 1: Is that right an Ubuntu and would be an ideal OS for those requirements.
Question 2: Being new to Ubuntu is it simple to setup the appropriate sharing settings on the server for the clients to access it remotely and via the network - any detail here would be much appreciated)
Question 3: is it a simply as accessing the server as a remote desktop/second desktop to navigate and save/retrieve files from its HD?
Question 4: Ubuntu Desktop or Ubuntu Server? - Not many of our staff would be comfortable using a command line to navigate
Question 5: am I missing anything obvious 

Excuse my ignorance ... any and all advice is much appreciated

Regards

Rufus

You can use Google apps for collaboration. Or you can install Vmware zimbra on ubuntu server, it's free.

You will also need file sharing it seems, so, like ejames said, install and configure SAMBA.

Your staff can access the server remotely if it has a public ip with dns server but it's better to setup a VPN for security. You can also purchase IP VPN from your ISP but it usually costs too much money. Then, they can just use VNC to connect to the server anytime!

Install ubuntu server then apt-get install ubuntu-desktop after it's up and running to get the GUI.

---

### Post by ejames on 2011-10-06
If the server is going to be available just on the internal network then you don't have to be too worried about security. However if you intend having some of the services available from the outside you'd need to think through how you are going to secure things.
I think it should be reasonably easy to set up a vpn using webmin which would allow secure access from outside too.

---

### Post by studentseedltd on 2011-10-06
Thanks everyone ... its all very helpful ... server is ordered and Ubuntu is downloaded. 

I'm looking forward to joining the Ubuntu community

---

### Post by mastablasta on 2011-10-06
there is a nice ubuntu based distribution for small servers: [http://distrowatch.com/table.php?distribution=zentyal](http://distrowatch.com/table.php?distribution=zentyal)
 
They have a GUI for administering it and all that. 
 
ofcourse you can just go Ubuntu server way and add you own stuff to it so you can administer it remotelly via GUI. 
 
also for easy installing (only install) on server you can use this neat tool: [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

