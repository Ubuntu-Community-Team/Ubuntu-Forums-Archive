---
title: "Gns3"
date: 2011-06-14
forum: General Help
---

### Post by shamz_71 on 2011-06-14
Hello Geeks ,
I am new to Linux OS. I'm running 11.04 NattyNarwhal  
I have started my CCNA course , and for that i need to run
Cisco Packet Tracer and GNS3 on my laptop. I have no idea how to install them on linux.
Also what do we have in Linux that is  similar to VmWare of windows

---

### Post by Joe of loath on 2011-06-14
[http://www.linuxscrew.com/2007/10/16/running-cisco-packet-tracer-in-linux/](http://www.linuxscrew.com/2007/10/16/running-cisco-packet-tracer-in-linux/)

[http://www.gns3.net/download](http://www.gns3.net/download)

[http://www.vmware.com/](http://www.vmware.com/) or [www.virtualbox.org](www.virtualbox.org)

:D

---

### Post by shamz_71 on 2011-06-15
First Link doesn't work

Second one ...

i wrote "
$ wget [http://gpl.code.de/DB898410.key.pub.asc](http://gpl.code.de/DB898410.key.pub.asc) -O - | sudo apt-key add -"
in terminal , and now i am not able to write anything in terminal...
Im stuck here ...

Anyway the next step is 
"Put the following lines to your */etc/apt/sources.list.d/gpl.code.de.list*: "
Not clear to me

---

### Post by shamz_71 on 2011-06-15
i waiter for so long , then i tried to close the terminal it said some process is running ,still i killed it . 
Ubuntu is still for geeks

---

### Post by shamz_71 on 2011-06-15
some one help me out

---

### Post by Joe of loath on 2011-06-15
> **shamz_71 said:**
> 
"Put the following lines to your */etc/apt/sources.list.d/gpl.code.de.list*: "
Not clear to me

Notice it says 'For Debian' above that? Follow the next section, only for Natty, so

```

# gpl.code.de
deb http://gpl.code.de/ubuntu natty/
deb-src http://gpl.code.de/ubuntu natty/
```

Linux isn't just for Geeks, my grandparents use it ;)

---

