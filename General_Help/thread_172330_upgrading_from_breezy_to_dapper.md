---
title: "upgrading from breezy to dapper"
date: 2006-05-08
forum: General Help
---

### Post by crakkajakka15 on 2006-05-08
some problem ive recently tried to upgrade from breezy to daper. I edited the sources.list can changed them all to dapper and then i did a sudo apt-get update which went fine i guess then i go to do my sudo apt-get upgrade and i comes up with this error .....
 xvinfo xwd xwininfo xwud zenity zlib1g
583 upgraded, 0 newly installed, 0 to remove and 464 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
todd@ubuntu:~$

im stumped can any one help?

---

### Post by barbarian on 2006-05-08
IMHO, on this stage, better upgrade from Dapper CD beta2

---

### Post by crakkajakka15 on 2006-05-08
where do i get that cd from

---

### Post by glotz on 2006-05-08
[https://lists.ubuntu.com/archives/ubuntu-announce/2006-April/000072.html](https://lists.ubuntu.com/archives/ubuntu-announce/2006-April/000072.html)

(google's your friend)

---

### Post by wtstommy on 2006-05-08
Before installing from a CD, try:

sudo apt-get dist-upgrade

If that does not work, I would check to make sure no instances of apt-get are currently running (ctr+esc for process table).

---

### Post by barbarian on 2006-05-08
it is not necessary for him to install from CD, he could just upgrade by adding CD to sources list.

---

### Post by wtstommy on 2006-05-08
I  understand that, but it looks as if his problem is that the resource list itself is unavailable, or some other directory apt-get requires to perform the necessary upgrade. The most likely cause of that kind of problem is permissions or an already-running process using the directory in question. 


Also, adding the dapper cd to the sources list and using the apt-get upgrade command should not upgrade from Breezy to Dapper. apt-get dist-upgrade is necessary (if I understand the process correctly).

---

