---
title: "Installing openssl"
date: 2010-07-31
forum: General Help
---

### Post by Frostraver on 2010-07-31
Hi everyone,

I've started using Ubuntu some time ago and now I wanted to try and install
trinitycore. I've done all the steps until I had to install OpenSSL. I've downloaded the packages I wanted but when I give the command to install them it gives the following:

frostraver@ubuntu:~$ sudo dpkg -i libssl0.9.8_0.9.8n-1_i386.deb
dpkg: error processing libssl0.9.8_0.9.8n-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libssl0.9.8_0.9.8n-1_i386.deb

Is there anybody who knows how to fix this?

Thanks,
Frostraver

---

### Post by Bachstelze on 2010-07-31
The package is probably not where you think it is.  Why are you doing that, though?  OpenSSL is in the repos (and installed by default, I believe).

---

### Post by Frostraver on 2010-08-02
I'm trying to install TrinityCore... I did all my updates so it is possible that it's already installed.
How should I know I did that? And if not, what should I do? I'm sure I've downloaded the package so I don't know why he doesn't find it.

---

