---
title: "Copy files preserving permissions"
date: 2010-11-17
forum: General Help
---

### Post by sebagr on 2010-11-17
Hi,

I have a really annoying problem...

I'm a web developer and have my www inside my home set with permissions 770 and owner <myuser>:www-data. I need this so the web server can read/write in that folder.

Whenever I copy a file within that folder (using Terminal or Nautilus) the new file owner is <myuser>:<myuser>; that is, it doesn't preserve owner information (nor permissions).

I know I can do ```
copy -p
``` to preserve them, but I'd like that to be the default behavior (specially working with Nautilus, which I use a lot).

Is there any way of changing this?

Many thanks in advance!

---

### Post by SeijiSensei on 2010-11-17
The simplest solution is to make www-data be your primary group.

On my machine www-data has group ID 33 ("grep www-data /etc/group" to check).  If you look at your entry in /etc/passwd, you'll see a pair of colon-separated numbers after your login name which are your UID and primary group ID.  Use "sudo nano /etc/passwd" to edit the file with root privileges and change the second number in your record to 33 (after you've confirmed that's the correct value in /etc/group).  Then all your activities will apply the www-data group by default.

Once you've done this you'll no longer belong to your original group.  To fix that, edit /etc/group as root and place your username after the final colon for the group entry that matches your username.  Now you'll have all the same group privileges your account had before.

You'll need to log out and log back in again to make these changes active.

---

### Post by endotherm on 2010-11-17
I would set GID on teh folder, so that all files created within the folder automatically take on the group that owns the folder. then just make sure that the group and owner permissions are the same. 

here is an example:
```
Lucid:~$ mkdir thing1
Lucid:~$ ll | grep thing1
drwxr-xr-x   2 myUser myUser  4096 2010-11-17 14:16 thing1/
Lucid:~$ sudo chown myUser:users thing1
[sudo] password for myUser: 
Lucid:~$ ll | grep thing1
drwxr-xr-x   2 myUser users   4096 2010-11-17 14:16 thing1/
Lucid:~$ sudo chmod 2771 thing1
Lucid:~$ touch thing1/test1.txt
Lucid:~$ ll thing1
total 28
drwxrws--x  2 myUser users   4096 2010-11-17 14:18 ./
drwx------ 35 myUser myUser 12288 2010-11-17 14:16 ../
-rw-r--r--  1 myUser users      0 2010-11-17 14:18 test1.txt
Lucid:~$ 
```

the chmod line turns on setGid by putting the 2 in front of the standard permission tripplet that you desire. in your case, make sure that the group and owner permissions are the same, as you will be relying on group, rather than user from here out.

---

### Post by sebagr on 2010-11-17
@endotherm: that's exactly what I needed, thanks!

@SeijiSensei: your solution, while it's not exactly what I asked, shows a different way of achieving what I ultimately wanted, demonstrating once more the importance of explaining the actual underlying problem (web server access by default) and not just the 'symptom' (wrong permissions on copy). Thanks!

---

