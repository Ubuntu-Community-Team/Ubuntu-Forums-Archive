---
title: "CHROOT Environmnent Setup"
date: 2012-02-29
forum: General Help
---

### Post by csiis on 2012-02-29
I want to allow external connections on port 22 (SSH) to access an internal sftp server. 

Once the user connects i want them to only be able to access one directory where the necessary file will be stored and them be able to copy it to their local server / store.

Im aware of CHROOT and that this can be used, however unsure of how to setup to cater for the above. Any tips or useful guides on this?

thank you

---

### Post by Khayyam on 2012-02-29
> **csiis said:**
> I want to allow external connections on port 22 (SSH) to access an internal sftp server. Once the user connects i want them to only be able to access one directory where the necessary file will be stored and them be able to copy it to their local server / store. Im aware of CHROOT and that this can be used, however unsure of how to setup to cater for the above. Any tips or useful guides on this?

sftp chroot's are fairly simple as there isn't any need to 'jail' all the environment needed for an interactive shell, you just need to decide on a user and/or group.

Openssh-4.9 and up supports chrooting sftp with no additional utilities.

Edit /etc/sshd_config and make sure 'Subsystem sftp' is defined. Then add something like the following.

```
Match User sftpuser # this could match on group its up to you.
ChrootDirectory /home/sftpuser
AllowTCPForwarding no
X11Forwarding no
ForceCommand /usr/lib/openssh/sftp-server
```Create an group and account for 'sftpuser' with '/bin/false' as the shell ..

```
% sudo groupadd sftponly
% sudo useradd sftpuser -g sftponly -d /home/sftpuser -s /bin/false
% sudo password sftpuser
```Create the ChrootDirectory /home/sftpuser and change ownership to root:root ..

```
% mkdir /home/sftpuser && chown root:root /home/sftpuser
```The direcory above (/home) should also be root:root but as this is the default there is no need to go into that unless you've changed it for some reason.

Restart sshd and test the login 'sftp [EMAIL="sftpuser@domain.tld"]sftpuser@domain.tld[/EMAIL], and test its jailed .. then test 'ssh', you should be logged after it accepting the passphrase (if you have '/bin/nologin' set as 'shell' they will get a notice .. /bin/false will just fail and logout).

The sftpuser will be able to upload files in /home/sftpuser, if you wanted you could create a loop image with a filesystem and the file(s) and then mount it read-only as /home/sftpuser, or you could have the files on some other place on the filesystem and 'mount -r --bind /path/to/dir /home/sftpuser'.

I'm kinda working from memory here, but the above should work as expected, let me know if not.

HTH ... khay

---

