---
title: "Dual-boot (Ubuntu/Windows) development workstation/server planning help needed."
date: 2010-03-23
forum: General Help
---

### Post by slworks on 2010-03-23
Hi everyone.

I am planning to build a machine for website development and design.
I want to run as much as possible under Linux (including a L.A.M.P. stack) however i just can't ditch Photoshop for Gimp yet.

I am not really sure about how to set this up, but i came up with the following idea :
I want to use a larger HDD (160Gbyte at least) exclusively for these projects, but SHARED between the two operating systems and using an NTFS partition.
I basically want to place Apache's www root folder and the database files of MySQL (if thats even possible) onto this disk and i want to use the same version of apache2 and mysql under both OSes to access the websites i'm working on.

(editing the config files is not a problem here.)

I would like to know if it is actually possible to do so. (i guess there would be no big problems with apache) however... can i share the files that mysql stores the databases in between two mysql-servers running on two different operating systems on the same machine?

I posted this thread into General discussion, because i'm not really sure if it belongs under one particular category (possibly server platforms, but then again... this machine won't be just a server)

Also, i looked on google for info about my issue, but found no useful information.

Any tips and suggestions are welcome.

---

### Post by john newbuntu on 2010-03-23
Apache I don't think should be a problem.
However, I don't think you can run the same version of mysql from both Linux and Windows. Your options would be to set up mysql separately on a different linux box and use OS specific clients to access mysql server or go for a replication.
However, I have not tried the virtualization option, where you try and access mysql (say, running in a host) from a guest box.  That could be possible with minor tweaks.

---

### Post by slworks on 2010-03-23
I would only access mysql through localhost.
the idea is, to access the same work under linux and windows (so when i jump over to windows, i can work the graphics and still see the website completely with contents.)

---

