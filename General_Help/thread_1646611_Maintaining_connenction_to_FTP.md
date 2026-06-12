---
title: "Maintaining connenction to FTP?"
date: 2010-12-16
forum: General Help
---

### Post by JitsuDan on 2010-12-16
Hi,

I am a web developer and I currently use Windows 7 and a program called PhpEd. This software enables me to connect to an ftp server and edit files directly.

I am trying to move over to Ubuntu as I find Windows 7 to be increasingly slow, however I have one problem which is preventing me from doing so.

When working in PhpEd, the program seems to maintain the connection and when I save the file I'm working on, it just uploads it immediately.

When I try the same thing in Ubuntu, unless I save VERY regularly, the whole thing freezes and becomes unresponsive. I have tried using several different programs and all have given the same results.

Is there anything I can do in order to improve the connection?

Any advice appreciated.

Thanks.

---

### Post by mendhak on 2010-12-16
Which FTP program are you using?  I believe PhpEd would have been sending NOOP commands regularly to the server.  Have you checked if whatever equivalent you're using has an option that specifies the NOOP or a keep alive option?

---

