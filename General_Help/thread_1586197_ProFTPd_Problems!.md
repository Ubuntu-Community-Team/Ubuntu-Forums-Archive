---
title: "ProFTPd Problems!"
date: 2010-10-01
forum: General Help
---

### Post by TaekOnai on 2010-10-01
[Solved] I solved this problem by downloading the deb packaged and installed it that way


Hi folks, first off the problem is i get a 530 error for user login in proftpd.

System Specs:
Ubuntu 9.10 Server Karmic
Host: HostV
Access: SSH2

I install proftpd just as everyone else does, via apt-get install proftpd. During the installation process i receive an error which i perceive as the possible error for this not working properly.
I've tried several times to install/uninstall/install and nothing seems to make it work. I have trolled several forums found through google and not one of the posts seems to have this error with installation. I've tried to manually configure a user account (proftpd) set a /bin/false and a bin/nologin in the etc/shells and nothing seems to work.

Right now i have it installed with the error below and a default proftpd.conf file.

Installation Error:
```
Preconfiguring packages ...
Can't exec "/tmp/proftpd-basic.config.71821": Permission denied at /usr/share/perl/5.10/IPC/Open3.pm line 168.
open2: exec of /tmp/proftpd-basic.config.71821 configure  failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
proftpd-basic failed to preconfigure, with exit status 255
```Expected Results: Successful ftp login for a shell account holder

Received results:
530 Login incorrect.
Error:    Critical error
Error:    Could not connect to server

Any help is appreciated.

Thanks

---

