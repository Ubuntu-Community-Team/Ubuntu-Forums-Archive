---
title: "Problems with SFTP using OpenSSH"
date: 2012-08-16
forum: General Help
---

### Post by spazlon on 2012-08-16
I am trying to follow some tutorials on how to set up SFTP using OpenSSH, but locking the users down to their home directory.

I first created a new user:

```
sudo addgroup sftponly
sudo adduser -d /mnt/mass_storage/accounts/testuser -s /bin/false -g sftponly testuser
```

Then I edited my /etc/shells. This is what it looks like now:

```

# /etc/shells: valid login shells
/bin/sh
/bin/dash
/bin/bash
/bin/rbash
/usr/bin/tmux
/usr/bin/screen
/usr/sbin/nologin
/usr/lib/sftp-server

```

Then I edited my /etc/ssh/sshd_config

The end of the file looks like this:

```

Subsystem sftp internal-sftp

Match group sftponly
   ChrootDirectory %h
   X11Forwarding no
   AllowTcpForwarding no
   ForceCommand internal-sftp

```

Everything works if I take that Match group sftponly section out. The problem is that then the users can browse outside of their home directory. I would like them locked down to just their home folder.

When I try to connect with the above settings I get "Connection Refused." This is with all users, via ssh, sftp, etc, and even when I do sftp localhost.

Any guidance on what I'm doing wrong?

Thanks.

---

### Post by SlugSlug on 2012-08-16
```
sudo chown root.root /path/to/home
```

---

