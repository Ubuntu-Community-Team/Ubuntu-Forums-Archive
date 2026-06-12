---
title: "Stuck with error after entering User_id and Password"
date: 2010-01-05
forum: General Help
---

### Post by TGcoffee on 2010-01-05
I receive these messages after I enter my user_id and password in Ubuntu 9.04;

"An error occured while loading or saving configuration information for update notifier.  Some of your configuration settings may not work properly."  then clicking on details box this can be seen;-
{Failed to connect configuration server; some possible causes are that you need to enable TCP/IP networking for ORBIT, or you have stale NFS locks due to a system crash.  See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details - 1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))}

then there's another error message;

"An error occured while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly." then clicking on details box this can be seen;- 
{Failed to connect configuration server; some possible causes are that you need to enable TCP/IP networking for ORBIT, or you have stale NFS locks due to a system crash.  See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details - 1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))}

after clicking Ok.  the desktop is just blank.

Need help please.

---

### Post by TGcoffee on 2010-01-07
got this from the link stated;-

I'm having a lock file problem. What do I do?

Usually a problem here involves either NFS, or a kernel bug.

The per-user daemon locks two files in the default configuration:

   ~/.gconfd/lock/ior
   ~/.gconf/%gconf-xml-backend.lock/ior
The first lock is to ensure that only one gconfd is running. The second lock is to ensure only one program accesses the XML config source at a time.

If you have an NFS-mounted home directory, you must be running an rpc.statd/rpc.lockd setup on both NFS client and NFS server, so that file locking works. On Red Hat Linux, this means the "nfslock" service must be running. Enable it permanently with the chkconfig tool - see its manual page. Turn it on or off at any given time with service nfslock start or service nfslock stop. You must be root to do this.

If the kernel crashes (or the power cord gets pulled) on an NFS client machine, theoretically when you reboot the client machine it will notify the NFS server that it has rebooted and all previously-held locks should be released. However, many operating systems including Red Hat Linux 7.2 do not properly do this; so you will have stale locks after a crash. If no gconfd is running, these locks may safely be removed. If gconfd is running though, DO NOT remove them; if you have two gconfd processes for a single user, bad things may happen to that user's preferences once in a while.

erm, sounds completed, any idea how to put it on Layman's term?
:?:?:?

---

### Post by TGcoffee on 2010-01-18
I try looking at the drive using Ubuntu LiveCD, it can't seem to mount the volume.
Reason to go into the drive is to look at the Gconf. file.
The drive can't be mounted with an error Detail;-

mount: wrong fs type, bad option, bad superblock on /dev/sda3, missing codepage or helper program, or other error in some cases useful info is found in syslog - try dmesg | tail or so

need help please..... :(

---

