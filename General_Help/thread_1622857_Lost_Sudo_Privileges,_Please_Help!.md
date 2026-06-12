---
title: "Lost Sudo Privileges, Please Help!"
date: 2010-11-16
forum: General Help
---

### Post by tacantara on 2010-11-16
I attempted to use a sudo command on the terminal, and received an error message "/etc/sudoers is mode 0640, should be 0440."  I looked up the problem on this forum, and the suggested solution was to boot in recovery mode, then run the"su -" command to get full root privileges, then chmod the /etc/sudoers file.  That plan didn't work, as it wouldn't take the password I provided for "su".  Is there any other work around, or will I be stuck reinstalling the OS?

System:  Ubuntu 10.10, installed as update rather than a fresh install.  Have had no problems with it up to this point.

---

### Post by yuki-nagato on 2010-11-16
> **tacantara said:**
> I attempted to use a sudo command on the terminal, and received an error message "/etc/sudoers is mode 0640, should be 0440."  I looked up the problem on this forum, and the suggested solution was to boot in recovery mode, then run the"su -" command to get full root privileges, then chmod the /etc/sudoers file.  That plan didn't work, as it wouldn't take the password I provided for "su".  Is there any other work around, or will I be stuck reinstalling the OS?

System:  Ubuntu 10.10, installed as update rather than a fresh install.  Have had no problems with it up to this point.

recovery mode is root.  if you haven't set a password for it, it'll be blank.  sudo and root don't use the same passwords unless you set them to do so.  the su command is used to drop a terminal to root which is redundant here.  you might try editing the file permissions using a live cd.

---

### Post by Rubi1200 on 2010-11-16
Hi,
I don't know if this reflects your situation, but take a look at the advice posted by sisco311 in the following threads:
[http://ubuntuforums.org/showthread.php?t=1352310&highlight=%2Fetc%2Fsudoers+mode+0640%2C+0440]("http://ubuntuforums.org/showthread.php?t=1352310&highlight=%2Fetc%2Fsudoers+mode+0640%2C+0440")
[http://ubuntuforums.org/showthread.php?t=1294356&highlight=%2Fetc%2Fsudoers+mode+0640%2C+0440](http://ubuntuforums.org/showthread.php?t=1294356&highlight=%2Fetc%2Fsudoers+mode+0640%2C+0440)

Hope this helps.

---

### Post by tacantara on 2010-11-16
Thanks for the quick replies yuki and Rubi.  Unfortunately, the blank password on su didn't do it, so I don't recall if I assigned a root password and have merely forgot it now.  Even when I log into a recovery console (which is different, apparently, in 10.10 than in other versions of Ubuntu), I don't get root privileges.  It looks like I'm going to have to dig up a LiveCD and go that route.

---

### Post by Rubi1200 on 2010-11-16
Are you saying that you tried using the guide here and were unable to gain root privileges at all?
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

Did you try this?
[https://help.ubuntu.com/community/RootSudo#root%20account](https://help.ubuntu.com/community/RootSudo#root%20account)

---

### Post by tacantara on 2010-11-16
The psychocats site worked.  I don't know how I overlooked that one before.  I can now sudo as needed.  Thanks for getting me straightened out on that.  Next time, I'll count to 10 before I tackle problems like this....that should prevent me from missing the obvious :)

---

### Post by Rubi1200 on 2010-11-16
Excellent! I am really pleased you got things sorted out :)

---

