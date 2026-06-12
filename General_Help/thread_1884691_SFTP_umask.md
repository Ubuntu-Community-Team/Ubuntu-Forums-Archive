---
title: "SFTP umask"
date: 2011-11-21
forum: General Help
---

### Post by synexis on 2011-11-21
Hello, I am new here, so I hope I'm posting in the right place and all that.

I have exhausted my search capabilities in trying to set the umask for SFTP sessions.

There seems to be two general solutions offered on various forums, neither of which are working for me.

The first is to use a special umask flag within /etc/ssh/sshd_config, as follows:
Subsystem sftp /usr/lib/openssh/sftp-server -u 0002

The second is to create a wrapper script around the sftp-server process:
I tried creating a shell script /usr/lib/openssh/sftp-server.sh with:
```
#!/bin/bash
umask 0002
/usr/lib/openssh/sftp-server
```... then telling sshd_config to use that:
Subsystem sftp /usr/lib/openssh/sftp-server.sh

(and of course restarting ssh with either solution)

I know the script was executed as I also tried echoing a statement to a text file. And, I also tried using "002" instead of "0002". But, whenever I create a new file via SFTP it still has 755 permissions.

I'm running Ubuntu 11.04 with OpenSSH 5.8p1 and OpenSSL 0.9.8o.

I've been slowly loosing my sanity working on this today. Any ideas would be greatly appreciated.


----- SOLVED -----

I hope this can save someone else hours of frustration...

If you're using a GUI SFTP application, check its preferences for setting permissions on upload.

It turns out the application was just overriding all the things I tried earlier.

---

