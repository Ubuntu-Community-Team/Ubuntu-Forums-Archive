---
title: "installing GRUB2 from 10.04 LiveCD"
date: 2011-05-23
forum: General Help
---

### Post by DOSIX on 2011-05-23
I'm in the process of trying to get an Arch Linux installation to work on my computer. There is a problem with the original GRUB install that comes with Arch (basically it's caused by GRUB 0.98 ). 
To fix this problem I need to update to GRUB2. I have no internet connection on this computer, only in Windows, so I couldn't do it from the Arch LiveCD itself. 

I tried grub-install from the Ubuntu 10.04 LiveCD onto /dev/sda. When I rebooted, it only gave me a GRUB2 prompt. So I went back into LiveCD, redid the process, and this time I did update-grub as well, but I got an error. I forgot the exact words but basically it said it couldn't find a root or something and it asked me if i was sure if '/dev' was mounted. I have no idea what that means, so I'm stuck. In general, if anyone has a way for me to get GRUB2 working, whether or not it's the method I'm trying, I would greatly appreciate it. 

Here is how my partitions are set up.

```

/dev/sda1 - Windows (NTFS)
/dev/sda5 - /boot (ext2)
/dev/sda6 - swap
/dev/sda7 - /root (ext4)

```

---

