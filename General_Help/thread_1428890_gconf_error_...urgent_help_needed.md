---
title: "gconf error ...urgent help needed"
date: 2010-03-13
forum: General Help
---

### Post by nbulchandani on 2010-03-13
Hello all,
whenever i do anything as sudo i get
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
...plz help
Thanks

---

### Post by vashman on 2010-07-15
This was resolved on my machine by removing by removing the contents of the .gconfd directory.
There where five directories in hand that would be related to the problem(.gnome .gnome2 .metacity .gconf .gconfd), I was able to restore the configuration with only the .gconfd one.
```
rm -r /home/[username]/.gconfd/*
```
Out of the four accounts on this machine, only one was affected which drew me to the conclusion that it was due to the accounts own configuration  files.

---

### Post by Penny N. Nickels on 2010-07-19
> **nbulchandani said:**
> Hello all,
whenever i do anything as sudo i get
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to GConf daemon: Connection is closed)
...plz help
Thanks

I have been getting that same message lately when after I finally get logged on, except my [COLOR=Red]Details[/COLOR] reads: [COLOR=Red]*1: Failed to get connection to session: Failed to connect to socket/temp/dbus-0bOsxNTbxR: Connection refused*[/COLOR]. That message would appear in the box as many times as it took for me to finally login. (The only thing that changes is the last part, as to which [COLOR=Red]*dbus*[/COLOR] it was.) Could this something in connection to the looping login problems I've been having? Any help would be graciously appreciated!

---

