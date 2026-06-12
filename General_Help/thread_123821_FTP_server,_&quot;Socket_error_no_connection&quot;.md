---
title: "FTP server, &quot;Socket error: no connection&quot;"
date: 2006-01-31
forum: General Help
---

### Post by danscott on 2006-01-31
errors for ftp clients:

---
win32 ftpclient "ftp: connected:10060" (disconnected)
leechftp "!Socket error: no connection"
---

my ftp server (198.53.17.5) cannot ever seem to let a client outside the network connect.

Im using pure-ftpd, and I check out what ports are open, and it only shows 21 for being open, dont I also need port 20?

anyhow...this is terribly frustrating. I have forwarded my required ports, 22, 21, 20, 5900, and 5800.

I even enabled DMZ, i have tried every combination possible with my router, so I know its a problem with the computer itself.

Is there some reason that a ftp server just cant load properly on default with Ubuntu? Or do I need to change something with my iptables...

oh and by the way, I tried SheildUp on the web, and it shows that 20 is totally closed, not even stealth mode like port 21.  then only OPEN port it shows is ssh.

Any help would be great, and if you guys want me to post any info, just tell me...I do anything you need.

---

