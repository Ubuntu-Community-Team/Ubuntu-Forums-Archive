---
title: "&quot;add user&quot; interface removed rootaccess on whole system!"
date: 2010-02-24
forum: General Help
---

### Post by cronjager on 2010-02-24
Just tried to add a new user to my system (9.10), when something realy weird  happened:
First I couldn't see any users in the "Users and Groups" menu, not even my own account. Then I tried to create a new (unprivileged) user, but it didn't show up niether. Then I quit the "Users and Groups" menu, and tried to open it again. This time, I could see a user, but only the root user. Then I quit again. Later I tried to gain root-access doing some other stuff, but all of a sudden, system told me, that I wasn't in the sudoers file anymore!
Then I rebooted the whole system, and got stuck with this messeage:

```
mountall: mount /dev/pts [397] terminated with status 32
mountall: Filesystem could not be mounted: /dev/pts
fsck from util-linux-ng 2.16
[     8.608595] Adding 393552k swap on /dev/sda5. Priority:-1 extents:1 across:393552k
init: mountall main process (389) terminated with status 4
Mount of root fileszstem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@notebook: 
```


All happened using the graphical interface in Ubuntu. I haven't been messing around with the terminal or the rootaccount or anything like that - just tried to add a new user to the system using the graphical inteface, and now I can't even access my system.

I really dont know wtf is goin on, and how to fix it :/ Would be really nice with some kindda help...

---

### Post by spiderbatdad on 2010-02-24
Did you launch the graphical interface as root from a terminal?

---

### Post by cronjager on 2010-02-24
nope. Just prompted the password to "unlock" the graphical interface as normal.

---

### Post by spiderbatdad on 2010-02-24
can you boot into recovery console? From there it might be useful to run the command ```
cat /etc/passwd
``` The output should show your user id 1000 near the end of the file. Next try to switch to the user account.
```
su username
``` Where username is your actual user name.

---

### Post by cronjager on 2010-02-24
yeah, that works. What do I do next?

---

### Post by spiderbatdad on 2010-02-24
ok check that your users /home directory exists.
```
cd /home
ls
``` to list directories in /home.
If all is as expected, I'm not sure what the problem is...try normal boot again and report results. It may be necessary to run 
fsck.

Edit: actually run
```
ls -al /home/user 
``` from the root directory or ```
 ls -al user
``` from /home to make sure the files and directories in /home/user are owned by the user.

---

### Post by cronjager on 2010-02-24
it's all there and owned by me. But the whole filesystem is writeprotected somehow. Cant even do stuff in my own home directory.

fsck says:
```

root@notebook: ~# fsck
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1: clean, 193387/468640 files, 1446372/1871564 blocks

```


EDIT: reboot doesn't help. Already tried that a million times

---

### Post by spiderbatdad on 2010-02-24
sorry feeling a little dumb right now. Just re-read your original post and realized I wasn't responding to the actual issue.

So /etc/passwd did list your user name with id 1000?

Can you become root from a normal login with the command ```
sudo -i
``` If so /etc/sudoers appears to work. If not login to recovery again and you can edit /etc/sudoers to contain the line

```
%admin ALL=(ALL) ALL

```

Also from recovery make sure your user is admin, I think 1000 is default admin.

The command ```
 groups user 
``` should list the groups your user belongs to...user should be substituted with actual user name. This command will add a user to admin group:
```
 useradd -G admin username 
```

---

### Post by cronjager on 2010-02-24
Yes, my user is the id 1000
I can't get rootaccess from normal login using 

```
sudo -i
```

althougn the /etc/sudoers has the line 

```
%admin ALL=(ALL) ALL
```
I can't add the user to the admin group using useradd. It just prompts

```

root@notebook: ~# useradd -G admin user
useradd: group 'admin' does not exist 
```

---

### Post by spiderbatdad on 2010-02-24
ok I believe you want to create the group something like so:
```
groupadd -o admin
```

Check out ```
man groupadd
``` if you want to see more options. Then check ```
groups user
``` to make sure your user is in the group.

---

### Post by cronjager on 2010-02-24
But does it help to create a new group that is called admin? The problem is, that a) I have lost my root-access and b) my whole filesystem is writeprotected witch makes me c) startup in recoveryshell and not in X :/

---

### Post by lavinog on 2010-02-24
This seems like an unusual issue.
Was this 64bit or 32bit?
Was the system recently installed?

if you do a hexdump of /etc/sudoers (hd /etc/sudoers) is the first character 23 ('#') and the last 0a?
I have seen a couple of programs corrupt files by putting a non-printable character at the beginning of a text file, which could make reading the file by a program difficult.
This may not be the case here, but it would be good to check just in case.

Also if you are needing a system up quickly, you may want to evaluate if reinstalling would be a better solution to this issue as it may not be an easy fix.

---

### Post by lavinog on 2010-02-24
also can you post /etc/fstab and /var/log/messages

---

### Post by cronjager on 2010-02-24
It was 32bit

The system was installed 4 month ago and has been runing without any problems until yesterday.I've been updating every or every second day using apt-get
 
Hexdump: yes, it looks right. 

What do you mean with posting /etc/fstab and /var/log/messages?

---

### Post by spiderbatdad on 2010-02-24
> **cronjager said:**
> It was 32bit

The system was installed 4 month ago and has been runing without any problems until yesterday.I've been updating every or every second day using apt-get
 
Hexdump: yes, it looks right. 

What do you mean with posting /etc/fstab and /var/log/messages?

concatenate the file with cat command:
```
cat /etc/fstab
cat /var/log/messages
```

Paste results inside code tags.

---

