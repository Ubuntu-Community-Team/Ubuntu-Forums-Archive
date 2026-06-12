---
title: "root cannot follow a symlink owned by non-root"
date: 2011-11-23
forum: General Help
---

### Post by Skaperen on 2011-11-23
I've run into a case where the **almighty powerful root** cannot follow a symlink owned by a non-root user.  The case I found where this is happening is when the **directory** the symlink is in, which is owned by root, has permissions 1777 (drwxrwxrwt).  If I change the directory permissions to 755 (drwxr-xr-x) then it works as expected.  It happens in both 10.10 and 11.04 (I have nowhere to test 11.10 at the moment).  It happens on both ext2 and ext4.

The code block below shows only the test in /tmp, but it happens in other filesystems and directories, too, as long as the same conditions are set up.  Note from the example that root can access the directory **directly** in all cases.  It can also follow the symlink if it owns it.  And it can **see** the symlink contents even when it cannot follow it.  It's something with the combination of directory permission mode settings (the sticky bit, apparently) and symlink ownership not being root.

I tested this in Slackware 13.37 with ext4 and it does not happen there (root can follow all symlinks always).

```
lorentz/root/c0 /tmp 75# ls -dl /tmp ; cd /tmp ; ls -dl . ; ls -dl a b ; ls -dl b/* ; ls -dl a/* ; cd a
drwxrwxrwt 55 root root 69632 2011-11-23 01:28 /tmp
drwxrwxrwt 55 root root 69632 2011-11-23 01:28 .
lrwxrwxrwx 1 phil phil    1 2011-11-23 01:27 a -> b
drwxr-xr-x 2 phil phil 4096 2011-11-23 01:27 b
-rw-r--r-- 1 phil phil 0 2011-11-23 01:27 b/foo
ls: cannot access a/*: Permission denied
bash: cd: a: Permission denied
lorentz/root/c0 /tmp 76# chmod 755 /tmp
lorentz/root/c0 /tmp 77# ls -dl /tmp ; cd /tmp ; ls -dl . ; ls -dl a b ; ls -dl b/* ; ls -dl a/* ; cd a
drwxr-xr-x 55 root root 69632 2011-11-23 01:28 /tmp
drwxr-xr-x 55 root root 69632 2011-11-23 01:28 .
lrwxrwxrwx 1 phil phil    1 2011-11-23 01:27 a -> b
drwxr-xr-x 2 phil phil 4096 2011-11-23 01:27 b
-rw-r--r-- 1 phil phil 0 2011-11-23 01:27 b/foo
-rw-r--r-- 1 phil phil 0 2011-11-23 01:27 a/foo
lorentz/root/c0 /tmp/b 78# chmod 1777 /tmp
lorentz/root/c0 /tmp/b 79# ls -dl /tmp ; cd /tmp ; ls -dl . ; ls -dl a b ; ls -dl b/* ; ls -dl a/* ; cd a
drwxrwxrwt 55 root root 69632 2011-11-23 01:28 /tmp
drwxrwxrwt 55 root root 69632 2011-11-23 01:28 .
lrwxrwxrwx 1 phil phil    1 2011-11-23 01:27 a -> b
drwxr-xr-x 2 phil phil 4096 2011-11-23 01:27 b
-rw-r--r-- 1 phil phil 0 2011-11-23 01:27 b/foo
ls: cannot access a/*: Permission denied
bash: cd: a: Permission denied
lorentz/root/c0 /tmp 80#
```

---

### Post by mutley89 on 2011-11-23
Same behaviour here as well.  This seems like a possible explanation:
[https://lwn.net/Articles/390323/](https://lwn.net/Articles/390323/)
[https://lwn.net/Articles/390565/](https://lwn.net/Articles/390565/)

---

### Post by Skaperen on 2011-11-23
> **mutley89 said:**
> Same behaviour here as well.  This seems like a possible explanation:
[https://lwn.net/Articles/390323/](https://lwn.net/Articles/390323/)
[https://lwn.net/Articles/390565/](https://lwn.net/Articles/390565/)
That explanation does make sense.  I'll call this thread solved (so hopefully the next person running into it has a better chance of finding the explanation in whatever terms they search on).

Now I need to go redesign my system to make it easy for users to add their own web sites.  My scheme involved a directory with the sticky bit where users put their site directory.  A script would automatically rebuild the Apache2 config file to include it.  The catch was that when Apache2 restarts, a symlink (e.g. 2 or more sites operating out of 1 directory) would fail the test Apache2 startup was doing and produce a warning.  So I need to figure out another way to do this w/o giving users the power to set the DocumentRoot to just anything they want.

---

