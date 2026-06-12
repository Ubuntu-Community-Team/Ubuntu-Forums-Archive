---
title: "Ubuntu SSH Tunneling"
date: 2012-01-30
forum: General Help
---

### Post by techinterplay on 2012-01-30
Hi All,

I am provided with a Windows 7  machine at my work place and I run ubuntu on Virual machine. We are  also provided with a Windows 2003 server which we RDP from our  windows7/virtual ubuntu machine and access Linux servers with the help  of putty. So Windows 2003 server act as a launchpad to access Linux  servers. I am thinking about some 'workaround' by which I can access/ssh  these Linux servers from my Virtual ubuntu machine without manually  logging into the windows 2003 server. Is there any way I can achieve  this, with the help of port forwarding or something? I have no clue  about this [IMG]http://i.hexindia.net/nixcraftcom/images/smilies/icon_sad.gif[/IMG] If I should be more elaborative, please let me know [IMG]http://i.hexindia.net/nixcraftcom/images/smilies/icon_smile.gif[/IMG]

Many thanks in advance.

---

### Post by josephmills on 2012-01-30
> **techinterplay said:**
> Hi All,

I am provided with a Windows 7  machine at my work place and I run ubuntu on Virual machine. We are  also provided with a Windows 2003 server which we RDP from our  windows7/virtual ubuntu machine and access Linux servers with the help  of putty. So Windows 2003 server act as a launchpad to access Linux  servers. I am thinking about some 'workaround' by which I can access/ssh  these Linux servers from my Virtual ubuntu machine without manually  logging into the windows 2003 server. Is there any way I can achieve  this, with the help of port forwarding or something? I have no clue  about this [IMG]http://i.hexindia.net/nixcraftcom/images/smilies/icon_sad.gif[/IMG] If I should be more elaborative, please let me know [IMG]http://i.hexindia.net/nixcraftcom/images/smilies/icon_smile.gif[/IMG]

Many thanks in advance.

Bridge you networkadapter on you virtual machine (settings network ) then open a linux server whatever one. then do a ifconfig look at the ipaddress then do a ```
nano /etc/ssh/ssh_config 
``` also look at /etc/ssh/sshd_config these are the two settings "menus"  for ssh  this is where you change your port and what not. then you can also use suth keys also there you can read more about that[HERE.](http://www.debian-administration.org/articles/530) hope this helps let us know. thanks

---

### Post by techinterplay on 2012-02-08
Hi Joseph,

Thank you for your reply. Could you please make this clear for me? My VPS is already bridged to my Host machine which is Windows 7. But I have no route to Linux server from both my host machine (Windows 7) and Ubutnu VM. I have only access from the Windows 2003 server which I access using RDP from Windows 7.

This is how it goes Ubutnu -> Windows 2003 -> Putty -> Linux server. I want to avoid logging into the Windows 2003 which is in-between me and the Linux servers. :)

Regards,
Faheem.

---

### Post by levidurfee on 2012-02-08
Sounds like you need a reverse tunnel. 

This [http://www.howtoforge.com/reverse-ssh-tunneling](http://www.howtoforge.com/reverse-ssh-tunneling) can probably explain it better than I can.

Hope this helps.

---

