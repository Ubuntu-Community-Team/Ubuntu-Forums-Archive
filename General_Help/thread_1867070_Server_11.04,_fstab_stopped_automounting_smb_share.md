---
title: "Server 11.04, fstab stopped automounting smb shares"
date: 2011-10-22
forum: General Help
---

### Post by crasher35 on 2011-10-22
I am currently having a problem with my Ubuntu Server 11.04 (Natty Narwhal). I have /etc/fstab set up to mount my [NAS (D-Link DNS-323)]("http://www.dlink.com/products/?pid=509") at two different mount points but it will not do it on boot. When I initially set it up, this worked just fine. It would mount the shares on start-up with no problems, then, about two weeks ago, it stopped.

Now, once I log in, I have to enter "sudo mount -a" to get it to mount the share which defeats the purpose of setting up a static mount for it.

Here is my /etc/fstab config file:
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/crashserv-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=395b452e-20b0-4cc0-98d7-7cc0b876ccbc /boot           ext2    defaults        0       2
/dev/mapper/crashserv-swap_1 none            swap    sw              0       0
//192.168.11.2/Volume_1/        /mnt/muta       smbfs   default 0       0
//192.168.11.2/Volume_1/John    /home/john      smbfs   default 0       0

```

I also tried changing the type to cifs instead of smbfs since I read that smbfs has been deprecated, but that still did not solve my problem.

Any help or insight on this would be greatly appreciated.

---

