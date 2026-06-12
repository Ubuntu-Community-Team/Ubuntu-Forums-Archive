---
title: "suddenly shutdown after update -- ups ??"
date: 2010-11-18
forum: General Help
---

### Post by rnerwein on 2010-11-18
high
nrver got problems with the the system ( koala ....) but i made an update today and the result is
( randomize 1, 2 or 3 hours ) the system turn off ( like anybody is calling the halt [ or power off ] command ) . i tried to send you my debug messages about my configuration and it results
in:
root@tschang:/var/log 18:49-> apport-bug linux
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Error showing url: Operation not suported


--> the current kernel is: 163863 -rw-r--r-- 1 root root 4050080 2010-11-17 20:23 vmlinuz-2.6.32-26-generic
but !!! --> 163851 -rw-r--r-- 1 root root 8316833 2010-11-18 15:50 initrd.img-2.6.32-26-generic
my question is - how to fix this and where does it come from.
i made every updates before - that's - sorry for me for an lts system very serious.

i'm not a newbe. there is absolute no log in the /var/log/* that can help me to check out what is going on.
i fall back to the : Linux tschang 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux

and this works - why ???? 
ciao

---

