---
title: "UFW and proFTPD"
date: 2011-03-17
forum: General Help
---

### Post by Darth_tater on 2011-03-17
I can not connect to my ftp server when i have UFW enabled, even if i have the correct passive ports set up and forwarded through ufw.

here is the relevant part of profpd.conf

```


Port                            2112

.
.
.

PassivePorts                  49512 49515


```


and here is ufw:


```

me@myComputer:/etc/proftpd# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
2112/tcp                   ALLOW IN    Anywhere
49512:49515/tcp            ALLOW IN    Anywhere

```


if i disable ufw then everything works perfectly.

i should mention that i can connect, and am asked for my credentials by my FTP client, but once i submit my credentials, i get a time out error.

if i look in the ufw log, i can see that my traffic is being blocked.

my question is *why* is my traffic being blocked?!  the passive ports are allowed in, and ufw does not prevent any outgoing traffic.

thoughts and feedback greatly appreciated!

---

### Post by Lars Noodén on 2011-03-17
> **Darth_tater said:**
> 
thoughts and feedback greatly appreciated!

What is your goal that is met by using FTP?  For FTP you need 20 and 21 open.  

If you can get away with using SFTP instead then you only need port 22 open in UFW.  If you have the package [openssh-server](http://packages.ubuntu.com/maverick/openssh-server) installed then you already have SFTP running and configured.

---

### Post by Darth_tater on 2011-03-17
> **Lars Noodén said:**
> What is your goal that is met by using FTP?  For FTP you need 20 and 21 open.  



i cant use sftp or ssh. i already use it for some things, but this i can't.

and 

did you not see the

> 
here is the relevant part of profpd.conf

Code:

Port                            2112


part of my first post? 

proftd operates on an entirely different set of ports now

---

### Post by Darth_tater on 2011-03-17
Actually, It's working now.

Not sure why, exactly, but the EXACT rules above are now working where they were not before.

ufw blocks all traffic not on those ports, proftpd still works!

---

