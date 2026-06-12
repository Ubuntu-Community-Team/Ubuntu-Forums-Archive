---
title: "Problem with startup script"
date: 2011-05-25
forum: General Help
---

### Post by ankeetg on 2011-05-25
Hey!

I'm having a problem, as a command I've entered in a script isn't working (I think).

I have 3 machines connected in a LAN all running Ubuntu 11.04.

One machine serves as the NFS and is always powered on.

My objective: When I switch on the other machines it should execute the following code:

> 
sudo mount NFS: /home/user/NFS /home/user/mountdir
I first entered this command in the /etc/rc.local file and it didn't work.

Thinking that rc.local might not provide root functionality, I also made an entry to /etc/init.d/rc.local

Any ideas how I should get this going?
It mounts when I execute it normally!

Will appreciate any help and suggestion!

Thanks!

---

### Post by ankeetg on 2011-05-25
I figured it out. Well not exactly.

I just added a sleep 15 and appended the mount code:
> sleep 15 && mount NFS:/home/user/NFS /home/user/mount

It works fine now. However I would still like to know why it wouldn't work normally.

---

### Post by aeiah on 2011-05-25
well there's no need for sudo (as you figured out) because /etc/rc.local runs as root.

if that isnt the issue, perhaps its because your machine hadn't received its IP address from your gateway, and so couldn't find your NFS server until it waited 15 seconds.

by the way, you can mount NFS shares via your /etc/fstab file, although if your solution works then there's no need to change. it might mean you dont have to sleep for 15 seconds though.

---

