---
title: "reboot using at command"
date: 2011-05-30
forum: General Help
---

### Post by kaykav on 2011-05-30
HI
      I'm trying to schedule a reboot ,using the 'at' command. Normally to reboot  I have to be 'root'. I tried using sudo to start 'at',to no avail.
       How would I type the command ,using at, to reboot?   Thanks

---

### Post by hwttdz on 2011-05-31
You could "sudo shutdown -r hh:mm", or you could make a file containing

#!/bin/bash
/sbin/reboot

and put that in say /root/bin

then "sudo at -f /root/bin/filename now + 10 minute" or whatever.  Not sure if "sudo at -f /sbin/reboot now + 10 minutes" would get the job done.  You can play with it some.  I might make the command "touch /root/at_output.txt", until you get it working right, because otherwise it will be annoying to have the machine constantly rebooting.  

Also, if it's a recurring job, you can just put it in root's crontab.

---

### Post by kaykav on 2011-06-01
Thank you for that input..... some good thoughts!!....

---

