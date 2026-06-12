---
title: "Root keeps on getting bigger in size"
date: 2012-06-01
forum: General Help
---

### Post by sd@ksu on 2012-06-01
I am using Ubuntu 11.04 and not going to upgrade to 11.10 now.
Here is what i get after issuing "df-h" from terminal:
```
user@ubuntu:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/sda3             9.2G  3.5G  5.3G  40% /[/COLOR]
none                  495M  632K  494M   1% /dev
none                  501M  376K  501M   1% /dev/shm
none                  501M  128K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
/dev/sda1             2.8G  110M  2.6G   5% /boot
/dev/sda4             134G   15G  114G  12% /home
.host:/               458G  253G  205G  56% /mnt/hgfs

```
The part in red is my concern.
While I installed, I put "/", "/home", "/boot" in separate partitions as you see above. I do not know what is filling up root. I have checked my log files but they are only a few MB. I suspect it is the "/proc" but using "du" or "sudo du" or sudo du -sh" etc, I am not able to find its size.
I think the occupied size in root grows up after any update from update manager (so far as i remember).  Can anyone help me identify what is taking so much space in root? Or is it OK? I am just afraid that soon it will complain about no available space on root. thanks in advance.
If I can identify it, I would like to put it in a separate partition form root.

---

### Post by Cheesemill on 2012-06-01
Your root partition only has 3.5GB in it. Not bad seeing as that's where the entire OS and all of your applications are stored.

---

### Post by sd@ksu on 2012-06-01
I just now found out that out of 3.5 GB, 2.1 GB is in /usr. I shall move /usr to a separate partition now. Googling and looking in the threads and ubuntu help how to do it. If anyone knows something, please post here..otherwise, I am going to follow these:
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")
and..

[https://help.ubuntu.com/community/HowtoPartition/ResizingPartition]("https://help.ubuntu.com/community/HowtoPartition/ResizingPartition")
.............
My case will be a little different but essentially the same. I have ubuntu installed through VMWARE in my win-7 machine.

---

### Post by sd@ksu on 2012-06-02
Instead of moving the /usr to a separate partition, I thought about increasing the size of root partition. So I did that after booting from gparted live cd. Oh, btw, I have ubuntu installed inside vmware as a guest in a win-7 host. So after I did that size increase of root form ~ 9 GB to ~ 22 GB and a decrease in size of /home from ~150 gb to ~ 123 gb, it took gparted a while to configure those changes. After that I rebooted into the machine and seems to work fine. But than I found another problem: size of a vmdisk file abnormally became high (~ 130 GB itself) whereas the whole vmware file (or folder) before this change was ~ 40 GB. I did not find a reason for this. And it was the first thing in the morning. I just deleted whole of it and will re-copy my vmware backup into the system again. But can anyone shed some light on this sudden side increase in vmware?

---

### Post by philinux on 2012-06-02
It is unlikely root would have used up 9gig. My system is at 5 out of 12. After 2 years.

---

### Post by sd@ksu on 2012-06-02
@ philinux: one question...do you use your system often? Do you usually do updates regularly...If so and still it is at 5 out of 12...then it gives me relief...I would just re-copy back my old vmware copy of ubuntu...and do nothing more...but the above question still bothers me...

---

### Post by philinux on 2012-06-02
> **sd@ksu said:**
> @ philinux: one question...do you use your system often? Do you usually do updates regularly...If so and still it is at 5 out of 12...then it gives me relief...I would just re-copy back my old vmware copy of ubuntu...and do nothing more...but the above question still bothers me...

Yep. This particular system is running 10.04 and is fully up to date. One thing that can get out of hand over time is old kernels. Easily sorted.  Via [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/) or use a gui like bleachbit. Also see man apt-get autoremove and others.

---

### Post by sd@ksu on 2012-06-02
@ phillinux...can u please look here : [http://ubuntuforums.org/showthread.php?t=1993583]("http://ubuntuforums.org/showthread.php?t=1993583")
...
I see you are still using 10.04. I am looking for maintaining 3 ubuntu systems for our lab and those should run forever...say for another 15 years without any security problems. Will ubuntu work somehow (11.04) or I should look for some other linux distro?

---

