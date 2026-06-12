---
title: "E: Unable to lock the administration directory"
date: 2006-02-17
forum: General Help
---

### Post by kelloggsx on 2006-02-17
NEWBIIEEEE here! and yes! very lost! and very frustrated ( sorry about typo) english not first language.

anyway! this is my problem! 

1) just finish installing ubuntu 5.10 
2) did the updates ( from little red icon) everything seeimg to work fine.
3) trying to install automatix ( ran terminal and type:  sudo apt-get update)

got a bunch of "ok" line.. then the following msg:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

after that any and ALL commands that i type in the terminal window get the following msg:

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

LOST LIKE THERE IS NOT TOMORROW... HELP.

I also dont know why i cant log in as the "root" and how do i go about giving my default user account "admin" rights as M$ does.

Help please

thanks

aol: klgsx
yahoo: kelloggssx
msn: [email]kelloggsx@hotmail.com[/email]

---

### Post by kaamos on 2006-02-17
Are you running synaptic at the same time? Try closing all other applications.

You have admin rights (literally actually since you are part of the group "admin"), but they work differently. If you wish to make system wide changes such as install video drivers or configure a firewall you have to enter your password. If you need to use the terminal with such an action, just put sudo in front of it. So instead of
```
command
```
type
```
sudo command
```

Hope this helps.

---

### Post by jrib on 2006-02-17
For your root/admin question, see: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

As far as the automatix problem, you may try posting in the automatix sub-topic somewhere in this forum.  The author of automatix, arneiboy, seems to keep an eye on it.  Keep in mind that only one application can access the apt database at once (which is what your error seems to be related to).  So "Synaptic/dpkg/update manager/aptitude/apt-get/automatix using one of the previous"<-- you should only be using one of those at a time.

---

### Post by Mustard on 2006-02-17
Some extra reading on the administration access is at this link too...

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

The error message above does sound like you either have Synaptic Package Manager open at the same time as you are running Automatix, or that the update manager is running in the background doing its thing at the same time.  Basically, Synaptic, the Update-manager, Apt-get and dpkg are all related and working on the same files, so you can't have two going at the same time.  The system creates a lock file to stop this occuring, and the error message is related to that.  When one of the above applications finishes and is closed down, the lock file is released.

-edit-

Hehehe..beaten to the punch today. :)

---

