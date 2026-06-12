---
title: "Permission denied - Executing"
date: 2010-07-22
forum: General Help
---

### Post by shahraj81 on 2010-07-22
Hi,

I have written a perl script that prints "hello world!". When I execute it by

>>perl temp.pl

it works. But when I run it directly:

>>./temp.pl

I get the following error:

-bash: ./temp.pl: Permission denied.

The output of ls -l:

-rwxr-xr-x 1 rajput rajput     95 2010-07-16 10:17 temp.pl

It sure is executable by this user.

I think it is the way I have mounted the hard drive. Some lines from fstab:

/dev/sdb2       /media/global_1 ext4    rw,suid,dev,exec,auto,user,async 0 0

I did some research to figure out the problem but could not fix it.

Can anyone point me in the right direction? Thanks.

---

### Post by andrewc6l on 2010-07-23
Is the first line of your script something like:
```

#!/usr/bin/perl

```

If not, it should be (that's what tells the shell to invoke Perl as opposed to another program to run the script).

If so, are you sure your perl executable is in /usr/bin/ and not somewhere else? You can find out where your perl is installed with:
```
which perl
```

---

