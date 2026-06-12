---
title: "SSH - chroot and sftp restrictions"
date: 2012-06-13
forum: General Help
---

### Post by porchrat on 2012-06-13
Hi all

I've used SSH a fair amount in the past and I find it very useful.

I'm now trying to see if I can setup a more restricted SFTP server for some other folks that need to get and put some files on my system.

From what I have read it seems most people use chroot and restricting the shell to sftp only.

I've followed a few guides and while I have succeeded in setting up a simple SFTP only shell for a user I am having trouble getting chroot to work properly.

I have received a myriad of errors including that it can't find the file or directory "usr/lib/openssh/sftp-server" despite it being there in the directory I have assigned as the root directory in sshd_config.

Anyone have any tips or advice or links to guides/tutorials that might be of some help?

---

### Post by Habitual on 2012-06-13
I have some note snippets from my ftp-over-gluster install that I had to lock down (prevent ftp 'users' from even seeing other ftp users' directories...).

I abandoned chroot for this access. For "some reason" (wink/nudge) I just couldn't 'hide' those other dirs via FileZilla)

These snippets are not in sequence or even complete. It is merely a (hopeful) clue... :)

```
-== ftp (ftp jail)
valicore:x:501:502::/mnt/gdata/clouds/cloud_valicore:/bin/bash
vi /etc/vsftpd/vsftpd.conf and uncomment #chroot_list_enable=YES
vi /etc/vsftpd/chroot_list and add valicore
chkconfig --levels 235 vsftpd on
service vsftpd start

-== disable sftp ==-
vi /etc/ssh/sshd_config and insert a comment at Subsystem sftp /usr/lib/openssh/sftp-server
/etc/init.d/sshd restart
sftp disabled.

-== Prevent sftp for clients (sftp issue via FileZilla with 'seeing' others' clouds) ==-
vi + /etc/ssh/sshd_config
AllowUsers root c9admin
DenyUsers valicore
service sshd restart
```

This allows regular **ftp only** and should keep them from navigating around and viewing what they shouldn't even see.
Don't ask me why I did it "that way" b/c I couldn't tell you!

Subscribed with interest...

---

### Post by porchrat on 2012-06-13
I can't rely on ordinary FTP it has to be secure. FTPS at the very least but SFTP would be preferable. I also don't want the user being able to look around the rest of the system.

I actually just now managed to get sftp-only chroot running and it seems to work great.

I am hardly a security expert so now that I finally have this figured out I need some further guidance. Is there a way for a user to escape chroot under the following circumstances:
[LIST]
[*]Not on the sudoers list
[*]In an sftp shell
[*]on an SSH server that doesn't permit root login
[/LIST]

---

