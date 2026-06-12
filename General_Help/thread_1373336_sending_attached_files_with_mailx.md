---
title: "sending attached files with mailx"
date: 2010-01-05
forum: General Help
---

### Post by yanvolking on 2010-01-05
hello community,

I am a frequent user of mailx.  Formerly it was possible to send attached files using the "-a" option eg. mailx -a /home/yan/textfile [email]recipient@gmail.com[/email].  (I think -a stood for "attached".

At the time the "-a" option figured as an option for sending attached files.  Now it is an option for sending headers.

Can anyone tell me how one can now send attached files using mailx?

Thanks in advance.

y.

---

### Post by yanvolking on 2010-01-07
Hello All,

I found a solution.  The problem is that I had installed mailx.  This has to be replaced by heirloom-mailx

So I removed mailx (sudo apt-get remove mailx).

Then to install heirloom-mailx, I went to 

[http://packages.debian.org/sid/heirloom-mailx](http://packages.debian.org/sid/heirloom-mailx)

There you will find different versions and architectures to suit your particular software configuration.  I chose i386, chose the FTP source nearest to me and installed the application with Gdebi installer.

Now when I run man mailx, the "-a" section states it is for attaching files rather than for sending headers.

Yan

---

