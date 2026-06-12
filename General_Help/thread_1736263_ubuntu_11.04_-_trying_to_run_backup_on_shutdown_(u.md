---
title: "ubuntu 11.04 - trying to run backup on shutdown (upstart-script)"
date: 2011-04-22
forum: General Help
---

### Post by _-LC-_ on 2011-04-22
Hello, I'm trying to run a script that will backup my data on shutdown/reboot (while the root filesystem is still mounted).
I have this basic skeleton:
root@mypc:/etc/init# cat backup.conf 
description "make backup on shutdown or reboot"

start on runlevel [06] and (filesystem-mounted until filesystem-unmounted)

console output

script
echo "hey" > /home/myhome/i_ran.txt"
end script
root@lcpcl:/etc/init#

It never runs...
I read the documentation up and down, but I couldn't get it to run at the right time.
Thanks for your help!

---

### Post by deckoff on 2011-05-01
BUMP!
I want to run a script at start up and shut down and fail with 11.04 
I have this script 
```

#!/bin/bash


umount -f /media/MyBookLive

exit 0


```

I have added it in /etc/init.d , than added links in /etc/rc0.d and /etc/rc6.d. It worked well for 10.10 but stopped after upgrade. it seems upstart is updated, and this is the main reason for the problem


I use it to umount my NAS drive to prevent the system from hanging. With natty upgrade it does not work anymore....

I would love to know what have changed

---

