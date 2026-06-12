---
title: "I removed myself from the root and admin groups"
date: 2011-02-07
forum: General Help
---

### Post by 6tonspacefly on 2011-02-07
I am no longer a member of any group other than my name.  I therefor cannot do anything that requires root access.

How do I fix this?  Thank you.

---

### Post by zhogan85 on 2011-02-07
It's good practice not operate as root so that you don't accidently screw anything up. To give yourself root privileges, in the terminal before your command, type "sudo". For example

sudo apt-get install program_name_here

---

### Post by sisco311 on 2011-02-07
> **6tonspacefly said:**
> I am no longer a member of any group other than my name.  I therefor cannot do anything that requires root access.

How do I fix this?  Thank you.

Boot into recovery mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

EDIT: By default, admin users are also added to the *cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,admin,sambashare,lpadmin and video* groups. So, may want to add your user to this groups as well:

```
sudo usermod -aG cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,admin,sambashare,lpadmin,video **username**
```

where **username** is your login name.

HTH

---

### Post by 6tonspacefly on 2011-02-07
> **sisco311 said:**
> Boot into recovery mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

EDIT: By default, admin users are also added to the *cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,admin,sambashare,lpadmin and video* groups. So, may want to add your user to this groups as well:

```
sudo usermod -aG cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,admin,sambashare,lpadmin,video **username**
```

where **username** is your login name.

HTH
Holy crap you are awesome!  Thank you SO much.

---

### Post by sisco311 on 2011-02-07
> **6tonspacefly said:**
> Holy crap you are awesome!  Thank you SO much.

My pleasure!

Don't forget to mark this thread as [SOLVED]. Thanks!

---

