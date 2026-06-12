---
title: "How to let user &quot;brynjarh access /media/hdb1?"
date: 2006-02-28
forum: General Help
---

### Post by brynjarh on 2006-02-28
I have an extra hard drive at /media/hdb1 that I want user "brynjarh" to be able to read/write/execute. Currently the permission for it is drwxr-xr-x or:

File owner: root
File group: root

Owner:    X-Read    X-Write    X-Execute
Group:    X-Read    O-Write    X-Execute
Others:   X-Read    O-Write    X-Execute

And the line for hdb1 in /etc/fstab is:
/dev/hdb1       /media/hdb1     reiserfs defaults        0       2

I don't want other users then "brynjarh" to be able to write to it except for root of course. I guess I might be able to change the owner to brynjarh but would that stay after a reboot? And isn't there a better/default way like changing the group to something new and then have both root and brynjarh in that group and add write permission to "Group".. or something along those lines?

---

### Post by RAOF on 2006-02-28
Root **always** has write privileges to **everything**.  Nothing is forbidden root!  You don't need to care about root when you're setting file permissions. :)

Thus, all you need to do is run a "sudo chown brynjarh -R /media/hdb1".  Because reiserfs is a real filesystem that supports access control, this will be persistant across reboots.

---

### Post by brynjarh on 2006-02-28
Okay, then that's cleared up, thanks. \\:D/

---

