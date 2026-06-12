---
title: "root partition 0 bytes remaining after enlarging"
date: 2010-09-02
forum: General Help
---

### Post by HyperFlexed on 2010-09-02
Hi, I recently cleared out some old partitions, and "/" was getting full so I made it bigger. It went from about 2Gb to 7Gb.

Now when I boot into my OS I get a dialogue saying:
```
The volume "Filesystem root" has only 0 bytes disk space remaining

You can free up disk space by removing unused programs or files, or by moving files to another disk or partition
```

I don't see how this is possible. If anything it should have more free space than it had before. Any idea how I might go about diagnosing this issue?

---

### Post by HyperFlexed on 2010-09-02
I just ran the disk usage analyzer, and only had the program scan my "/" partition, the total space taken by files on that partition is 2.2Gb. This makes no sense.

I tried
```
sudo shutdown now -rF
```

to do a filesystem check, but didn't stumble on any errors.

---

### Post by Smart Viking on 2010-09-02
Does it allow you to install a program?

---

### Post by tarps87 on 2010-09-02
Can you post the output of:
```
df -h
```
Thanks

---

### Post by MooPi on 2010-09-02
You didn't mention how you enlarged the / partition. Did you use gparted to include the emptied space. Let us know so we can move on with helping you.If you haven't already boot the Live Ubuntu CD and run gparted to discover your disk issues.

---

### Post by HyperFlexed on 2010-09-02
> **tarps87 said:**
> Can you post the output of:
```
df -h
```
Thanks

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             7.1G  7.1G     0 100% /
none                  1.5G  304K  1.5G   1% /dev
none                  1.5G  256K  1.5G   1% /dev/shm
none                  1.5G  320K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda9             3.9G  131M  3.6G   4% /tmp
/dev/sda1              40G   21G   19G  53% /media/OS
/dev/sda11            2.0G  153M  1.7G   9% /boot
/dev/sda10             66G  5.7G   57G  10% /home
/dev/sda7             2.9G  731M  2.1G  27% /var
/dev/sda8              22G  6.7G   14G  34% /usr
/dev/sdb1             873G  726G  148G  84% /media/TREKSTOR
/home/johnny/.Private
                       66G  5.7G   57G  10% /home/johnny
/dev/sdb2              58G  180M   55G   1% /media/ubuntu-home-back_
```

---

### Post by HyperFlexed on 2010-09-02
> **MooPi said:**
> You didn't mention how you enlarged the / partition. Did you use gparted to include the emptied space. Let us know so we can move on with helping you.If you haven't already boot the Live Ubuntu CD and run gparted to discover your disk issues.

yes, I did use gparted on a livecd to expand and move the partitions

my partitions were like this
[swap][/][var][usr][tmp][home][boot][old1][old2]

now they're like this
[swap][<--/--> + -->][var-->][usr-->][tmp-->][<--home--> + -->][boot-->]

where:
--> means partition was moved as far right as it could go, and
<--x--> means the partition was increased in size

Are you suggesting I should right click the partition in gparted on the liveCD and select the Check option? I have to go out tonight, but I will check tomorrow if you could clarify.

Thanks all for looking into this for me. My system has been acting very strange since I got this error message (I get ecryptfs errors in TTYs though my home folder seems accessible for now)

---

### Post by HyperFlexed on 2010-09-02
> **Smart Viking said:**
> Does it allow you to install a program?

yeah, but /usr and /tmp have their own partitions, so it's not surprising.

---

### Post by tarps87 on 2010-09-03
> **HyperFlexed said:**
> ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             7.1G  7.1G     0 100% /
none                  1.5G  304K  1.5G   1% /dev
none                  1.5G  256K  1.5G   1% /dev/shm
none                  1.5G  320K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda9             3.9G  131M  3.6G   4% /tmp
/dev/sda1              40G   21G   19G  53% /media/OS
/dev/sda11            2.0G  153M  1.7G   9% /boot
/dev/sda10             66G  5.7G   57G  10% /home
/dev/sda7             2.9G  731M  2.1G  27% /var
/dev/sda8              22G  6.7G   14G  34% /usr
/dev/sdb1             873G  726G  148G  84% /media/TREKSTOR
/home/johnny/.Private
                       66G  5.7G   57G  10% /home/johnny
/dev/sdb2              58G  180M   55G   1% /media/ubuntu-home-back_
```

It looks like / is still at 100% usage after the resize, as to what is using this space I don't know. Can you provide any more details on where this space is being used?

---

### Post by dulbirakan on 2010-09-03
> **tarps87 said:**
> It looks like / is still at 100% usage after the resize, as to what is using this space I don't know. Can you provide any more details on where this space is being used?

You can do that with

```
sudo du / --max-depth=1 -h
```

You might want to exclude other partitions with the -x parameter...

---

### Post by HyperFlexed on 2010-09-03
> **dulbirakan said:**
> You can do that with

```
sudo du / --max-depth=1 -h
```

You might want to exclude other partitions with the -x parameter...

```
0    /sys
200K    /srv
19M    /etc
4.0K    /usr
4.8G    /media
0    /proc
7.4M    /sbin
4.0K    /selinux
20K    /tmp
908K    /root
4.0K    /boot
13M    /lib32
0    /dev
769M    /lib
128K    /mnt
7.8M    /bin
4.0K    /var
4.0K    /home
1.4G    /opt
16K    /lost+found
7.0G    /

```

looks like I didn't mount a drive properly in /media/ when I did a backup. That would explain a lot.

---

### Post by tarps87 on 2010-09-06
> **HyperFlexed said:**
> ```
0    /sys
200K    /srv
19M    /etc
4.0K    /usr
4.8G    /media
0    /proc
7.4M    /sbin
4.0K    /selinux
20K    /tmp
908K    /root
4.0K    /boot
13M    /lib32
0    /dev
769M    /lib
128K    /mnt
7.8M    /bin
4.0K    /var
4.0K    /home
1.4G    /opt
16K    /lost+found
7.0G    /

```

looks like I didn't mount a drive properly in /media/ when I did a backup. That would explain a lot.

Yep, that's what it looks like from here **4.8G /media** problem solved?

---

### Post by progone on 2011-01-30
Thank you so much for bringing sudo du / --max-depth=1 -h to light.  I had the same issue.  A thumb drive was connected to my printer that was causing my headaches.

---

