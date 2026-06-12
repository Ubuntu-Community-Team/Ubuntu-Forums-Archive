---
title: "Ftp"
date: 2010-03-14
forum: General Help
---

### Post by mikbai on 2010-03-14
New to Ubuntu. I'm looking to set up a FTP server. Can anyone point me in the right direction. I have Ubuntu server installed, and would like to test before using it for our corporate environment. Needeless to say, security will be considered a top concern for implemnentation.

So, if someone could tell me the best steps to set it up securely, it would be much appreciated. I'm not much of a CLI user. It's been a while, so I have it booting into GUI mode. Would this be an issue with security. Should we stick to running a system strictly running in CLI mode?

Thanks for the help in advance

---

### Post by blueridgedog on 2010-03-14
This is a bit old, but may get you to the point where you can post specific questions versus a big generic one:

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by Bradj47 on 2010-03-14
> **mikbai said:**
> New to Ubuntu. I'm looking to set up a FTP server. Can anyone point me in the right direction. I have Ubuntu server installed, and would like to test before using it for our corporate environment. Needeless to say, security will be considered a top concern for implemnentation.

So, if someone could tell me the best steps to set it up securely, it would be much appreciated. I'm not much of a CLI user. It's been a while, so I have it booting into GUI mode. Would this be an issue with security. Should we stick to running a system strictly running in CLI mode?

Thanks for the help in advance

I don't see how booting into GUI would be a security issue. Maybe a teeny weeny bit slower but not really a security issue. The only advice I can give on that is to keep it out of GUI mode as much as possible to get slightly better results when connecting to it remotely.

---

### Post by mikbai on 2010-03-14
Thanks for the tips, guys. I found a few things in the meantime that dealt with vsftpd and using Filezilla SSL client. I think I'll play around a bit with that, and see.

Thanks

---

### Post by asmoore82 on 2010-03-14
> **mikbai said:**
> Thanks for the tips, guys. I found a few things in the meantime that dealt with vsftpd and using Filezilla SSL client. I think I'll play around a bit with that, and see.

Thanks

If you use the Filezilla client in combo with SSH server, you don't even need vsFTPd.

The only way old fashioned "FTP" and "secure" fit together is with anonymous FTP.

---

