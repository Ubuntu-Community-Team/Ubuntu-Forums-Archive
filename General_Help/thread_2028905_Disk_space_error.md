---
title: "Disk space error"
date: 2012-07-19
forum: General Help
---

### Post by chakri1 on 2012-07-19
Hello,

I am trying to find out available disk space in my Desktop. Here are the commands that I tried and their outputs :

$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda2 74G 57G 14G 81% /
none 2.0G 688K 2.0G 1% /dev
none 2.0G 1.6M 2.0G 1% /dev/shm
none 2.0G 260K 2.0G 1% /var/run
none 2.0G 0 2.0G 0% /var/lock
/dev/sda1 184M 31M 145M 18% /boot
/dev/sda6 66G 19G 45G 30% /home

$ sudo du -hs /
47G	/

First command 'df' shows that 57G is used in '/' partition. Second command 'du' shows 47G is used in '/' folder. I could not understand why '/' partition is using more disk space than '/' folder ?

Any help in understanding how disk space is measured will be much appreciated.

Thanks in advance,
Chak

**Update :** modified second command as suggested by [mmehboobhan]("http://ubuntuforums.org/member.php?u=1698776")

$ cd /
$ sudo du --si -s
50G	.

Still there seems to be a difference between 'du' and 'df' values.

Also, does 'du' command on '/' folder consider the space occupied by '/home' folder that resides within '/' folder ? If so, then 'du --si -s' must give larger value than 'df' of '/' partition. 

Any help is appreciated.

---

### Post by hal8000 on 2012-07-19
du shows the USED space by ALL mounted file systems. Disk usage summary shows as 123G on my system, when broken down with df shows what is mounted and where. Hope that helps.

[root@orac ~]# du -sh /
123G    /

[root@orac ~]# df
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              19G  6.0G   12G  34% /
/dev/sdb2              24G   11G   13G  46% /home
/dev/sda12             36G   23G   12G  67% /media/share
/dev/sda1             128G   12G  117G   9% /media/xp
/dev/sda2             196G   74G  122G  38% /media/win7

---

### Post by Wim Sturkenboom on 2012-07-19
There are a few things that I'm aware of that can give the difference
1)
Deleted files might still be in use by an application; du will not see them but df (the filesystem) will still see them as in use. If you open a huge file in vi, vi will create an equally huge swp file. If you keep vi open and delete the swp file, du will immediately reflect the change but df will not as vi still has it 'open'. If you close vi after that, df will reflect it.
The command *lsof* can be of help here. A reboot should _mostly_ get rid of this discrepancy.
2)
du traverses directories that it can see. If you mount a partition over a directory (like /dev/sda6 on /home), du will not count the original /home directory but what is mounted on it. If your /home directory (before mounting /dev/sda6 over it) contains a few gigs of data, df will reflect this in the reporting of /dev/sda2 and du will not (as it can't see it).

---

### Post by chakri1 on 2012-07-19
Thanks for your reply.

If 'du' shows COMBINED space used by all mounted file-systems, then it should be higher than 'df' of one single partition. But in my case, du shows 50G while df of '/' partition shows 57G.

> **hal8000 said:**
> du shows the USED space by ALL mounted file systems. Disk usage summary shows as 123G on my system, when broken down with df shows what is mounted and where. Hope that helps.

[root@orac ~]# du -sh /
123G    /

[root@orac ~]# df
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              19G  6.0G   12G  34% /
/dev/sdb2              24G   11G   13G  46% /home
/dev/sda12             36G   23G   12G  67% /media/share
/dev/sda1             128G   12G  117G   9% /media/xp
/dev/sda2             196G   74G  122G  38% /media/win7

---

### Post by spjackson on 2012-07-20
> **chakri1 said:**
> If 'du' shows COMBINED space used by all mounted file-systems, then it should be higher than 'df' of one single partition. But in my case, du shows 50G while df of '/' partition shows 57G.
True, but the command
```

du -sh /

```does indeed calculate the sum used by all mounted partitions. So your discrepancy is larger than it currently appears. You need -x if you only want to analyze the / partition itself, i.e.
```

du -shx /

```The possible reasons offered by Wim Sturkenboom are very good explanations of what you are seeing. I'd add to this that it is possible for there to be a problem that an fsck of / could sort it out. Here's how to force fsck at reboot [http://linux.aldeby.org/post/linux-ubuntu-force-fsck-filesystem-check-at-reboot.html](http://linux.aldeby.org/post/linux-ubuntu-force-fsck-filesystem-check-at-reboot.html)

You could also run fsck of /dev/sda2 by booting from a LiveCD.

If your problem is that /home or /boot have been mounted onto a directory that contains files (the second point mentioned by Wim Sturkenboom), then you would really need to boot from a LiveCD to sort that out. e.g. (from a LiveCD)
```

sudo mkdir /media/root
sudo mount /dev/sda2 /media/root
sudo ls -a /media/root/home /media/root/boot

```If these directories contain files, then they are taking up space but are hidden from du when you boot normally.

---

