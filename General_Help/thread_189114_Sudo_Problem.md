---
title: "Sudo Problem"
date: 2006-06-04
forum: General Help
---

### Post by dthomp325 on 2006-06-04
Help! I can't sudo, su , or login as root. I can't access any admin features.

Whenever I try to use the sudo command I get something like this:

Sorry, user ***** is not allowed to execute '/bin/bash' as root on localhost.localdomain

If I try to access one of the graphical admin utilities with the graphical sudo I get this:
Failed to run ***** as user root:
 Child terminated with 1 status

If I try to su I get this:
su: Authentication failure
Sorry.

I also cannot login to root from gdm.

What do I need to do to fix this?

thanks

---

### Post by bswilson on 2006-06-04
Sir, it sounds to me like your userid is maybe not in the proper groups for whatever reason.  Let's take it one step at a time.  Try running the command:

```
/usr/bin/groups <username>
```

Where *<username>* is your username on that Ubuntu system.  What groups does it show that you belong to?  Do you see a group called **adm** in the list?  There are probably 5 to 10 entries, and **adm** should be one of them.

---

### Post by dthomp325 on 2006-06-04
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner

---

### Post by dthomp325 on 2006-06-04
Could this be a problem with my /etc/sudoers file?

I can't copy the file contents right now, because I don't have permission to access it, but I used a knoppix boot cd to view it, and there was only a single entry in the file aside from comments:

root All = (All) all

Should there be an entry in this file regarding my normal user?

The reason this happened in the first place is because ever since I installed Ubuntu about a month ago, sudo has not worked. I have been using su with my root password instead. Today I disabled root login with this command:

passwd -l root

in the hopes that disabling root would somehow get sudo to work properly. Now I am stuck and cannot access either the root account or use sudo. I do have access to protected files with my trusty knoppix boot cd.

---

### Post by bswilson on 2006-06-05
I see 2 problems; first that your group membership is missing the group called admin.  Second, that your /etc/sudoers file is in fact missing something.

**1. Group membership**
I think you'll want to add yourself to the admin group too.  Using your Knoppix CD, boot up and use vi as root to edit /etc/group and ensure that your system has your userid listed for membership to the admin group.  Mine looks like this (106 is my userid number):

```
bswilson@ubuntu:~$ grep admin /etc/group
admin:x:106:bswilson
```

**2. Fix sudoers file**
As long as you have that Knoppix CD, boot to it and then just use vi as root to edit the /etc/sudoers file.  Back it up first; you're supposed to use visudo to edit this file but I think in this case you'll be okay.  Add this:

```
# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL
```

Once you boot back into Ubuntu, I think you'll be all set.

---

### Post by dthomp325 on 2006-06-05
I added this line to my sudoers file as a temporary fix.
username    ALL = (ALL) ALL

This way I can use sudo, but I have no idea what the security implications are.

As for adding my user to the admin group, and then adding the line to the sudoers file so that admin has the correct privileges; I looked at /etc/group and it doesn't show any 'admin' group. How weird is that? Should I create an admin group, or maybe my admin group is just the group called 'adm'?

---

### Post by garyng on 2006-06-05
> **dthomp325]I added this line to my sudoers file as a temporary fix.
username    ALL = (ALL) ALL

This way I can use sudo, but I have no idea what the security implications are.

As for adding my user to the admin group, and then adding the line to the sudoers file so that admin has the correct privileges said:**
> 

This is supposed the way of sudo.

[QUOTE]root All = (All) all

This is redundant(thus useless) as what it means is "you are allowed to sudo if you are root", and root don't need sudo.

---

