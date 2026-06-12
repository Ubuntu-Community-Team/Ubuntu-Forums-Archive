---
title: "can't login after attempt at openafs install"
date: 2010-09-06
forum: General Help
---

### Post by demba on 2010-09-06
Hi all,

I'm running Kubuntu 9.10. In the process of trying to
install openafs, I messed w/ /etc/pam.d/common-auth and
/etc/pam.d/common-session. So, now I can't login to my
machine. Loging in using the console gives the message

module is unknown

I'm unable to log in in recovery-mode: the system freezes
at the recovery menu.

Thoughts? Thx.


Demba.

---

### Post by demba on 2010-09-06
bump

---

### Post by demba on 2010-09-06
If anybody cares, I fixed the problem after a bit of mud-wrestling.

The solution involves a combination of booting with the LiveCD, mounting the partition on which kubuntu is installed and then playing with some of the instructions in

[http://ubuntuforums.org/showthread.php?t=1150786](http://ubuntuforums.org/showthread.php?t=1150786)

$ sudo pam-auth-update --force

This did it for me (I selected the 1st option "Unix...") and
then typed

$ passwd

and reset my psswd


Demba.

---

