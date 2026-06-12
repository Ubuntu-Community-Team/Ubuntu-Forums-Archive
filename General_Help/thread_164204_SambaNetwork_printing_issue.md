---
title: "Samba/Network printing issue"
date: 2006-04-22
forum: General Help
---

### Post by firecat53 on 2006-04-22
Hey....
   I've got a HP-PSC 2175 printer attached to a wired XP box and I'm trying to get printing to work from my wireless Ubuntu laptop. I can mount shares on the XP box from the laptop. If I try 'smbtree', it gives no output, unless I first ping the XP box. Then, it gives the following output:
```
HOME
        \\KIDS                          KIDS
cli_start_connection: failed to connect to KIDS<20> (0.0.0.0)
        \\HOMESERVER                    homeserver server (Samba, Ubuntu)
                \\HOMESERVER\PSC-2175           PSC-2175
                \\HOMESERVER\ADMIN$             IPC Service (homeserver server (Samba, Ubuntu))
                \\HOMESERVER\IPC$               IPC Service (homeserver server (Samba, Ubuntu))
                \\HOMESERVER\Group              Group Folder
                \\HOMESERVER\print$             Printer Drivers
        \\BUSINESS                      Business
cli_start_connection: failed to connect to BUSINESS<20> (0.0.0.0)

```
(HOMESERVER is a linux server, BUSINESS and KIDS are XP boxes)

When I'm logged in to the wired linux server (HOMESERVER), smbtree works correctly the first time (no ping required) and shows:
```
HOME
        \\KIDS                          KIDS
                \\KIDS\SharedDocs     
                \\KIDS\IPC$             Remote IPC
        \\HOMESERVER                    homeserver server (Samba, Ubuntu)
                \\HOMESERVER\PSC-2175           PSC-2175
                \\HOMESERVER\ADMIN$             IPC Service (homeserver server (Samba, Ubuntu))
                \\HOMESERVER\IPC$               IPC Service (homeserver server (Samba, Ubuntu))
                \\HOMESERVER\Group              Group Folder
                \\HOMESERVER\print$             Printer Drivers
        \\BUSINESS                      Business
                \\BUSINESS\Music (E)      
                \\BUSINESS\print$               Printer Drivers
                \\BUSINESS\SharedDocs     
                \\BUSINESS\IPC$                 Remote IPC
                \\BUSINESS\My Documents   
                \\BUSINESS\hp2175               hp psc 2170 series

```

So it appears that the laptop is not seeing the XP shares for some reason, thus the printing issue. Again, though, I can manually mount the XP shares (ie My Documents) from the command line just fine. The firewall settings on the XP box (Zone Alarm) allow access to all the computers on the network (and does the same thing with the firewall off, anyways).

Any thoughts??

Thanks, Scott

---

### Post by sitedesign on 2006-05-22
It may be that you have not set-up your /etc/hosts file on the linux box.
In there you will need a list of the computers on the network in the form:
192.168.1.10   business
192.168.1.20   homeserver
.....
 Also check the workgroup in the /etc/smb/conf file is the same as the other XP machines are on.

Then restart the linux box (I know you don't really have to but it saves explaining how to restart services).

---

