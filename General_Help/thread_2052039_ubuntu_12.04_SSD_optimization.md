---
title: "ubuntu 12.04 SSD optimization"
date: 2012-09-02
forum: General Help
---

### Post by Dasberry on 2012-09-02
Hi guys, 

I've been wanting to slowly shift over to ubuntu for a while now, and have finally set up a dual boot system with windows and ubuntu on my SSD. In windows I did a lot of optimization to reduce writes to the drive, and I am hoping I can do the same in ubuntu. Most of the guides seem to require some previous knowledge though, and I'm a total noob. 

Can anyone point me in the right direction?

---

### Post by jim_deadlock on 2012-09-02
It's very simple, all you need to do is edit /etc/fstab

Do ALT-F2 and run 'gksudo gedit'

Open /etc/fstab

Add noatime,discard to your SSD options, mine is below to give you an idea. Save and reboot, that's it!

If you're not sure which line is your SSD you can run 'sudo blkid' in a terminal to list your devices.

```
# <file system> 			  <mount point>   <type>  <options>       			<dump>  <pass>
proc				          /proc           proc    nodev,noexec,nosuid 			0       0
UUID=7944a180-602b-4e65-b863-39726ad07b0a none            swap    sw              			0       0
UUID=3b1723cb-088f-4380-9e66-e8cd9fcc775f /               ext4    noatime,discard,errors=remount-ro 	0       1
UUID=2fc889b2-c230-4e03-9e8e-1245f08d0101 /home           ext4    defaults        			0       2
```

---

### Post by dcstar on 2012-09-03
> **jim_deadlock said:**
> It's very simple, all you need to do is edit /etc/fstab

Do ALT-F2 and run 'gksudo gedit'

Open /etc/fstab

Add noatime,discard to your SSD options, mine is below to give you an idea. Save and reboot, that's it!
........

And:

[http://tombuntu.com/index.php/2012/04/26/setting-up-ubuntu-on-an-ssd/](http://tombuntu.com/index.php/2012/04/26/setting-up-ubuntu-on-an-ssd/)

---

### Post by Dasberry on 2012-09-03
Thank you guys

---

