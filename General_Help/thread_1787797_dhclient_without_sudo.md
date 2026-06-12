---
title: "dhclient without sudo"
date: 2011-06-21
forum: General Help
---

### Post by auftable on 2011-06-21
[FONT=Times New Roman][SIZE=3]Hello,[/SIZE][/FONT][COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]I want to start dhclient without using the sudo command from another software, JDownloader.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]I used visudo to change these permissions, but something is missing. How do I change the missing permissions?[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Last part of my visudo file:[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Times New Roman]# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%jdl ALL = NOPASSWD: /sbin/dhclient, /var/lib/dhcp3/dhclient.leases[/FONT][/COLOR]

```[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]
```
[FONT=Times New Roman]dhclient[/FONT]
[FONT=Times New Roman][SIZE=3]Internet Systems Consortium DHCP Client V3.1.3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Copyright 2004-2009 Internet Systems Consortium.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]All rights reserved.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]For info, please visit https://www.isc.org/software/dhcp/[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]can't create /var/lib/dhcp3/dhclient.leases: Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]SIOCSIFADDR: Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]SIOCSIFFLAGS: Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]SIOCSIFFLAGS: Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]SIOCSIFADDR: Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]SIOCSIFFLAGS: Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]SIOCSIFFLAGS: Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Open a socket for LPF: Operation not permitted[/SIZE][/FONT]

```[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]I am  member of the group jdl, part of the /etc/groups file:[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3]```
jdl:x:1007:auftable
```[/SIZE][/FONT]

---

### Post by auftable on 2011-06-26
Still looking for a solution.

---

### Post by gmargo on 2011-06-26
You still have to run the **sudo(1)** program.  You can't just type 'dhclient' and expect it to magically assume root permissions.

Can't you just make your jDownloader program run an arbitrary shell script?  Then put "sudo dhclient" inside the shell script.

---

