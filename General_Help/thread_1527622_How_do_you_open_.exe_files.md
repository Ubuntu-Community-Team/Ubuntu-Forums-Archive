---
title: "How do you open .exe files?"
date: 2010-07-09
forum: General Help
---

### Post by computer123 on 2010-07-09
I downloaded Utorrent but its giving me an error. Also do i need an anti virus for Ubuntu?

---

### Post by philinux on 2010-07-09
> **computer123 said:**
> I downloaded Utorrent but its giving me an error. Also do i need an anti virus for Ubuntu?

You would have to install the application Wine from Software Centre or synaptic. Windows .exe files do not run on linux natively. 

Transmission is the default torrent app but there is also Deluge too. Using linux/ubuntu apps is the best way to go.

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Rubi1200 on 2010-07-09
> **computer123 said:**
> I downloaded Utorrent but its giving me an error. Also do i need an anti virus for Ubuntu?

Firstly, utorrent is Windows software. In general, .exe files will not run in Linux unless you are using something like WINE (and, then, not everything will work).

This seems to be the easiest tutorial I could find:

[http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml](http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml)

Regarding anti-virus: people will tell you different things, but the basic answer is no **unless** you are sharing files with a Windows installation or other Windows users.

For general security tips for Ubuntu:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by Turtle.net on 2010-07-09
You'd better use Linux program on a linux machine and leave Windows program on windows machines, don't you think ?
Utorrent can be replaced by Transmission (installed by default).
If you really need to use Utorrent (?) as Phil said you could install wine and then launch the .exe file.

---

### Post by Megaptera on 2010-07-09
Hi,
You can't execute .exe files in Linux. you can use Wine or Cedega for running windows application in Linux.

Re antivirus two links:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

that explain why not.

---

### Post by quimkaos on 2010-07-09
No anti virus needed... this is Linux not windows. The same for .exe files... .exe files are executables/applications for windows not linux. but you can try opening .exe files, or even install applications (games, office, etc), by installing wine: go to synaptic, search wine and install it.

---

### Post by Shompol on 2010-07-09
> **computer123 said:**
> I downloaded Utorrent but its giving me an error. Also do i need an anti virus for Ubuntu?

.exe is a Windows program, it will not run on other systems, such as Mac or Linux. 
Ubuntu supports Debian i386 or AMD64 (depending on your install) executables (aka binaries, supplied as packages).

If you need a torrent program, go to Synaptic manager in Administration or 
  bottom item Applications menu, and pick one  you like.

If you absolutely must run windows .exe, you can use simulator called Wine (free). I actually purchased [http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/), which is a commercially supported implementation of Wine.

Linux has strong security, and is not a popular target for virus makers, so anti-virus is not needed, and you will never have any problems. This is Linux's main selling point -- no malware headaches.

---

### Post by computer123 on 2010-07-09
Thanks for your answers. I should probably scan my computer.

---

