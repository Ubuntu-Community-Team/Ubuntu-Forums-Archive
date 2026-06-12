---
title: "Hard drive activity when going out of &quot;Suspend&quot; mode"
date: 2009-11-12
forum: General Help
---

### Post by tdlx on 2009-11-12
Hello all,

Happy user of Ubuntu on my laptop Acer 4100 since Dapper, I recently downgraded from Karmic after some hours of use back to ubuntu 8.10 in order to have fglrx working again.

Since this downgrade, the hard drive is scratching like mad during 2 to 3 minutes when the laptop is going out of the "Suspend" mode, thing that I had never experienced since i began to use ubuntu. I havent changed anything (no change in the BIOS, nothing)

Its like it is writting something during some minutes on the HDD, and meanwhile, the computer is very slow (can barely input my password in the invite)

THe kernel is 2.6-27-15
which command can i input int the terminal to help you figure out my problem?

thanks for your help folks!

tdlx

---

### Post by Giblet5 on 2009-11-12
```
top
```

---

### Post by tdlx on 2009-11-23
Hello,

I thought I had subscribed to this topic, but apparently not. Sorry, for not answering to your message. Thanks for your answer anyway.

i looked around, and discovered iotop which actually gives the details regarding the processes reading/writing on the HDD.

I went a little further and discovered that a process regularly reads a lot my HDD when going out of "suspend" mode.

Here is a part of the log of iotop :

```

Total DISK READ: 164.25 K/s | Total DISK WRITE: 58.40 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 2589 root      142.35 K/s    3.65 K/s  0.00 %  0.00 % X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 2182 root           0 B/s   25.55 K/s  0.00 %  0.00 % [kjournald]
 9512 root        3.65 K/s       0 B/s  0.00 %  0.00 % sh ./linux/hal-system-power-suspend-linux
 9517 root       18.25 K/s    3.65 K/s  0.00 %  0.00 % sh /usr/sbin/pm-suspend
 4547 syslog         0 B/s   18.25 K/s  0.00 %  0.00 % syslogd -u syslog
 5062 root           0 B/s    3.65 K/s  0.00 %  0.00 % NetworkManager
 5066 root           0 B/s    3.65 K/s  0.00 %  0.00 % wpa_supplicant -u -f /var/log/wpa_supplicant.log
```I analysed it, and it appears that X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 regularly reads a lot of data over the HDD (takes a few minutes) when going out of suspend mode. However, surprisingly enough, it seems that the longer the computer stays in suspend mode, the longer it reads the HDD when waking up...

Any idea?

---

### Post by dcstar on 2009-11-24
> **tdlx said:**
> Hello all,

Happy user of Ubuntu on my laptop Acer 4100 since Dapper, I recently downgraded from Karmic after some hours of use back to ubuntu 8.10 in order to have fglrx working again.

Since this downgrade, the hard drive is scratching like mad during 2 to 3 minutes when the laptop is going out of the "Suspend" mode, thing that I had never experienced since i began to use ubuntu. I havent changed anything (no change in the BIOS, nothing)
.......

Check that the UUID of your swap partition matches what is in your /etc/fstab file and that swap is enabled.

---

### Post by tdlx on 2009-11-24
hello dcstar, thanks for your answer

Here is my fstab :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=03b5421b-29ec-42b2-8cb0-d7ed4d5901a3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9788b69b-658c-4976-9c5b-69698753337f /home           ext3    relatime        0       2
# /dev/sda2
UUID=334b9903-099c-4601-9bc1-decfe922c174 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

and here is the list of UUID :

```
tdl@tdl-laptop:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2004-06-16 02:00 03b5421b-29ec-42b2-8cb0-d7ed4d5901a3 -> ../../sda6
lrwxrwxrwx 1 root root 10 2004-06-16 02:00 334b9903-099c-4601-9bc1-decfe922c174 -> ../../sda2
lrwxrwxrwx 1 root root 10 2004-06-16 02:00 72C0C59FC0C569C5 -> ../../sda1
lrwxrwxrwx 1 root root 10 2004-06-16 02:00 9788b69b-658c-4976-9c5b-69698753337f -> ../../sda5
```

Looks like my swap partition (sda2) is correctluy identified

---

### Post by matmota on 2010-01-27
I also have this problem since updating to Karmic last year. This is in a Lenovo ThinkPad W500.
It seems to be caused by the fglrx driver:

[https://bugs.launchpad.net/ubuntu/+bug/391628](https://bugs.launchpad.net/ubuntu/+bug/391628)

---

