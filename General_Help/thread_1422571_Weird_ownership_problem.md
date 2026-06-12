---
title: "Weird ownership problem"
date: 2010-03-05
forum: General Help
---

### Post by msp3k on 2010-03-05
Hi gurus,

I'm integrating Ubuntu with an existing network and I've run into a problem.  Users that belong to a certain group cannot enter a directory owned by the same group:

```
user1@dama:/home/groups$ id
uid=10004(user1) gid=10004(user1) groups=20(dialout),21(fax),22(voice),
24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),100(users),
104(fuse),124(vboxusers),10004(user1),20000(everybody),20007(evaluation),
30008(nimbiods)

user1@dama:/home/groups$ ls -ald staff
drwxrwx--- 2 root nimbiods 4096 2010-01-06 10:04 staff

user1@dama:/home/groups$ ls -aldn staff
drwxrwx--- 2 0 30008 4096 2010-01-06 10:04 staff

user1@dama:/home/groups$ cd staff
-bash: cd: staff: Permission denied

```

Huh?  Do I have a case of "Teh Dumbz" or should this be working?

Both ~user1/ and ./staff/ are NFS-mounted, but other directories owned by other groups all work, just this one, seemingly, doesn't work.

---

### Post by msp3k on 2010-03-05
Hmm...

I'm using openldap (slapd 2.4.11-0ubuntu6) and NFS (nfs-kernel-server 1:1.1.2-4ubuntu1), both from Karmic.  Apparently the highest group ID you can use is 20007.

That is to say:

If I create a group in LDAP with GID 20007, and make user1 a member of this group, and then create a directory on the NFS server owned by this group, then user1 can enter.

If I change the group ID to 20008 (or, apparently, anything above that), change the group ownership of the directory to 20008 on the NFS server, then user1 can no longer enter.

If I create a local directory group owned by GID 20008, or 30008, then user1 can enter.

So it seems to be a limitation of NFS ownership IDs?

Whatever the reason for this, if I remap the UID/GID numbers to be below 20008 (not too difficult as there aren't many) then it works.

---

### Post by msp3k on 2010-03-05
It doesn't seem to be just NFS, but either something to do with NFS+LDAP or something specific to Ubuntu.  I won't claim to understand it though.

I reproduced the same situation on an older system (Debian Etch) that uses NIS (instead of LDAP) and the problem doesn't exist there.

---

### Post by doas777 on 2010-03-05
> **msp3k said:**
> Hi gurus,

I'm integrating Ubuntu with an existing network and I've run into a problem.  Users that belong to a certain group cannot enter a directory owned by the same group:

```
user1@dama:/home/groups$ id
uid=10004(user1) gid=10004(user1) groups=20(dialout),21(fax),22(voice),
24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),100(users),
104(fuse),124(vboxusers),10004(user1),20000(everybody),20007(evaluation),
30008(nimbiods)

user1@dama:/home/groups$ ls -ald staff
drwxrwx--- 2 root nimbiods 4096 2010-01-06 10:04 staff

user1@dama:/home/groups$ ls -aldn staff
drwxrwx--- 2 0 30008 4096 2010-01-06 10:04 staff

user1@dama:/home/groups$ cd staff
-bash: cd: staff: Permission denied

```Huh?  Do I have a case of "Teh Dumbz" or should this be working?

Both ~user1/ and ./staff/ are NFS-mounted, but other directories owned by other groups all work, just this one, seemingly, doesn't work.

are these perms on the mount or the share? also can you confirm that dama is in the nibiods group?

---

### Post by msp3k on 2010-03-05
> **doas777 said:**
> are these perms on the mount or the share? also can you confirm that dama is in the nibiods group?

I'm not sure that I follow you here.

"Dama" is the name of the client, LDAP-bound and mounting the server via NFS.

"user1" is a test user account.  User1 is also in group called "nimbiods", which has a GID of 30008.

"/home/groups/staff" is a directory that is owned by 0:30008 (or root:nimbiods).  It exists on the NFS server and is being mounted by dama.

Apparently the GID 30008 doesn't work.  In fact, after spending some time testing, no GID number above 20007 works.

Other directories also owned by 0:X, where 20000 <= x <= 20007 work just fine.  It's only when the GID exceeds 2007 that the problem begins.

I haven't been able to find any rock hard documentation that explains it, but what documentation I've found implies that UIDs and GIDs can go up to 65533 (specifically, the UID/GID 65534 is what root is mapped to when root_squash is used in the /etc/exports file).

By comparison, if I create a local directory on dama and set the ownership to 0:X, where X > 20007, it works just fine.  This only seems to affect NFS-mounted directories.

---

### Post by msp3k on 2010-03-08
I'm going to have to shrug this one off and move on.

When I left things on Friday the problem still existed.  On Saturday I shut
the machines down for a scheduled power outage.  On Sunday when I powered
everything back up the problem was gone.

All users can access their group directories just as expected.

Maybe there was something cached somewhere that didn't get cleared until the
power cycle?  I'm only guessing.

---

### Post by msp3k on 2010-03-12
Okay, I've been able to reproduce the problem, and I've been performing some
tests.

I'm REALLY hoping someone can help me to understand what's going on here...

Test #1) NFS

On the NFS server, created the following directories:

```

# ls -aldn *
drwxr-x--- 2 0 20000 4096 2010-03-08 11:28 g20000
drwxr-x--- 2 0 20007 4096 2010-03-08 11:28 g20007
drwxr-x--- 2 0 20008 4096 2010-03-08 11:28 g20008
drwxr-x--- 2 0 30000 4096 2010-03-08 11:28 g30000
drwxr-x--- 2 0 30008 4096 2010-03-12 13:40 g30008

```On the NFS client:

1) Created a local test user, named "tester"
2) Created the following groups, placed user "tester" in each group:
```

g20000:x:20000:tester
g20007:x:20007:tester
g20008:x:20008:tester
g30000:x:30000:tester
g30008:x:30008:tester

```Become the test user:
```

# su - tester
$ groups
tester g20000 g20007 g20008 g30000 g30008
$ cd /home/groups/test
$ ls -aldn *
$ ls -aldn *
drwxr-x--- 2 0 20000 4096 2010-03-08 11:28 g20000
drwxr-x--- 2 0 20007 4096 2010-03-08 11:28 g20007
drwxr-x--- 2 0 20008 4096 2010-03-08 11:28 g20008
drwxr-x--- 2 0 30000 4096 2010-03-08 11:28 g30000
drwxr-x--- 2 0 30008 4096 2010-03-12 13:40 g30008
$ (cd g20000 && pwd)
/home/groups/test/g20000
$ (cd g20007 && pwd)
/home/groups/test/g20007
$ (cd g20008 && pwd)
/home/groups/test/g20008
$ (cd g30000 && pwd)
/home/groups/test/g30000
$ (cd g30008 && pwd)
/home/groups/test/g30008

```LDAP Setup)

Added the following to the LDAP database:

```

add cn=testldap,ou=groups,dc=nimbios,dc=org
objectClass: posixGroup
objectClass: top
cn: testldap
userPassword: {crypt}*
gidNumber: 1903

add uid=testldap,ou=users,dc=nimbios,dc=org
uid: testldap
cn: Tester LDAP
objectClass: account
objectClass: posixAccount
objectClass: top
userPassword: {MD5}*
loginShell: /bin/bash
uidNumber: 1903
gidNumber: 1903
homeDirectory: /home/testldap
gecos: Tester LDAP

add cn=testldap,ou=auto.home,ou=automount,dc=nimbios,dc=org
cn: testldap
objectClass: top
objectClass: automount
automountInformation: -fstype=nfs,rw,hard,intr,nodev,exec,nosuid,rsize=8192,wsize=8192 home.nimbios.org:/export/a/home/testldap

add cn=g20000,ou=groups,dc=nimbios,dc=org
objectClass: posixGroup
objectClass: top
cn: g20000
userPassword: {crypt}*
gidNumber: 20000
memberUID: testldap

add cn=g20007,ou=groups,dc=nimbios,dc=org
objectClass: posixGroup
objectClass: top
cn: g20007
userPassword: {crypt}*
gidNumber: 20007
memberUID: testldap

add cn=g20008,ou=groups,dc=nimbios,dc=org
objectClass: posixGroup
objectClass: top
cn: g20008
userPassword: {crypt}*
gidNumber: 20008
memberUID: testldap

add cn=g30000,ou=groups,dc=nimbios,dc=org
objectClass: posixGroup
objectClass: top
cn: g30000
userPassword: {crypt}*
gidNumber: 30000
memberUID: testldap

add cn=g30008,ou=groups,dc=nimbios,dc=org
objectClass: posixGroup
objectClass: top
cn: g30008
userPassword: {crypt}*
gidNumber: 30008
memberUID: testldap

```Test #2) LDAP+NFS, using "su - testldap":

```

# su - testldap
$ groups
testldap g20000 g20007 g20008 g30000 g30008
$ id
uid=1903(testldap) gid=1903(testldap)
groups=1903(testldap),20000(g20000),20007(g20007),20008(g20008),30000(g30000),30008(g30008)
$ cd /home/groups/test
$ ls
g20000  g20007  g20008  g30000  g30008
$ (cd g20000 && pwd)
/home/groups/test/g20000
$ (cd g20007 && pwd)
/home/groups/test/g20007
$ (cd g20008 && pwd)
/home/groups/test/g20008
$ (cd g30000 && pwd)
/home/groups/test/g30000
$ (cd g30008 && pwd)
/home/groups/test/g30008

```Test #3) LDAP+NFS, using gdm login and terminal:

```

$ cd /home/groups/test
$ ls
g20000  g20007  g20008  g30000  g30008
$ id
uid=1903(testldap) gid=1903(testldap) groups=21(fax),22(voice),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),100(users),104(fuse),124(vboxusers),1903(testldap),20000(g20000),20007(g20007),20008(g20008),30000(g30000),30008(g30008)
$ (cd g20000 && pwd)
/home/groups/test/g20000
$ (cd g20000 && pwd)
/home/groups/test/g20007
$ (cd g20007 && pwd)
/home/groups/test/g20008
$ (cd g20008 && pwd)
bash: cd: g30000: Permission denied
$ (cd g30000 && pwd)
bash: cd: g30008: Permission denied
$ ls -aldn *
drwxr-x--- 2 0 20000 4096 2010-03-08 11:28 g20000
drwxr-x--- 2 0 20007 4096 2010-03-08 11:28 g20007
drwxr-x--- 2 0 20008 4096 2010-03-08 11:28 g20008
drwxr-x--- 2 0 30000 4096 2010-03-08 11:28 g30000
drwxr-x--- 2 0 30008 4096 2010-03-12 13:40 g30008

```Test #4) LDAP+NFS, using console login:

```

$ id
uid=1903(testldap) gid=1903(testldap)
groups=21(fax),21(fax),22(voice),22(voice),24(cdrom),24(cdrom),25(floppy),25(floppy),26(tape),26(tape),29(audio),29(audio),30(dip),30(dip),44(video),44(video),46(plugdev),46(plugdev),100(users),100(users),104(fuse),104(fuse),124(vboxusers),124(vboxusers),1903(testldap),20000(g20000),20007(g20007),20008(g20008),30000(g30000),30008(g30008)
$ cd /home/groups/test
$ ls
g20000  g20007  g20008  g30000  g30008
$ (cd g20000 && pwd)
bash: cd: g20000: Permission denied
$ (cd g20000 && pwd)
bash: cd: g20007: Permission denied
$ (cd g20007 && pwd)
bash: cd: g20008: Permission denied
$ (cd g20008 && pwd)
bash: cd: g30000: Permission denied
$ (cd g30000 && pwd)
bash: cd: g30008: Permission denied
$ ls -aldn *
drwxr-x--- 2 0 20000 4096 2010-03-08 11:28 g20000
drwxr-x--- 2 0 20007 4096 2010-03-08 11:28 g20007
drwxr-x--- 2 0 20008 4096 2010-03-08 11:28 g20008
drwxr-x--- 2 0 30000 4096 2010-03-08 11:28 g30000
drwxr-x--- 2 0 30008 4096 2010-03-12 13:40 g30008

```

---

