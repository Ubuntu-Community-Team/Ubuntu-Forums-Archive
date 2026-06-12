---
title: "SVN and ChrootDirectory"
date: 2011-10-15
forum: General Help
---

### Post by Phonicx on 2011-10-15
I'm using Ubuntu Server 11.10 and I'm not sure if what I'm trying to do is possible.

I've set up Subversion with a repository in the /home directory and I've also setup an sftp folder in the /home directory. I'm using SSH to connect to both of them from the client side and it works fine.

I wanted to have some users Chroot'd to the /home directory though so I added the following lines to my sshd_config file.

```
Match group workers
        ChrootDirectory /home
        X11Forwarding no
        AllowTcpForwarding no
        ForceCommand internal-sftp

```These users can still access the sftp fine, but they are refused access to the subversion repository.

Is what I'm trying to do possible? Have I gone about it the wrong way?

Thanks.

---

