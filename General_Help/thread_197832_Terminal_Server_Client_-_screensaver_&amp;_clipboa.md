---
title: "Terminal Server Client - screensaver &amp; clipboard help"
date: 2006-06-16
forum: General Help
---

### Post by drfox on 2006-06-16
At my office, I use Terminal Server Client/Remote Desktop to log onto a Windows 2003 Server. Everything works fine except for 2 things: I can't share my clipboard between Ubuntu and Windows, and the Gnome screensaver locks the entire system when it turns on. 

Is there a way to share the clipboard between Ubuntu and Windows?

Would xscreensaver work better than gnomescreensaver?

Thanks.

Larry

---

### Post by betawind on 2007-10-18
Run rdesktop from a command line (or put it in a shell script and sudo chmod +x <file>) with the "-r clipboard:PRIMARYCLIPBOARD" option.  You will want to configure the plethera of other options as well, but this will get your clipboard working.  Also, I dont know if this makes a difference, but im running rdesktop 1.5.  I did *not* see this option in the tsclient, but it looks like you can run it w/ the -x FILE option to run it with the parameters outlined in FILE.

Hope this helps, 

Beta

---

### Post by OpenMinded on 2008-06-09
I saw a very handy tip here to fix your clipboard, namely by using the RDPv5 protocol when connected.
Confirmed working on Ubuntu 8.04 with Windows Terminal Server 2003.

[http://www.giannistsakiris.com/index.php/2007/10/04/shared-clipboard-with-terminal-server-client-on-ubuntu/](http://www.giannistsakiris.com/index.php/2007/10/04/shared-clipboard-with-terminal-server-client-on-ubuntu/)

hope that helps :)

---

