---
title: "HDD not spindown in RAID5"
date: 2012-05-03
forum: General Help
---

### Post by arryo on 2012-05-03
I tried all of the suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=1488614](http://ubuntuforums.org/showthread.php?t=1488614)

but it seems my 3 harddrives on raid 5 won't go standby

Even when i used the command 

Code:
hdparm -y /dev/sda /dev/sdc /dev/sdd
and check with 

Code:
hdparm -C /dev/sda
the result is still active/idle

Only when I unmount raid from the system then those hdds will spin down

I have fresh new ubuntu server 12.04 on USB with nothing it it yet except SSH, mdadm, smartmontools, and hdparm

---

### Post by Cheesemill on 2012-05-03
There maybe something of value on rubylaser's site:
[http://zackreed.me/articles/60-spin-down-idle-hard-disks](http://zackreed.me/articles/60-spin-down-idle-hard-disks)

---

### Post by arryo on 2012-05-03
> **Cheesemill said:**
> There maybe something of value on rubylaser's site:
[http://zackreed.me/articles/60-spin-down-idle-hard-disks](http://zackreed.me/articles/60-spin-down-idle-hard-disks)

I also followed that guide but it's not working either :(

---

### Post by arryo on 2012-05-04
I used another program called "spindown" and it has an option to check the status of the harddrive and I noticed that my harddrives go idle only for 60 seconds, no wonder that they never go standby. Is there someway that I could check what is possible reason making harddrives behave like that?

---

