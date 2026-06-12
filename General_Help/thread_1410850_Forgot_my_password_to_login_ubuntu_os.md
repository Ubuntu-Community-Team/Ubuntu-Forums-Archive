---
title: "Forgot my password to login ubuntu os?"
date: 2010-02-19
forum: General Help
---

### Post by subakaran on 2010-02-19
Hi all,
I opened my note book.
I have installed XP,Ubuntu.
when i boot, i select ubuntu os.
But I forgot my Password.
How to recovery or reset my password?
please advise me.
Thanks..

---

### Post by sisco311 on 2010-02-19
Reboot into *Recovery Mode* & reset your password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by r_s on 2010-02-19
In that tutorial , when you select to go on to the root prompt, it asks for the root password, so if one has forgotten the root password that won't work.I presume that is a way to make it sure that no unauthorized access is allowed.

---

### Post by subakaran on 2010-02-19
Hi ,
I follow ur link.
I choose , drop to root shell.
shell propt opens . but it asked login to webmaster notebok.
it asked username & password.

Please, reply to me.
I used Ubuntu 9.10

Thanks..

---

### Post by sisco311 on 2010-02-19
> **r_s said:**
> In that tutorial , when you select to go on to the root prompt, it asks for the root password, so if one has forgotten the root password that won't work.I presume that is a way to make it sure that no unauthorized access is allowed.

Only if you have set a root password. By default, the root account password is locked. sulogin is patched to handle the default case of a locked root password, it drops you to a root shell without prompting for a password. 

> **subakaran said:**
> Hi ,
I follow ur link.
I choose , drop to root shell.
shell propt opens . but it asked login to webmaster notebok.
it asked username & password.

Please, reply to me.
I used Ubuntu 9.10

Thanks..

That's weird.


At the Grub menu highlight the recovery mode option,

press e for edit, 

remove the **ro single** kernel parameters form the end of the **linux** line,

append the line with **rw init=/bin/bash**,

press Ctrl+x to boot.

Wait for all the boot-up processes to finish.

Make sure that the root ("/") partition is mounted rw:
```
mount -o remount,rw /
```
 
Run:
```
passwd **username**
```to reset your password (replace **username** with your login name).

Press Ctrl+Alt+Del to reboot.

---

