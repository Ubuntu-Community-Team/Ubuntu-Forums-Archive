---
title: "Please Help - Samba Permissions"
date: 2011-03-19
forum: General Help
---

### Post by Daisy2 on 2011-03-19
Hi,

I'm using Ubuntu 10.10 as a Windows server.

I have four Windows7 machines connected to Samba and reading and writing the shared Ubuntu drives.

I am experiencing one problem.  When one of the Windows machines creates a directory on the Ubuntu drive and adds a file to that directory the directory and file is not fully shared.  The other Windows machines can only read the file.  I need the other Windows machines to have full access to the directory and file.  Any machine should be able to read, write, delete etc.

How do I automatically give all Windows machines equal privileges over any folder or file no matter which machine created it?

At the moment I am having to change the permission of each folder manually with chmod.

Besides the usual settings my smb.conf file also contains:
[global]
usershare owner only = False

[share]
    path = /home/myhome/share
    writeable = yes
;    browseable = yes
    valid users = machine1, machine2, machine3, machine4



Thanks for any advise!

---

### Post by lykwydchykyn on 2011-03-19
Just as with Windows, both the sharing permissions AND the local filesystem permissions apply to the file.  My suspicion is that the file is being created with the logged-in user as owner.

You either need to force the user, like so:
```

force user = someuser

```
So that all read/write operations will be done with the same local server account, or
```

force create mode = 777
force directory mode = 777

```

which will make sure any uploaded files are world-writable.

---

### Post by Daisy2 on 2011-03-19
Hi lykwydchykyn,
Thanks for the prompt response!

So should I cange the smb.conf to:

[share]
path = /home/myhome/share
writeable = yes
; browseable = yes
valid users = machine1, machine2, machine3, machine4
force users = machine1, machine2, machine3, machine4
force create mode = 777
force directory mode = 777

Would that be correct?

Many thanks for your help

---

### Post by lykwydchykyn on 2011-03-19
"force user" only takes one username, and there is no "force users" command.  See the documentation here:  [http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCEUSER](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCEUSER)

You don't need to force a user if you are going to force the permissions; you only need to do one or the other, it's just a question of what makes more sense to you.

---

