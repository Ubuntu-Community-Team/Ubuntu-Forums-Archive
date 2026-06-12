---
title: "Time Synchronisation with NTP help"
date: 2010-06-30
forum: General Help
---

### Post by COKEDUDE on 2010-06-30
I followed these 2 guides. 
[https://help.ubuntu.com/9.04/serverguide/C/NTP.html](https://help.ubuntu.com/9.04/serverguide/C/NTP.html)
[http://support.ntp.org/bin/view/Support/GettingStarted?sortcol=0;table=8;up=0#sorted_table](http://support.ntp.org/bin/view/Support/GettingStarted?sortcol=0;table=8;up=0#sorted_table)

I'm curios why I get this message so much. Is there something that you need to check for to deal with Socket in use, or is there another problem? 
```
~ $ sudo ntpdate -b server 0.us.pool.ntp.org 

30 Jun 17:46:32 ntpdate[16248]: the NTP socket is in use, exiting
```

---

### Post by CannibalZerg on 2010-07-01
You have to stop ntp-server (sudo /etc/init.d/ntp-server stop) before  running ntpdate

---

### Post by COKEDUDE on 2010-07-04
> **CannibalZerg said:**
> You have to stop ntp-server (sudo /etc/init.d/ntp-server stop) before  running ntpdate

Wow thats funny. I've just been killing the process and that has been doing the trick for me.

---

### Post by COKEDUDE on 2010-07-05
> **CannibalZerg said:**
> You have to stop ntp-server (sudo /etc/init.d/ntp-server stop) before  running ntpdate

Are you sure you gave the right directory? I couldn't stop it.

---

### Post by COKEDUDE on 2010-07-07
Does anyone know what the ntp directory is?

---

### Post by tgalati4 on 2010-07-08
ls -la /etc/init.d/ntp*

On Hardy, it's just called ntp.  So the command to stop it would be:

sudo /etc/init.d/ntp stop

---

