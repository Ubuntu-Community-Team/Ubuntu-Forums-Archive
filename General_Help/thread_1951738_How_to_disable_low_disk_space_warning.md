---
title: "How to disable low disk space warning"
date: 2012-04-03
forum: General Help
---

### Post by firekage on 2012-04-03
Hi.

I've got one, big problem with low disk space warning. I switched from Slackware and KDE, and on Slackware there wasn't something annoying like with Ubuntu 11.10 and low disk space warning. I don't now how or i can't disable low disk space warnings. It's really annoying, it so fast that sometimes i'm not able to close message dialog.

Is there any way to disable it? My output from df -h looks like this:

```
System plików            rozm. u&#380;yte dost. %u&#380;. zamont. na
/dev/sdb1              25G  6,9G   17G  30% /
udev                  2,0G  4,0K  2,0G   1% /dev
tmpfs                 806M  1,1M  805M   1% /run
none                  5,0M     0  5,0M   0% /run/lock
none                  2,0G  3,4M  2,0G   1% /run/shm
/dev/sda2              33G   13G   18G  42% /mnt/hd/36GB
/dev/sda5             108G  100G  7,7G  93% /mnt/hd/112GB
/dev/sdb2             572G  572G   61M 100% /mnt/hd/598GB
/dev/sdf1              20G  4,3G   15G  23% /mnt/hd/20GB
/dev/sdf2             577G  577G   63M 100% /mnt/hd/604GB
/dev/sdc1              26G   24G  1,5G  95% /mnt/hd/25GB
/dev/sdc2             441G  441G  669M 100% /mnt/hd/462GB
/dev/sdd2             907G  888G   20G  98% /mnt/hd/950GB
/dev/sdd5              25G   18G  7,3G  72% /mnt/hd/26GB_1
/dev/sde1              36G   88M   35G   1% /mnt/hd/26GB_2
/dev/sde2             897G  897G  404M 100% /mnt/hd/940GB

/dev/mapper/truecrypt1
                      440G  439G  1,7G 100% /media/truecrypt1

/dev/mapper/truecrypt2
                      571G  571G  474M 100% /media/truecrypt2

/dev/mapper/truecrypt3
                      576G  576G  251M 100% /media/truecrypt3

/dev/mapper/truecrypt4
                      896G  873G   24G  98% /media/truecrypt4

/dev/mapper/truecrypt5
                      820G  820G  487M 100% /media/truecrypt5

df: `/root/.gvfs': Brak dost&#281;pu
```


I don't want to remove/freeing space from my disks. I need all things on them, i just want do disable low disk space warnings.

/dev/mapper/truecryptXY is a container mounted in filesystems, and containers were created on /dev/sdXY.

Can you help me?

---

### Post by TeoBigusGeekus on 2012-04-03
Could [this]("http://www.hecticgeek.com/2011/11/how-to-disable-low-disk-space-warnings-in-ubuntu-linux/") be of any help?

---

### Post by firekage on 2012-04-05
Unfortunately, i tried it several times and it doesen't work at all. I think that main reason for it is that all devices are placed in / and of course we can't uncheck / in disk usage analizer, and because of this it will always warn us about low disk space - cause drives are mounted in / filesystem...

As a matter of fact it drives me mad and i don't know what is better:

-faster system (ubuntu) with this mad behaviour
-slower system (Slackware - i don't know why on quad core systems with X4 955 dolphin file manager and firefox are so slow that this system is barely to use) without "ubuntu" behaviur of low disk space warning...

---

### Post by kazztan0325 on 2012-04-06
Hi firekage,

There are *.desktop files of 'Startup Applications' in **/etc/xdg/autostart/**.

What about trying to remove **"gdu-notification-daemon.desktop"**?
You may move the file to somewhere else temporarily if you would not like to remove it.

Hope this helps.

---

### Post by firekage on 2012-04-06
> **kazztan0325 said:**
> Hi firekage,

There are *.desktop files of 'Startup Applications' in **/etc/xdg/autostart/**.

What about trying to remove **"gdu-notification-daemon.desktop"**?
You may move the file to somewhere else temporarily if you would not like to remove it.

Hope this helps.

Thank you, i will try this. I'll make this file non executable with chmod -x, also there is something in it so i will try to change few lines in this - i hope it will help me.

---

### Post by firekage on 2012-04-07
As to be expected - i chmoded it with chmod -x, i chmoded it with chmod 000, i moved it to other locations and it didn't helped me at all.

Geez...it really drives me mad to a point where i don't want to use ubuntu at all. I must admit that Linux is a operating system with minor or major bugs compared to Windows :( (i had bugs on Slackware during last year, i had on Mint, now under Ubuntu...)

---

### Post by kazztan0325 on 2012-04-07
It seems to be a bug which has not been fixed yet.
I found following web page in Launchpad a little while ago.

**"Low disk space" warning popping up repeatedly.**
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/881376]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/881376")

---

### Post by firekage on 2012-04-07
So, it seems that it is not my fault and i havent been doing anything wrong. 

Strange is that it's not still fixed when so many people are affected by this issue.

---

### Post by kazztan0325 on 2012-04-07
> **firekage said:**
> So, it seems that it is not my fault and i havent been doing anything wrong. 

Strange is that it's not still fixed when so many people are affected by this issue.

Exactly.
And I was surprised to know "This bug is STILL present in 12.04 beta 2"!

---

### Post by dcstar on 2012-04-08
> **firekage said:**
> Hi.

I've got one, big problem with low disk space warning. I switched from Slackware and KDE, and on Slackware there wasn't something annoying like with Ubuntu 11.10 and low disk space warning. I don't now how or i can't disable low disk space warnings.
.........
Install the **dconf-tools** package and then run the **dconf-editor** and try changing the relevant settings in the following key:

```
org.gnome.settings-daemon.plugins.housekeeping
```

---

### Post by firekage on 2012-04-08
> **dcstar said:**
> Install the **dconf-tools** package and then run the **dconf-editor** and try changing the relevant settings in the following key:

```
org.gnome.settings-daemon.plugins.housekeeping
```


Thank you very much. It works! I will observe it for a more few days but so far, warnings don't appear -  no more!

---

### Post by firekage on 2012-04-08
I think that it really works!

Thank you very much. I tried with similar options but in other branch in dconf-editor, in apps, not in org.

---

