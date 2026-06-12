---
title: "I can't get ftp to work"
date: 2010-11-03
forum: General Help
---

### Post by tech7 on 2010-11-03
I've installed several ftp clients available through the software center.  I'm able to connect to my remote host and view directories, but for some reason every time I try to download my files/directories, it disconnects and doesn't help me at all.  I've got a large remote site so I can't feasibly download each file through my file manager.
Does anybody have any suggestions to get an ftp client working on my computer???

---

### Post by ragtag on 2010-11-03
If you're comfortable with command line, ncftp is pretty solid, and if your remote site supports rsync, that might be an even better choice.

Other than that, I like Filezilla. I used it to download a website a few days ago that was 800mb, and consisted of over 50.000 files. For smaller downloads though, I tend to just use Nautilus.

Are you able to download something at all, or do just get the file listings?

---

### Post by tech7 on 2010-11-03
actually i've been trying to use filezilla, gftp, kftpgrabber..  i've used them on linux boxes before just fine and use dreamweaver at work to connect to this remote host without problems..  i really don't understand what the problem is..  I'm not terribly proficient in terminal, just basic functions..  
So far, I can connect to remote, view files and directories, but as soon as I try to download a file or directory; I lose my connection.  
I was able to download one file though..

---

### Post by tech7 on 2010-11-04
I really don't know where to turn at this point..  I can't get any help on irc..  Can somebody at least point me towards a source where I can get some support for ubuntu?  I've been unable to get any help for this and other issues and I'm not sure what to do at this point.

---

### Post by HpZ on 2010-11-04
[https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)

follow this and forward ports. make sure ports are also allowed through in firewalls (21 should be by default in windows + lunix).

---

### Post by tech7 on 2010-11-06
file permissions

---

