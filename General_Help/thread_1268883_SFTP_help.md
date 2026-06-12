---
title: "SFTP help"
date: 2009-09-17
forum: General Help
---

### Post by alexlaban on 2009-09-17
I want to be able to access some files from outside my network. But there's one thing. I'm a bit paranoid and normal ftp isn't good enough for me. I only want to be able to use one account over sftp which can only READ files in one folder and not edit or change anything on my server. So even if someone somehow got my 24character long password, they still wouldn't be able to do anything more than read and download the files from that folder, no ssh commands or anything. So is this possible and if yes how? Security is always priority number one for me.

---

### Post by joe2012 on 2009-09-17
Why don't you create a user with ssh access, but has no access to anything else except for what's in their home folder?

---

### Post by sedawk on 2009-09-17
With normal FTP the solution is to use "chroot", so that the
ftp user can only see a subdirectory and cannot escape outside
that small world you allow him to see.

So what you are looking for is "chroot SFTP" or "chroot SCP".

This seems to be some good piece of documenation:
[http://www.minstrel.org.uk/papers/sftp/](http://www.minstrel.org.uk/papers/sftp/)

It seems that it gets easier with brand new versions
of openssh because they now added support for limited
access.

---

### Post by alexlaban on 2009-09-17
> **joe2012 said:**
> Why don't you create a user with ssh access, but has no access to anything else except for what's in their home folder?

I alread got a folder with the files I a want to be able to access, it's the same folder which I use as a file server at home.

---

### Post by alexlaban on 2009-09-19
Well still not getting it to work, problem is that I want to be able to have full ssh access over the internal network but only this sftp read files from one folder access over internet.

---

