---
title: "SFTP over SSH"
date: 2012-10-02
forum: General Help
---

### Post by hhaydoura on 2012-10-02
I hear this expression quite a lot lately and I still dont know how this is possible to have sftp over ssh :( well I rly want to know how this works theoretically and practically :)  thanks guys

---

### Post by 2F4U on 2012-10-02
SFTP = **S**SH **F**ile **T**ransfer **P**rotocol. See

[http://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol](http://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol)

---

### Post by Lars Noodén on 2012-10-02
Practically, you can use the text-based SFTP client in the shell by opening a terminal and entering [sftp](http://manpages.ubuntu.com/manpages/precise/en/man1/sftp.1.html) plus the address of the server you are connecting to.

```

sftp -l hhaydoura *xx.yy.zz.aa*

```

Or you can use your file manager, either Dolphin or Nautilus.  In either you can press ctrl-L or in Nautilus choose the menu File->Connect to Server->SSH.  That will give you a graphical interface to work with.

---

