---
title: "Samba forgets user passwords"
date: 2010-05-10
forum: General Help
---

### Post by tietze on 2010-05-10
Hi
I've just installed 10.04 x64 and I've had some problems with samba (cifs/windows file sharing). It seems like samba is forgetting user passwords, so on every reboot I have to add a password for the user that needs access: **sudo smbpasswd -a tietze**

I've tried restarting samba (**sudo service sbmd restart**), as suggested in the thread below, but it does not work. I have to add a new password for the user with the command above.

I tried to google a bit for a solution, but only found the following thread with a problem that seems related:[** [other] Samba forgets user**]("http://ubuntuforums.org/showthread.php?t=1471925")

Any ideas or suggestions making samba remember passwords betweeen reboots/shutdowns?

---

### Post by tietze on 2010-05-11
Ok - I found out that it was a misconfiguration of my samba server. Apparently I had turned on sync of unix and samba passwords, which was not what I wanted.

For anyone running into this confusion, it is the following lines in the smb.conf the controls this functionality:

```
        unix password sync = yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
```

---

