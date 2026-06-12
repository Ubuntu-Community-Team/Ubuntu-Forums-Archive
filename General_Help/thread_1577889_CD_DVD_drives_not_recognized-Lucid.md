---
title: "CD DVD drives not recognized-Lucid"
date: 2010-09-19
forum: General Help
---

### Post by Flyboy712 on 2010-09-19
Since my upgrade to lucid from karmic I have not been able to use my CD or DVD drives on my computer.  They show up in Places > Computer but I cannot click on them it does nothing when I insert a CD or DVD into the drives they spin up, the lights flash and then nothing.  I can boot from both drives but once the OS is up and running then the computer shows them as being there but when I try to access them either nothing happens or I get a message saying they dont exist??  I have seen many other threads about this all over the internet but no solutions yet that have worked for me....  I have reported a Bug and still waiting????  [https://bugs.launchpad.net/bugs/605716](https://bugs.launchpad.net/bugs/605716)  

Here is the output of lshw -c disk:

*-cdrom:0               
       description: DVD reader
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio dvd
       configuration: status=open
  *-cdrom:1
       description: DVD-RAM writer
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open

Any Help would be appreciated as the next step is a complete system backup, reinstall, and reconfiguration which I am dreading!!

Without functioning CD/DVD drives there is little functionality in my computer.

Thanks,
Mike

---

### Post by Flyboy712 on 2010-09-23
Bump

Anything??

---

### Post by Flyboy712 on 2010-10-06
I just downloaded and installed the Maverick Kernel and so far everything seems to be working perfectly I'll keep you all posted on what happens.

---

