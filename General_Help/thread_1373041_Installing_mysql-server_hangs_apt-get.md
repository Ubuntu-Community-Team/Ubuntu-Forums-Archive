---
title: "Installing mysql-server hangs apt-get"
date: 2010-01-05
forum: General Help
---

### Post by Winterhart on 2010-01-05
I'm trying to install DekiWiki, which has as a dependency mysql-server.

This is what's going on:
```

root@servername:~# apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  mysql-doc-5.0
Recommended packages:
  apparmor libhtml-template-perl mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 40 not upgraded.
Need to get 27.5MB of archives.
After this operation, 86.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy-updates/main mysql-server-5.0 5.0.51a-3ubuntu5.4 [27.4MB]
Get:2 http://us.archive.ubuntu.com hardy-updates/main mysql-server 5.0.51a-3ubuntu5.4 [54.2kB]
Fetched 27.5MB in 14s (1877kB/s)
Preconfiguring packages ...
(Reading database ... 39317 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb) ...

```

And there it hangs.  All night, as a matter of fact - I left it going just in case it was for some reason a really gigantic package.

Do you think this package might be corrupted, and if so can I manually specify a different version or a different package?  I don't know what else to do; ctrl+c to kill it results in dpkg hangups that yeah, I can purge, but I'd rather not be doing that more than is really necessary.

---

### Post by kakyoism on 2010-09-04
I have the same problem and it's not just one package but all of them. 
I tried to upgrade Chromium, installing Deluge... everything hangs at the "Unpacking". 

Anyone please help?

On lucid I've had great experience, but something fundamental like this bit me in my ***...making me really want to turn away from ubuntu...

---

### Post by kakyoism on 2010-09-04
I think this dependency problem happens just in August.

---

