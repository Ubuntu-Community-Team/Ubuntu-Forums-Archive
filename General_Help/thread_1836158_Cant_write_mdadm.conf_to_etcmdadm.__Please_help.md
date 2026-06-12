---
title: "Cant write mdadm.conf to /etc/mdadm.  Please help"
date: 2011-08-30
forum: General Help
---

### Post by sumasage on 2011-08-30
I am trying to setup a RAID5 array on my server box running a clean install of Ubuntu 11.04 (desktop version 32bits).  The command i used is: sudo mdadm --detail --scan > /etc/mdadm/mdadm.conf

The result is bash: /etc/mdadm/mdadm.conf: permission denied

I have done this when running 10.04 and it worked just fine.  Maybe something changed in 11.04?

---

### Post by rubylaser on 2011-08-30
What are the permissions on the the file?
```
ls -la  /etc/mdadm/mdadm.conf
```

and have you tried to do by becoming the root user?
```
sudo -i
```
enter your password, then this...
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

---

### Post by sumasage on 2011-08-30
It worked!  Thanks for the quick reply.  I just didnt know the command to become root...

---

### Post by rubylaser on 2011-08-30
No problem, you can mark the thread as solved via the Thread tools at the top :)

---

