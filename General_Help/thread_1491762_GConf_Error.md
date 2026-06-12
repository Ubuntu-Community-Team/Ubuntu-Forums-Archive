---
title: "GConf Error"
date: 2010-05-24
forum: General Help
---

### Post by Skidbladniir on 2010-05-24
I've looked around, I've emptied any suspicius (... I have got to update Firefox, the spell check isn't workuing...) things in my /tmp file, looked in ~/.gconf[d], and looked in /var/lock.

```

GConf error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
All further errors shown only on terminal

```It appears when I start file-roller, and a few other applications.  My system hasn't crashed recently...
Please help.  (Oh, and shoot me, I'm using the root account)

Using 10.04 Xubuntu - CD Install (Not update-manager upgraded)

---

### Post by Skidbladniir on 2010-05-24
^Bump^

---

### Post by Skidbladniir on 2010-05-24
By the way, the terminal just repeats that same error message over and over.

---

### Post by wojox on 2010-05-24
```
cd /home/username/.gconfd
```

```
rm -rf saved_state
```

reboot
(when the machine reboot, a fresh copy of the saved_state file will be generated and this should solved the problem)

---

