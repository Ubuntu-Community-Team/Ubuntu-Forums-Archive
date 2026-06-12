---
title: "file transfer from buntu to me bro windows setip over the web?"
date: 2010-01-21
forum: General Help
---

### Post by soni1770 on 2010-01-21
ok, so i use ubuntu for a while, now i want to
give my  brother some files over the internet
it's from ubuntu to windows, maybe vista
large files, whats some good ways and means to get it set up,
i'm at me bros for the next few days chilling so i got both computers,

can we solve this problems , sweet, 
for those that say google...
this is o only pre emptive swrike, :popcorn:

---

### Post by jamesisin on 2010-01-21
You could create an FTP share on your Ubuntu machine and give your brother access:

[http://www.astahost.com/info.php/Setup-Ftp-Server_t1624.html](http://www.astahost.com/info.php/Setup-Ftp-Server_t1624.html)

(I haven't used this page; I just did a search.)

---

### Post by howefield on 2010-01-21
> **jamesisin said:**
> [http://www.astahost.com/info.php/Setup-Ftp-Server_t1624.html](http://www.astahost.com/info.php/Setup-Ftp-Server_t1624.html)

(I haven't used this page; I just did a search.)

You want him to use a windows application to do ftp on an Ubuntu machine ?

> System Requirements
Windows® 7 (Seven), Windows Vista, Windows Server 2003/2008, Windows XP, Windows 2000/NT (Windows® 7, Vista or XP recommended)
Microsoft® Internet Explorer&#8482; 5.0.0 (Microsoft® Internet Explorer&#8482; 6.0.0 recommended)

Strange choice ...


:lolflag:

---

### Post by jamesisin on 2010-01-21
I need a class on basic copy/paste skills:

[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

Better?

---

### Post by Rob_H on 2010-01-21
I just learned about a [very cool, ridiculously easy way]("http://fosscasts.com/screencasts/5-Command-Line-Tips-2") to throw up a temporary web server for a directory of files. Go to a command prompt, **cd** to the directory you want to serve, and run:

```
python -c "import SimpleHTTPServer;SimpleHTTPServer.test()"
```

Mind you, it provides no security other than the fact that it's restricted to that directory tree, but for a quick transfer, it works well, and you can monitor incoming requests. You'll need to make sure the port is open on your firewall, too.

---

### Post by howefield on 2010-01-21
> **jamesisin said:**
> Better?

No. I don't think so.

Unless I misread the original post, I think the poster will want something more secure as he is sharing over the internet (wan), by the looks of it, your link is more suitable for a home network, (lan).

But I'm working my way through the 10 pages, reading and learning.

---

### Post by jamesisin on 2010-01-21
Securing the 'net is quite different from file sharing.  I would prepare to share files *as though on* a local network, then I would connect (using VPN, SSH, &c).

---

### Post by pricetech on 2010-01-21
Short Answer:  SSH on the Linux box.  winscp on the winders box.  Forward port 22 in the Linux box's router to the Linux box.

---

### Post by jamesisin on 2010-01-21
I've used winscp.  It works pretty well.  You can also ssh from the Windows box using Cygwin (using Bash which is the same shell you are likely using on your Ubuntu box).  At which point you could use scp to copy the files.

---

### Post by junapp on 2010-01-21
[https://www.dropbox.com/](https://www.dropbox.com/)

---

### Post by jamesisin on 2010-01-21
Right, dropbox will allow you to file share.  However, keep in mind that you will be storing your files on someone else's server.

---

