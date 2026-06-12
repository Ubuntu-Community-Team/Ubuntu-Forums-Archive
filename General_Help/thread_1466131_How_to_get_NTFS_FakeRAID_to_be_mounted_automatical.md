---
title: "How to get NTFS FakeRAID to be mounted automatically at startup?"
date: 2010-04-30
forum: General Help
---

### Post by luckyjonny on 2010-04-30
Hello,

I've been searching for a solution get mount my NTFS FakeRAID automatically when 9.10 64-bit starts, but haven't managed to find a solution.

Currently, after boot, dmraid activates my RAID automatically but does not map the partitions on the drive:

```
$ ls /dev/mapper/
control  isw_bibdafajea_Vault

```

so I have to run

```
sudo kpartx -a /dev/mapper/isw_bibdafajea_Vault
```

(which incidentally returns) 

```
GPT:Primary header thinks Alt. header is not at the end of the disk.
GPT:Alternate GPT header not at the end of the disk.
GPT: Use GNU Parted to correct GPT errors.

```

but nonetheless results in the appearance of

```
$ ls /dev/mapper/
control  isw_bibdafajea_Vault  isw_bibdafajea_Vault1  isw_bibdafajea_Vault2
```

and then

```
sudo mount -t ntfs-3g /dev/mapper/isw_bibdafajea_Vault2 /media/Vault
```

to mount the volume. Obviously can't add a line in /etc/fstab mounting /dev/mapper/isw_bibdafajea_Vault2 as I would wish, because the partitions aren't being mapped automatically.

I've found the following posts reporting the same problem:

[http://ubuntuforums.org/showthread.php?t=610857](http://ubuntuforums.org/showthread.php?t=610857)

[http://forums.overclockers.com.au/showthread.php?t=857006](http://forums.overclockers.com.au/showthread.php?t=857006)

and suspect this bug report could refer to the same issue:

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/152409](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/152409)

Any help would be most gratefully received.

---

### Post by luckyjonny on 2010-05-01
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/Tumbleweed_in_Chelan_WA.jpg/220px-Tumbleweed_in_Chelan_WA.jpg[/IMG]

:)

---

### Post by luckyjonny on 2010-05-08
It's lonely in here ...

---

### Post by ewa8949 on 2011-01-12
I have the same exact problem.  Did you ever figure it out?

---

### Post by BBUCommander on 2011-03-31
I tried making use of the new Upstart boot executer to launch a script handling the task with no luck.  However, I did manage to half-way do the job half-way by calling a script I made from my /etc/rc.local file.  See attached.

---

