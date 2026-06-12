---
title: "sudo and login password recognized, password box does not like"
date: 2010-04-27
forum: General Help
---

### Post by Rocket J Squirrel on 2010-04-27
Karmic Koala,

I needed to use Synaptic Package Manager to install an app, but the dialog box ("enter the Administrative Password") that pops up before you can use Synaptic doesn't recognize my password ("incorrect password). I tried typing it into a text editor and it's spelled right, caps lock not turned on or anything. 

In Terminal, sudo recognizes it, and it is recognized when I log into Ubuntu. I'm the sole user, I have admin privileges, I've been doing admin things. 

I just now did System > Administration > Users and Groups and got a dialog box saying 

*"Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)"*

Moving past that, I changed my user password, and Ubuntu authenticated it. 

I'm baffled. 

How do you launch Synaptic Package Manager from the command line?

---

### Post by egalvan on 2010-04-27
> **Rocket J Squirrel said:**
> 
How do you launch Synaptic Package Manager from the command line?

```
 gksudo synaptic
```

but why do you want to?

error reporting?

---

### Post by Rocket J Squirrel on 2010-04-27
I'm installing some software packages and want to use Synaptic. However, as I noted in the OP, I can't run Synaptic or any other app that pops up the "enter the Administrative Password" box through System > Administration because the box does not recognize the same darn password that I use to sudo and to login. For some reason, whatever that dialog box looks to for password no longer likes the password. 

Thanks for the tip on how to run Synaptic through the command line, that works and it accepts my usual password. 

So -- does anyone have any suggestions on how to get the "enter the Administrative Password" box to accept the same password?

---

### Post by Rocket J Squirrel on 2010-04-27
While I'm trying to figure out why I can launch Synaptic from Terminal but not from  System > Administration because "enter the Administrative Password" box does not recognize my password (see top post in this thread), I wonder if someone can help me with this mess:

```
$ gksudo synaptic
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)

(gksudo:27258): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)

```

---

### Post by Rocket J Squirrel on 2010-04-27
Original question and the weird omg.org thing possibly caused by the same problem. See VanHammersly response at [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=864779](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=864779) -- I tried that and it seems to have fixed the password problem and the omg.org problem. i think. We'll see. I'm not changing this to Solved until I know for sure.

---

