---
title: "how to make hard drive spin down for a long time"
date: 2009-09-30
forum: General Help
---

### Post by markp1989 on 2009-09-30
i wana spin down my mediapc/servers hard drive when not inuse for noise, and power reasons, how do i do this?

i have tried manualy putting hard drive to sleep using hdparm -Y and within secounds of hearing it spin down, i hear it spin up again?

thanks Markp1989

---

### Post by Littleweseth on 2009-10-01
[http://ubuntuforums.org/showthread.php?t=179074](http://ubuntuforums.org/showthread.php?t=179074)

In short : -Y is the wrong switch - try -S. Here's the relevant snippet from man hdparm :

> 
-S
    Set the standby (spindown) timeout for the drive. This value is used by the drive to determine how long to wait (with no disk activity) before turning off the spindle motor to save power. Under such circumstances, the drive may take as long as 30 seconds to respond to a subsequent disk access, though most drives are much quicker. The encoding of the timeout value is somewhat peculiar. A value of zero means "timeouts are disabled": the device will not automatically enter standby mode. Values from 1 to 240 specify multiples of 5 seconds, yielding timeouts from 5 seconds to 20 minutes. Values from 241 to 251 specify from 1 to 11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5 hours. A value of 252 signifies a timeout of 21 minutes. A value of 253 sets a vendor-defined timeout period between 8 and 12 hours, and the value 254 is reserved. 255 is interpreted as 21 minutes plus 15 seconds. Note that some older drives may have very different interpretations of these values. 


It pays to read the manual. :)

EDIT : You will also want to use the 'noatime' mount flag in your /etc/fstab. This prevents linux from writing the access time back to the hard drive every time it reads a file - even if that file was in cache and the hard drive didn't need to spin up to read it in the first place.

- L.

---

### Post by markp1989 on 2009-10-04
i tried setting different spin down values, they never spin down.

is there a program i can use to view and i/o and to see whats using the drive?

edit: i thinkg its to do with writeback delay 
mark@torrentslave:~$ cat /proc/sys/vm/dirty_writeback_centisecs
500

which by defualt is set to 5 seconds. how can i increase it?

i tried 
sudo echo 6000 > /proc/sys/vm/dirty_writeback_centisecs
-bash: /proc/sys/vm/dirty_writeback_centisecs: Permission denied

but im having no luck. 

any pointers will be apriciated .

---

