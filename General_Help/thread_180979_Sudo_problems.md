---
title: "Sudo problems"
date: 2006-05-23
forum: General Help
---

### Post by cosborn72 on 2006-05-23
Running Breezy  Kernel 6.2.12-10.386

I am having a problem with sudo.  Everytime I try to sudo something, I get a message saying

sudo: no passwd for root!

here is the exact message

chris@cprcd01:~$ sudo nano /etc/fstab
sudo: no passwd entry for root!
chris@cprcd01:~$ sudo mount -a
sudo: no passwd entry for root!
chris@cprcd01:~$ mount -a
mount: only root can do that
chris@cprcd01:~$

I use to be able to do this, and I don't know of one particular thing that has changed.  It just started doing this one day.

THere is nothing in the syslog that suggests a problem.
Any ideas?

From the Gnome desktop, when I try to open anything requring sudo- synapic, user manager, etc -nothing happens

I'm also getting a HAL error, which I suspect is due to a smbfs entry in fstab, but I can't get rw access, because I can't sudo it.

---

### Post by spamzilla on 2006-05-23
Try "sudo passwd root", then follow the onscreen instructions :)

---

### Post by cosborn72 on 2006-05-23
Here are the latest contents of my auth.log
I don't think it is helpful.


May 23 10:28:43 localhost gdm[6166]: (pam_unix) session opened for user administrator by (uid=0)
May 23 10:29:53 localhost sudo: administrator : no passwd entry for root!
May 23 10:30:31 localhost gdm[6166]: (pam_unix) session closed for user administrator
May 23 10:30:48 localhost gdm[6166]: (pam_unix) session opened for user administrator by (uid=0)
May 23 10:34:22 localhost gdm[6166]: (pam_unix) session closed for user administrator
May 23 10:34:41 localhost gdm[6166]: (pam_unix) session opened for user stephanie by (uid=0)
May 23 10:42:34 localhost sshd[4194]: Accepted password for chris from 192.168.1.112 port 55902 ssh2
May 23 10:42:34 localhost sshd[4206]: (pam_unix) session opened for user chris by (uid=0)
May 23 10:43:13 localhost sudo:    chris : no passwd entry for root!
May 23 10:43:28 localhost sudo:    chris : no passwd entry for root!
May 23 11:15:35 localhost sshd[4206]: (pam_unix) session closed for user chris
May 23 11:17:36 localhost sshd[4641]: Accepted password for administrator from 192.168.1.112 port 34442 ssh2
May 23 11:17:36 localhost sshd[4661]: (pam_unix) session opened for user administrator by (uid=0)

---

### Post by cosborn72 on 2006-05-23
No luck with that.

administrator@cprcd01:~$ sudo passwd root
sudo: no passwd entry for root!
administrator@cprcd01:~$ passwd root
passwd: Unknown user root
administrator@cprcd01:~$ su

---

