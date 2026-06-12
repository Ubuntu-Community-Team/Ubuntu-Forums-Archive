---
title: "How FTP using root?"
date: 2011-08-22
forum: General Help
---

### Post by NCMS on 2011-08-22
I am running Ubuntu 10.40.3  . want to ftp from my Windows XP as  root

Does Ubuntu  have  root  ?

I am a bit confused :confused:

Not to worry about the security, etc., I need to FTP using root, something similar to RedHat

* By the way I am not sure which FTP I am using, whether it is vsftpd, or else !! ( I am new to Ubuntu)

---

### Post by raja.genupula on 2011-08-22
yes , every operation like this needs root

---

### Post by NCMS on 2011-08-22
Can I FTP & logon using  root   to Ubuntu ?

---

### Post by stefangr1 on 2011-08-22
> **NCMS said:**
> Can I FTP & logon using  root   to Ubuntu ?

ftp is an inherently unsafe protocol, as it sends password unencrypted over the net. You should not even consider to use ftp to login on the system with your root account.

There is no need to use root on Ubuntu, as almost everything can be performed using sudo (in fact it's disabled by default, see the [ SudoRoot](https://help.ubuntu.com/community/RootSudo) sticky).

I would recommend you to use sftp. This is part of the ssh suite. If you would like to change a system files that require admin rights, I would recommend the following procedure.

(1) Upload files to a temporary folder using sftp under your normal user account.
(2) Login using ssh. Use sudo to make backups of the system files you want to replace.
(3) Use sudo to replace the old files.

---

### Post by seawolf167 on 2011-08-22
You are FTPing from your Windows box to your Ubuntu box, correct?

If you are using something like [putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/"), you can either use their [psftp ]("http://the.earth.li/%7Esgtatham/putty/latest/x86/psftp.exe")program, or the regular ol' [putty ]("http://the.earth.li/%7Esgtatham/putty/latest/x86/putty.exe")program and start ftp on the remote side via the *ftp* program (or sftp, lftp, etc.)

To run something as root, you should use [*sudo* ]("https://help.ubuntu.com/community/RootSudo")instead. i.e.

```
sudo *command*
```

---

### Post by NCMS on 2011-08-22
[SIZE=3]**stefangr1**[/SIZE]  &  **[SIZE=3]seawolf167[/SIZE]**

THANK YOU big time ..

---

