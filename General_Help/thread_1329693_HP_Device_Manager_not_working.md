---
title: "HP Device Manager not working"
date: 2009-11-17
forum: General Help
---

### Post by davehkent on 2009-11-17
This program allows me to view device status, ink levels, and perform maintenance on my HP Deskjet D1460 printer, and worked perfectly under Ubuntu 9.04

However, since upgrading to 9.10, if I go to Applications > Accessories > HP Device Manager and click on it, absolutely nothing happens.

If it's any help, entering "hp-toolbox" in Terminal gives the following output:

david@ubuntu:~$ hp-toolbox

HP Linux Imaging and Printing System (ver. 3.9.6b)
HP Device Manager ver. 15.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-toolbox requires GUI support. Exiting.
david@ubuntu:~$ 

I suspect the "Qt/PyQt 4 initialisation failed." may have something to do with the problem, but don't know how to fix it, so any help appreciated!

Cheers
davehkent

---

### Post by davehkent on 2009-11-17
[solved]

I've solved my own problem by installing the new version of the program from the Software Centre.

Cheers
davehkent

---

### Post by Vermind on 2009-11-17
Please mark the thread as solved, from Thread Tools - Mark thread as solved.

---

