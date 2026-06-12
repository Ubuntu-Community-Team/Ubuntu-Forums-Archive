---
title: "Restoring root privileges (admin group) in Lucid Lynx"
date: 2010-05-01
forum: General Help
---

### Post by powerpleb on 2010-05-01
After freshly installing Lucid Lynx and tinkering for some time to get everything just how I like it, I managed to somehow remove myself and all other users from all groups.8-[ Now, obviously, I've restarted and I don't have root privileges as I am no longer a member of *admin* group. So I am somewhat stuck. :(

I've looked at this page: [http://www.cyberciti.biz/tips/ubuntu-admin-group-permissions.html](http://www.cyberciti.biz/tips/ubuntu-admin-group-permissions.html). But annoyingly, there is no grub menu appearing on boot up (unlike previous Ubuntu versions).:-?

So I'm appealing for your help to either:
a) Show me how I can bring up the grub menu so I can access ubuntu in safe mode
b) Show me another way of accessing the system with root privileges. (Would using *chroot* from the Live CD work? I just thought of that now so I'll try it).
c) Let me know of another way of getting my privileges back.

Cheers.

---

### Post by Skorzen on 2010-05-01
Hit 'shift'.
[http://ubuntuforums.org/showthread.php?t=1428932](http://ubuntuforums.org/showthread.php?t=1428932)

---

### Post by dino99 on 2010-05-01
[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

---

### Post by powerpleb on 2010-05-01
I ended up just booting into a live CD and manually adding myself to /etc/group.

---

