---
title: "Automated Data backup of Ubuntu Linux using Remote Backup software rsnapshot"
date: 2010-08-28
forum: General Help
---

### Post by swamytk on 2010-08-28
rsnapshot is a software written in Perl to make backup of local and remote file system. The well proven rsync is behind this utility. rsnapshot does not need root user intervention to restore the data of a normal user. It does not take much space in your Backup server. It can be easily automated (scheduled) to make life easier. Just setup once and forget it configuration. Basically it takes snapshot of file system (or a part of) in regular interval such as hourly, daily, weekly and monthly. This can be configured easily through a simple text based configuration file.

The above task can be setup in a few easy steps in a few minutes. Two major tasks are configuring rsnapshot and openssh automatic login. To make the backup automatically, we need to automate the remote login in a secured way. This can be done through openssh tools. This scenario depicts backup of desktop (assuming that IP address is 192.168.0.100) data to a backup server. My desktop runs on Ubuntu 10.04 and backup server runs on Debian Squeeze.

Read more: [http://karuppuswamy.com/wordpress/2010/08/28/automated-data-backup-of-ubuntu-linux-using-remote-backup-software-rsnapshot-in-debian/](http://karuppuswamy.com/wordpress/2010/08/28/automated-data-backup-of-ubuntu-linux-using-remote-backup-software-rsnapshot-in-debian/)

---

### Post by K.Mandla on 2010-08-28
Moved to General Help.

---

### Post by QLee on 2010-08-28
> **K.Mandla said:**
> Moved to General Help.
I wonder why, there's no question asked or problem stated, where was this before the move?

---

