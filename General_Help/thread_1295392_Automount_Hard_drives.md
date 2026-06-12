---
title: "Automount Hard drives"
date: 2009-10-19
forum: General Help
---

### Post by PcBoyGeorge on 2009-10-19
(First off sorry if this is not supposed to be here.)

Hi, So I got Ubuntu installed and dual-booting. But because I have 3 partitions of my hard drive I use them for file transfers. But what is annoying is that I want the drives mounted on my desktop. So they stay on there. But every time I restart I have to remount them again. Is there a code or program I can use to auto-mount them on every restart. I tried sometime called Psydm or whatever but it was too complicated as it says sd1 or whatever and won't let me choose what hard drives to automount. And Im new to this OS so can you provide me with a basic code and full instructions to do this please.

Thank you

---

### Post by drs305 on 2009-10-19
PcBoyGeorge,

First, welcome to the Ubuntu forums.

We can put entries in fstab so they automatically mount on boot. To do this, we will need some information.

Open a terminal (Applications, Accessories, Terminal) and enter the following commands. You will be asked for your password. Type it in but don't be surprised when you don't see it as you type.

Mount the devices where you want them, then:
```

mount
cat /etc/fstab
sudo blkid

```

Here is an excellent guide on fstab:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Matt__ on 2009-10-19
Dual booting with windows ntfs drive?

```
sudo aptitude update
sudo aptitude install ntfs-config
```run the app (/system/admin) & enable write support when prompted

---

