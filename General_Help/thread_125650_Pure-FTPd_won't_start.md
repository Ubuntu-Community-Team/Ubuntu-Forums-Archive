---
title: "Pure-FTPd won't start"
date: 2006-02-04
forum: General Help
---

### Post by Dingen on 2006-02-04
Hello. I've followed [this](https://wiki.ubuntu.com/PureFTP) guide to get Pure-FTPd working with the PureAdmin frontend. I've completed all the steps without any errors or warnings or whatever, but I can't get the server to start. From PureAdmin the "start server"-option is disabled and when I try to run it from the console, it says:

```
:~$ sudo pure-ftpd
Unable to start a standalone server: Address already in use
```

What's up? :confused:

---

### Post by dcstar on 2006-02-04
[QUOTE=Dingen]Hello. I've followed [this](https://wiki.ubuntu.com/PureFTP) guide to get Pure-FTPd working with the PureAdmin frontend. I've completed all the steps without any errors or warnings or whatever, but I can't get the server to start. From PureAdmin the "start server"-option is disabled and when I try to run it from the console, it says:

```
:~$ sudo pure-ftpd
Unable to start a standalone server: Address already in use
```

What's up? :confused:[/QUOTE]
Possibly you already have another ftp server daemon running on your system.

What happens when you use a terminal to do:

ftp localhost

---

### Post by qferret on 2006-02-12
Check this out:

[http://ubuntuforums.org/showthread.php?t=9936&page=2&highlight=pure-ftpd](http://ubuntuforums.org/showthread.php?t=9936&page=2&highlight=pure-ftpd)

---

