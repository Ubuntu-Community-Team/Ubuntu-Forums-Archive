---
title: "ZFS: errors with raidz1 pool"
date: 2011-01-29
forum: General Help
---

### Post by dissident69 on 2011-01-29
Hi 
 
I've created a raidz1 configuration zfs storage pool a few months ago. I've been scrubbing the pool once per week without any problems.
 
About a month ago for the first time the scrub resulted in errors being detected and repaired on the third device in the pool. Even though the device appeared to have no problems, I replaced it assuming it to be faulty. The replacement went fine, and everything was okay for a week or two. Then with a brand new device, the same problem started. 
 
I replaced the controller cable (SATA drives) and replaced the drive with the original drive. Ran fine for a week, then same problem. I then connected the replacement drive onto a different controller, having 2 additional SATA ports. After a week, again the same problem. What changes however is that my scrubs are taking longer and longer, the latest one currently sitting at "22541h34m to go". 
 
While scrubbing, the motherboard beeps every 4 seconds or so (with the corresponding output in messages as below)
 
```

root@antares:~# tail -f /var/log/messages
Jan 29 20:26:42 antares kernel: [253321.484644] ata1.01: configured for PIO0
Jan 29 20:26:42 antares kernel: [253321.484672] ata1: EH complete
Jan 29 20:26:48 antares kernel: [253327.281713] ata1: soft resetting link
Jan 29 20:26:48 antares kernel: [253327.472651] ata1.00: configured for UDMA/100
Jan 29 20:26:48 antares kernel: [253327.492659] ata1.01: configured for PIO0
Jan 29 20:26:48 antares kernel: [253327.492679] ata1: EH complete
Jan 29 20:26:52 antares kernel: [253331.281685] ata1: soft resetting link
Jan 29 20:26:52 antares kernel: [253331.468650] ata1.00: configured for UDMA/100
Jan 29 20:26:52 antares kernel: [253331.485141] ata1.01: configured for PIO0
Jan 29 20:26:52 antares kernel: [253331.485168] ata1: EH complete
Jan 29 20:26:56 antares kernel: [253335.281656] ata1: soft resetting link
Jan 29 20:26:56 antares kernel: [253335.488647] ata1.00: configured for UDMA/100
Jan 29 20:26:56 antares kernel: [253335.521703] ata1.01: configured for PIO0
Jan 29 20:26:56 antares kernel: [253335.521735] ata1: EH complete
Jan 29 20:27:00 antares kernel: [253339.281767] ata1: soft resetting link
Jan 29 20:27:00 antares kernel: [253339.472646] ata1.00: configured for UDMA/100
Jan 29 20:27:00 antares kernel: [253339.505527] ata1.01: configured for PIO0
Jan 29 20:27:00 antares kernel: [253339.505559] ata1: EH complete

```
 
Can anyone please provide me with a some guidelines as to how I can ascertain what the root cause of the problem is?
 
The problem only ever occurs on the third device in the pool, and the replacement drive is brand new. Here is some output from various commands I've issued:
 
```

 
root@antares:~# uname -a
Linux antares 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux
 
root@antares:~# zpool status
pool: zfspool
state: ONLINE
see: http://www.sun.com/msg/ZFS-8000-EY
scrub: scrub stopped after 41h20m with 0 errors on Fri Jan 28 18:27:18 2011
config:
NAME STATE READ WRITE CKSUM
zfspool ONLINE 0 0 0
raidz1-0 ONLINE 0 0 0
disk/by-id/ata-ST3500418AS_5VM7LA3C ONLINE 0 0 0
disk/by-id/ata-ST3500418AS_9VM8GSBS ONLINE 0 0 0
disk/by-id/ata-ST3500418AS_9VM8GRFA ONLINE 0 0 2 8.81M repaired
errors: No known data errors
 
[EMAIL="root@antares"]root@antares[/EMAIL]:~# 
 
root@antares:~# zpool iostat -v
capacity operations bandwidth
pool alloc free read write read write
-------------------------------------- ----- ----- ----- ----- ----- -----
zfspool 643G 749G 5 2 571K 10.4K
raidz1 643G 749G 5 2 571K 10.4K
disk/by-id/ata-ST3500418AS_5VM7LA3C - - 2 0 285K 5.49K
disk/by-id/ata-ST3500418AS_9VM8GSBS - - 3 1 285K 5.44K
disk/by-id/ata-ST3500418AS_9VM8GRFA - - 2 0 285K 5.54K
-------------------------------------- ----- ----- ----- ----- ----- -----
[EMAIL="root@antares"]root@antares[/EMAIL]:~# 
 
root@antares:~# zpool status
pool: zfspool
state: ONLINE
see: [http://www.sun.com/msg/ZFS-8000-EY](http://www.sun.com/msg/ZFS-8000-EY)
scrub: scrub in progress for 0h2m, 0.00% done, 22541h34m to go
config:
NAME STATE READ WRITE CKSUM
zfspool ONLINE 0 0 0
raidz1-0 ONLINE 0 0 0
disk/by-id/ata-ST3500418AS_5VM7LA3C ONLINE 0 0 0
disk/by-id/ata-ST3500418AS_9VM8GSBS ONLINE 0 0 0
disk/by-id/ata-ST3500418AS_9VM8GRFA ONLINE 0 0 2
errors: No known data errors
root@antares:~# 
&#12288;
root@antares:~# tail -f /var/log/messages
Jan 29 20:26:42 antares kernel: [253321.484644] ata1.01: configured for PIO0
Jan 29 20:26:42 antares kernel: [253321.484672] ata1: EH complete
Jan 29 20:26:48 antares kernel: [253327.281713] ata1: soft resetting link
Jan 29 20:26:48 antares kernel: [253327.472651] ata1.00: configured for UDMA/100
Jan 29 20:26:48 antares kernel: [253327.492659] ata1.01: configured for PIO0
Jan 29 20:26:48 antares kernel: [253327.492679] ata1: EH complete
Jan 29 20:26:52 antares kernel: [253331.281685] ata1: soft resetting link
Jan 29 20:26:52 antares kernel: [253331.468650] ata1.00: configured for UDMA/100
Jan 29 20:26:52 antares kernel: [253331.485141] ata1.01: configured for PIO0
Jan 29 20:26:52 antares kernel: [253331.485168] ata1: EH complete
Jan 29 20:26:56 antares kernel: [253335.281656] ata1: soft resetting link
Jan 29 20:26:56 antares kernel: [253335.488647] ata1.00: configured for UDMA/100
Jan 29 20:26:56 antares kernel: [253335.521703] ata1.01: configured for PIO0
Jan 29 20:26:56 antares kernel: [253335.521735] ata1: EH complete
Jan 29 20:27:00 antares kernel: [253339.281767] ata1: soft resetting link
Jan 29 20:27:00 antares kernel: [253339.472646] ata1.00: configured for UDMA/100
Jan 29 20:27:00 antares kernel: [253339.505527] ata1.01: configured for PIO0
Jan 29 20:27:00 antares kernel: [253339.505559] ata1: EH complete
&#12288;
 

```
 
Any help would be greatly appreciated.

---

### Post by iposner on 2011-03-25
You were right to change the drives and cables, but if the problem persists with different drives and cables connected to the same port, your disk controller is probably faulty. If it's part of the motherboard then you'll need new motherboard.

This is a far less common fault than a faulty disk, but it does occur.

---

