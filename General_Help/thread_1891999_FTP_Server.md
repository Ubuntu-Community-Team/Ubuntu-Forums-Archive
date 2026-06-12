---
title: "FTP Server"
date: 2011-12-07
forum: General Help
---

### Post by Swashbunglar on 2011-12-07
I'm looking for an ftp server that will get what I need done without needing local users or anonymous access.

I want to create ftp user with access ONLY to their website  (/var/www/this_site), so they can manage files for their site without  touching anything else.

So far all I've seen are outdated and complicated "tutorials" or  virtually no documentation on how to configure users and directories.

Any ideas?

Ubuntu Server 10.04 x64

---

### Post by DapperMe17 on 2011-12-07
Look here...

[http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by Lars Noodén on 2011-12-07
Look at the [ChrootDirectory](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) configuration directive for OpenSSH-Server.  It will allow you to chroot SFTP sessions. SFTP is a secure alternative to [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).

---

