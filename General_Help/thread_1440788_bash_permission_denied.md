---
title: "bash: permission denied"
date: 2010-03-27
forum: General Help
---

### Post by jasonwlh314 on 2010-03-27
I just into Ubuntu, and not familiar with the error information...

I tried to execute the following command:
$ ./eval_online_wiki.ml -db_user aa -db_pass bb -db_name cc

It returned as follows: bash: ./eval_online_wiki.ml: Permission denied

What does this mean? How to solve the problem?

Actually, I was following a README, and it says "$ ./eval_online_wiki -db_user <username> -db_pass <pwd> -db_name <db_name>"

Help me!

---

### Post by Ancanus on 2010-03-27
It seems to be that your eval_online_wiki.ml has not been flagged as an executable.
Try
```

# chmod +x eval_online_wiki.ml

```

---

### Post by NiGhtMarEs0nWax on 2010-03-27
yep, on linux every thing has either read, write or executable permissions.

if you do a:
```
ls -l filename     or    /path/filename
```

you will get an output like this:

```
drwxr-xr-x  2 owner:group
```

to break it down  d rwx r-x r-x

the d means directory, could be - for a file.

the first block of 3, rwx is for the owner, read,write,execute permissions.
the second block r-x is for the group, read & execute only.
last block r-x is for 'others' (everyone else) read & execute.

the **owner:group**  ie **root:root** is the owner **root** and group **root**.


-rwxr-x--- root:users   is a file with r,w,x permissions for the owner root, read and execute for the group 'users' and no access at all for everyone else.


chmod +x 'file name'

will add executable permissions for all. scripts need to be executable before they can run in the terminal.

---

