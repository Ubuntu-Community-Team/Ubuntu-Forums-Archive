---
title: "ssh on bootup ?"
date: 2011-07-17
forum: General Help
---

### Post by swedishbriefs on 2011-07-17
hi all,

can someone advise what i may be doing wrong ?
im using 10.04,,
i can start ssh using init.d ... and connect via windows putty.
problem is when i down/up power my ubuntu box ssh doesnt come back up...

ive got to up it again locally - !which is very inconvienent and involves a trip to site.

ive read a couple forums which suggest that in
/etc/init/ssh.conf, i enter the following  "filesystem and net-device-up IFACE=eth0)" - this apparently sets ssh to start up only when the network is ready .


also

in etc/ssh/sshd_config - enter the listening address as 0.0.0.0 -






none the above works - can anyone suggest how i might find the fault ?- could someone a suitable way of enabling ssh on startup..

btw ,,

im currently using sysv-rc-conf and have found ssh - and "crossed out" the appropiate start up levels.


- although , again , on another forum it suggests that although ssh maybe listed in the  sysv-rc-conf files - editing the ssh tables has no effect ..

---

### Post by ajgreeny on 2011-07-17
I am afraid I am lost.  Do you mean that the ssh-server does not start at boot, or the connection from host to server does not open automatically?

The sysv-rc.conf does not have any effect for most things any more as many services are started by upstart scripts and are not using init scripts.  I have not understood yet how to deal with this automatically at boot, apart from adding command lines to /etc/rc.local, but I suspect there may be easier or better ways to deal with this problem.

I may have been unsuccessful, but you may have more luck finding out how to do this.

---

### Post by Wayne_V on 2011-07-17
If it is starting when you do "initctl restart ssh" but not on boot it is probably something to do with the network not being ready.   Until you figure it out you could try adding:


/sbin/initctl restart ssh | at now+5min

to /etc/rc.local  as a workaround.


One thought -- the network does start on boot and not only when you log in, right?   Is this Ubuntu server or desktop?

---

