---
title: "Problem setting file permission in Ubuntu 10.4"
date: 2011-01-31
forum: General Help
---

### Post by s.a.patil on 2011-01-31
Respected community members, I'm facing unique problem with my Ubuntu 10.4 installation. After recent update of Ubuntu I'm not able to change the file permission of other user file from my Default Admin 'User Account'. Here is details of the problem.
When I type "sudo find /home/otheruser/ -type d -print0 | xargs -0 sudo chmod 0777" it successfully change the permission.
But when I type "sudo find /home/otheruser/ -type f -print0 | xargs -0 chmod 0777"  it return error for each files.
I did not face any issue before update, what may be the problem? Also one can find my post on Ubuntu forum that I'm facing another problem with "Users and Groups" where I cannot change my Account password. Thanks a lot in advance.
Please note that if I type "sudo find /home/otheruser/ -type f -print0 | xargs -0 sudo chmod 0777" it gives error message of command length.
Update: Respected matt_symes wrote in response to my thread Not able to change 'User Account'  password ([http://ubuntuforums.org/showthread.php?t=1678847](http://ubuntuforums.org/showthread.php?t=1678847)) "Have you tried dropping to a root shell at the grub menu and changing it from there ? From the root shell... Code: passwd Your_username" but I fear it will enable 'root' because I'm particular about disabled 'root'.

---

### Post by vanadium on 2011-01-31
You can only change permissions of files that you own. In order to change other files, you need root permissions.

When you pipe the output of one command to another, you do just that:
```

sudo find /home/otheruser/ -type d -print0 | xargs -0 chmod 0777

```
The first command is run with root privileges, the command that receives the output of that first command is running with normal privileges.

You can test that nicely from the output of "ls -l" after running
```

sudo touch test1 | touch test2

```

> ..."sudo find /home/otheruser/ -type f -print0 | xargs -0 sudo chmod 0777" it gives error message of command length.

To avoid that, use find's "exec" option instead of an xargs construct.

---

### Post by s.a.patil on 2011-01-31
Respected vanadium, thanks a lot. I really appreciate your kind help. Will fallow your tips :) :)

---

