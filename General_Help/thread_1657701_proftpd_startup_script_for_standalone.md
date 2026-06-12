---
title: "proftpd startup script for standalone"
date: 2011-01-01
forum: General Help
---

### Post by Whyzer on 2011-01-01
After pretty exhaustive search I've never seen an example of how to make my standalone proftpd server start at boot up. I always have to terminal into /etc/init.d then ./proftpd start it.
I have no skillz in writing scripts, but I haven't seen one ever posted on how to do this.
I am using Ubuntu 10.04, if anyone has done this can you show what your script is or what one might look like please?
Thanks in advance
Jamie

---

### Post by Whyzer on 2011-01-01
Figured it out, just create a symbolic link for proftpd and put it into the rc5.d directory.
For those noobies like me, here's what to do (you can copy paste). 

1) open terminal window.
2) cd/etc/init.d   (enter)
3) sudo cp -s proftpd /etc.init.d/proftpd_start      ( enter password - it has to have a new name so I called mine proftpd_start)
4)sudo mv proftps_start  /etc/rc5.d 

That's it the next time you restart your standalone proftpd server will be up and running.

---

### Post by Whyzer on 2011-12-27
Sorry there was a typo error in there, here's correct way

1) open terminal window.
2) cd/etc/init.d (enter)
3) sudo ln -s proftpd proftpd_start (enter password - this creates the symbolic link with a new name so I called mine proftpd_start)
4)sudo mv proftps_start /etc/rc5.d 

That's it the next time you restart your standalone proftpd server will be up and running.

---

### Post by AJenbo on 2012-01-27
Simpler and less error prone:
[PHP]sudo ln -s /etc/init.d/proftpd /etc/rc5.d/[/PHP]

---

