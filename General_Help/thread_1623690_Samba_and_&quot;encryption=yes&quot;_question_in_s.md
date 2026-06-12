---
title: "Samba and &quot;encryption=yes&quot; question in smb.conf file"
date: 2010-11-16
forum: General Help
---

### Post by e24ohm on 2010-11-16
Folks:
I am having a hard time understanding a few items about Samba. I have modified my config file, and add "encryption = yes". Does this encrypt password when passed to the Samba server or are passwords still transfered in plain text? 

In addition, I read that "encryption = yes" must be used for Windows to use encryption, if not, Windows will default to plain text password transfer.

I have tried wireshark; however, I am not seeing any password authentication processes.

Right now I am only using SSHFS for file transfers on my home lan; however, I want to be able to use samba for windows.

Thanks.

---

