---
title: "Inconsistant User Permissions"
date: 2011-08-08
forum: General Help
---

### Post by Disapproved Toaster on 2011-08-08
I have 3 users that have overlaping groups but they do not behave the same.
I'll try to be as clear as possible

users:
userA:x:1014:1017:Boss 1:<home folder>
userB:x:1015:1017:Boss 2:<home folder>
accounting:x:1018:1021:Accounting:<home folder>

groups:
userA:x:1014:userA                     #default user group
userB:x:1015:userB                     #default user group
management:x:1017:userA,userB          #Management group
accounting:x:1021:admin,userA,userB    #Accounting group

The Accountants[C] files need to be read by the Bosses. C can read/write with no issue, Boss[A] can read/write with no issue, however any file opened and saved by Boss[B] becomes owned by that user.
ie:
-before-
[properties] admin:accounting [size / date] <name.xls>
-after-
[properties] **[COLOR="Red"]userB:management[/COLOR]** [size / date] <name.xls>

while the other users work as expected:
-after-
[properties] _[COLOR="green"]userA:accounting[/COLOR]_ [size / date] <name.xls>

I have spent weeks looking for an answer, I really hope it is something simple I overlooked, because I am tired of keeping an open SSH console to run sudo chown -R every time the accountant calls me.

Much Thanks in advance

Edit: I forgot to mention users are accessing the system via Samba from Windows 7 boxes. Not sure how much of a difference that makes.

---

### Post by oldfred on 2011-08-08
I have not done any groups in Linux. My last use was Novell 2.15 20 years ago.

But these may get you started.


[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

---

### Post by Disapproved Toaster on 2011-08-10
> **oldfred said:**
> 
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

Thank you, This will work as a stop gap for the time being. I will still continue to search for the answer to why this one particular user appears to reset the permissions on any file he saves. I even tried changing the owner to root:accounting and he was still taking ownership of both. After running
```
$ sudo chmod -R 2770 /home/accounting_dept
```
The file was finally able to retain it's group, but still gave up both ownership And the SGID bit that had been set to the file.

---

