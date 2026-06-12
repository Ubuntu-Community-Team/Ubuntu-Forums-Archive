---
title: "sudo is not working.."
date: 2010-01-26
forum: General Help
---

### Post by omshiralkar on 2010-01-26
Hi All,

I am new to Ubuntu and facing a strange problem.
I think accidentally I have changed permissions of /usr/bin/sudo to 777
Now whenever I try to use sudo command I get an error message...
sudo: must be setuid root

My prediction is I need to login as root and change permission back to 4111 ( i.e u+s) 

But when I try to boot in recovery mode using ESC key. I can not change permission and get a message 'this is readonly file system'.

Also I am unable to login as su. Error is: authentication failure. I haven't set any separate password for su.
In fact I have never logged in as su before.

Can you please help me to solve this problem?

---

### Post by sisco311 on 2010-01-26
Try to remount the root partition:
```
mount -o remount,rw /
```
or boot a Live CD, mount the partition and change the permissions.

EDIT:

If you are using 9.10 (Karmic), then you can use pkexec to change the permissions. Boot in normal mode and run:
```
pkexec chmod 4111 /usr/bin/sudo
```

---

### Post by nothingspecial on 2010-01-26
Do you mean you can`t boot into a root maintanence shell.

It may work if you boot from a live cd

You need to

```

chown root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo
```

But not the live cds /usr/bin/sudo

mount the computers file system to the live cd first

---

### Post by Lars Noodén on 2010-01-26
Use the rescue mode of the LiveCD or Alternate Install CD.

The correct permissions for /usr/bin/sudo are  -r-sr-xr-x

```

chmod u=rxs,g=rx,o=rx /usr/bin/sudo

```

---

### Post by sisco311 on 2010-01-26
> **Lars Noodén said:**
> Use the rescue mode of the LiveCD or Alternate Install CD.

The correct permissions for /usr/bin/sudo are  -r-sr-xr-x



Well, the default permissions for sudo, in Ubuntu (at least lucid), are -rwsr-xr-x (4755). It's a binary so the read permissions are futile, it's owned by root, but root already has write permission on any files (the write permission for the owner is futile as well). There is noting wrong with setting the permissions to 4111.

---

### Post by omshiralkar on 2010-01-26
Yahoo!!!!!!!!!!!!!!!!!!!!!!!!!!

Its working properly now!

I did exactly what '[nothingspecial]("http://ubuntuforums.org/member.php?u=491516")' said in post # 3

Booted via a live ubuntu CD, mounted local file system and then changed the permission.

Thanks a lot all of you, for quick and perfect replies!!!

Thanks,
Omkar Shiralkar

---

