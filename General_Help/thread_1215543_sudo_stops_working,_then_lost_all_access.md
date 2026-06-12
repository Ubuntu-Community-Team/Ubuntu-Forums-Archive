---
title: "sudo stops working, then lost all access"
date: 2009-07-17
forum: General Help
---

### Post by Valacosa on 2009-07-17
I was using my computer last night when I had randomly lost use of sudo. Whenever I tried to use sudo in the terminal, I got the response, "segmentation fault". 

Googling yielded no consistent solution to this problem, so I just tried rebooting my computer. But now I can't log in at all! If I try logging in, it'll appear as if it's working for a moment, but then dump me back at the login screen. Such is the case for myself and the other user account on the system. 

I can't SSH in either. The computer is responsive to SSH, but as soon as I sign in, I get a message that the connection has been closed. 

Does anybody have any idea what's going on?

---

### Post by nikhilk on 2009-07-17
Boot from a live CD and see if your partitions are full?
Determine the partitions using```
fdisk -l
```
Mount the partitions and use the command```
df -H
``` to see the disk space report.

---

### Post by LightningCrash on 2009-07-17
+1 to Root partition full

---

### Post by Valacosa on 2009-07-17
The partition filling up is kind of likely, actually. I'll check on this when I return home this afternoon, and post my findings here.

---

### Post by Valacosa on 2009-07-20
Sorry for the delay. 

I booted using a [Knoppix]("http://www.knoppix.net/") disc, and mounted my Ubuntu partition. Then I ran the disk usage command:
```
df -H
```
The pertinent line is as follows:
```
/UNIONFS/dev/sda3       11G   8.4G   1.5G  85% /mnt/sda3

```
So my root partition isn't full. Any other ideas?

Here's a bit more information: the last time I remember using sudo and having it work was when I installed nmap. (This house has a WPS54G print server, but I didn't set it up - the easiest way to see what IP it lives at was to ping every IP.) nmap installed fine, but every instance of sudo I remember after that failed with the segmentation fault. Does that leave any other likely candidates?

---

