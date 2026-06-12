---
title: "Losing sudo on SSH"
date: 2012-08-13
forum: General Help
---

### Post by jsnrice on 2012-08-13
The strangest thing has occurred and I can't seem to figure out why. I'm at training for work and have decided to scp all my files to my home server. Everything seems fine, except the fact that when I log in I am not a member of the sudo group any more. When I type 'groups' on the command line, my name comes up along with just one other group 'developers' I'm not sure why SSH strips off this group. As a test (just a test) I tried editing /etc/ssh/ssh_config to allow root login (just a test folks). I can't even log in as root! What am I doing wrong here? :confused:

---

### Post by asmoore82 on 2012-08-13
> **jsnrice said:**
> I tried editing /etc/ssh/ssh_config to allow root login (just a test folks).

1. You'd need to edit "sshd_config", that's ssh<(d)>_config

2. It would only work if the root account is already enabled with a password.

3. You'd have to restart sshd for the change to take effect.

Wait a minute, if you've lost sudo, how in the world did you edit /etc/* ?

---

### Post by jsnrice on 2012-08-13
> **asmoore82 said:**
> 1. You'd need to edit "sshd_config", that's ssh<(d)>_config

2. It would only work if the root account is already enabled with a password.

3. You'd have to restart sshd for the change to take effect.

Wait a minute, if you've lost sudo, how in the world did you edit /etc/* ?

Actually root login was already enabled. It still doesn't let me login as root. When I do log in with my regular user name why am I not on the sudo list? This doesn't make sense.

---

### Post by jsnrice on 2012-08-14
Problem solved. I just used visudo and added my user name to the list under root. Gave myself root privileges. :popcorn:

---

### Post by asmoore82 on 2012-08-14
Again, very confusing... If you had the ability to edit system settings like sudo, then I would think sudo was already working.

---

