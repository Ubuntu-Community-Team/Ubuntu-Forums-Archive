---
title: "How to access common ftp user's home"
date: 2010-02-28
forum: General Help
---

### Post by portabill on 2010-02-28
I have a person system at home running vsFTP for my own purposes.  I created a ftp-specific user and configured vsFTP to only allow that user to connect.  

I don't know how to set the permissions so that my user can freely access the ftp user's home folder.  I tried sudo chmod 0777 /home/ftpuser , but no luck.

Thanks

---

### Post by dcstar on 2010-02-28
> **portabill said:**
> I have a person system at home running vsFTP for my own purposes.  I created a ftp-specific user and configured vsFTP to only allow that user to connect.  

I don't know how to set the permissions so that my user can freely access the ftp user's home folder.  I tried sudo chmod 0777 /home/ftpuser , but no luck.


It breaks the security model to change a user's top level folder so that gets reset automatically AFAIK, but you should be able to change any folder you create **under** that folder.

---

### Post by asmoore82 on 2010-02-28
I would dump FTP in favor of sftp.

All you have to do is run the openssh-server and you have sftp,
I would guess you already have done this if you went through the
trouble of setting up vsFTPd.

sshd opens only 1 port, number 22, and allows remote shell access, sftp,
rsync, and X11 forwarding all ***very* securely**.

You can even mount your remote sftp shares graphically in
"Places -> Connect to server" - just choose "SSH" as the "Service Type"

You can access sftp from that other OS with "Filezilla" -
just tell it port 22 and it knows what to do.

---

### Post by portabill on 2010-03-01
Old habits die hard.  I'll try the FileZilla option on the client servers to see what kind of access I have through the firewalls.  I'll search for the openssh-server install and config to see why I'm not connecting.

Thanks

---

