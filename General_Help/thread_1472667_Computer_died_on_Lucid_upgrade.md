---
title: "Computer died on Lucid upgrade"
date: 2010-05-04
forum: General Help
---

### Post by dpeterson3 on 2010-05-04
Hello. I'm new to Ubuntu (I use Debian, so it shouldn't be too much of a jump). I was put somewhat in charge of a server last semester running Ubuntu. It serves as a router and general purpose computer for a robotics lab. Yesterday, I went do dist-upgrade using the command line, and ran into a couple of bugs with gtk libraries which I fixed based on the bug reports. However, the computer decided to reboot for some reason in the middle of the upgrade and killed the running OS. I currently have it up on a Debian recovery CD. I can't get past intramfs without the CD. It is dying somewhere in rsyslog with an error about a broken pipe. I am not sure where to go from here. I will post actual error messages when I get back infront of the machine. No one knows how the machine was set up in the first place and it holds a few secrets we need to keep, so reinstall is the last option.

Thanks in advance

---

### Post by dpeterson3 on 2010-05-05
After playing for a while, I got the packages situation sorted out and everything seems to be installed fine. Now, I have an initrd problem. While booting, I get a error message 
```

Mount: Mount /dev/sda1 on /root failed: No such device


```
at which point I get dumped into a busybox shell. I have run fsck on the drive and tried rebuilding initrd and still nothing. After hours of googling, I still come up with nothing. Any ideas where to go from here. 

PS. The machine seems to be trying to load a raid device even though there is only one drive in the machine. Could that be the problem?

---

### Post by quadproc on 2010-05-05
> **dpeterson3 said:**
> After playing for a while, I got the packages situation sorted out and everything seems to be installed fine. Now, I have an initrd problem. While booting, I get a error message 
```

Mount: Mount /dev/sda1 on /root failed: No such device


```at which point I get dumped into a busybox shell. I have run fsck on the drive and tried rebuilding initrd and still nothing. After hours of googling, I still come up with nothing. Any ideas where to go from here. 

PS. The machine seems to be trying to load a raid device even though there is only one drive in the machine. Could that be the problem?
Very possible.  You might try changing from using the device ID to UUIDs instead.  Device IDs can change as hardware is installed or removed, or plugged in and unplugged.  And there is a big conflict between old hdX and newer sdX kinds of disks - a system can think that it has two disks with the same device ID!  UUIDs are the recommended workaround for these problems.

quadproc

---

### Post by dpeterson3 on 2010-05-05
Thanks. I already tried that and thought it had failed the same way. Your post made me think. I set a bad option in grub so I couldn't see the output. Now the system can find the rootfs, but I still get an error 
```

Gave up waiting for root device. Common Problems: 

```

I will start tracking down this error and see what happens. Any more suggestions would be great.

---

### Post by quadproc on 2010-05-06
> **dpeterson3 said:**
> Thanks. I already tried that and thought it had failed the same way. Your post made me think. I set a bad option in grub so I couldn't see the output. Now the system can find the rootfs, but I still get an error 
```

Gave up waiting for root device. Common Problems: 

```I will start tracking down this error and see what happens. Any more suggestions would be great.
Could your system be trying to boot from the network?  if so, since the network isn't available at boot time, the situation is a classical deadlock.

quadproc

---

### Post by dpeterson3 on 2010-05-06
Thanks. Its not trying to boot from network, Grub comes up and the kernel loads. It dies in initramfs. I decided to reinstall and copy everything we need. The more I played, the more I found wrong with that box. I think it has to do with the OS being set up to use raid even though there is only 1 HDD in the box. I really don't know how that system worked in the first place now.

---

