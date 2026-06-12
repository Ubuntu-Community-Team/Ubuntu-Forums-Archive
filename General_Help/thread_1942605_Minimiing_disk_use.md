---
title: "Minimiing disk use"
date: 2012-03-17
forum: General Help
---

### Post by ldude7 on 2012-03-17
I've recently replaced Windows with Ubuntu on an old laptop. The computer is primarily used for web browsing via wifi (including numerous flash games, video, audio, etc.) Word 97 is also used through wine. 

The system has only about 750MB memory and what seems to be a very slow hard drive.

What can be done to minimize disk access? (Are there nonessential processes the can be stopped?)

---

### Post by Tamlynmac on 2012-03-17
> ldude7

you may wish to look at [this]("http://lubuntu.net/about"). It's designed for light weight systems that have limited resources.

Good Luck
Mac

---

### Post by dave2001 on 2012-03-17
Well, you can stop your disks from spinning down in idle by adding the line ```
hdparm -B 254 /dev/sda
```to the file /etc/rc.local just before the "exit 0" line. That might speed things up a *little*.

There's also a way to keep swap file usage in your ram only, or at least reduce the frequency of ram to hdd swap file transfers, but sadly I don't remember the specifics.

As Mac suggested, you may want to try Ubuntu with LXDE. It has much lower resource usage. I use it on my ancient A20m Thinkpad, which has even less ram than yours. The Lubuntu spin comes with it installed by default, but you can also install everything needed for LXDE to your already running Ubuntu installation, and then remove unnecessary Gnome and Unity related packages afterward.

In order to get the lightest load possible on my old A20m, I installed a  base system, put the LXDE on top of that, and chose the rest of my  packages carefully.

Another small suggestion, Abiword is a great low-resource usage linux word-processor which should do just about anything Word97 does, and you can run it natively instead of through WINE, so it should be a bit more responsive.

---

### Post by Rodney9 on 2012-03-17
+ 1 for Abiword
+ 2 for Lubuntu

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by BertN45 on 2012-03-18
Xubuntu or Lubuntu would be a good choice. Lubuntu has a desktop like Windows 2000 and uses around 90MB after booting, while Xubuntu has nicer desktop and uses 130MB after booting. Why do you think the cause is that the disk is slow? Ubuntu will be slow as soon as it starts swapping and that is true for almost all disks.

---

### Post by rng on 2012-03-18
If your system is swapping too often you can adjust swappiness. 
To check its current value, command is: 
```
cat /proc/sys/vm/swappiness
```
Default value is 60. To reduce swapping, make the value 10 by the command: 
```
sudo sysctl vm.swappiness=10 
```
To make the change permanent (persisting after reboot), command is:
```
sudo echo vm.swappiness=10 >> /etc/sysctl.conf 
```

---

### Post by BertN45 on 2012-03-18
> **rng said:**
> If your system is swapping too often you can adjust swappiness. 
To check its current value, command is: 
```
cat /proc/sys/vm/swappiness
```
Default value is 60. To reduce swapping, make the value 10 by the command: 
```
sudo sysctl vm.swappiness=10 
```
To make the change permanent (persisting after reboot), command is:
```
sudo echo vm.swappiness=10 >> /etc/sysctl.conf 
```

That will not work. If the problem is not enough memory for the programs used, the OS will have to swap. Telling it to avoid swapping   will not help. Telling it to swap earlier and more aggressively could help, because that would be done, while the system (cpu/disk) is less loaded. It would also be done before the user issued the request, resulting in less disk IO during the request itself and thus in better response times. Try swappiness of 90 or 100. Early and more aggressive swapping (paging) is one of the reasons, why Windows 7 runs better then Vista.

If you think the disk is slow, run the disk utility from the dash, which has some disk benchmarks. Average read throughputs of 60-100MB/sec are normal. Average seek times should be between 12 - 18 msecs. SATA for desktops are the best and IDE for laptops are in the lower ranges. Larger disks tend to have a higher throughput. Some disks have the best throughput in the begin of the disk, you can see that using the above benchmark. If so put the SWAP partition in the begin of the disk. If the second partition is the OS, most disk IO will be concentrated in the begin of the disk and the disk heads have to travel the minimal distance, resulting in shorter seek times for most of the disk IO.

You could also put the swap partition on an usb stick, if the read throughput gets close to the 30MB/sec. Access (seek) times are 1-2 msec. It improves your response times during swapping, partly also because you divide the disk IO over two units. With USB sticks I would use the default swappiness to keep it alive somewhat longer.

---

### Post by wojox on 2012-03-18
If you mount a file-system with option, "noatime" the inode access times will not be updated. This means that if a cached file or directory is read, the disk will not spin up. Edit /etc/fstab

```
/dev/sda1 /home ext4 defaults,noatime 0 0 
```

---

### Post by TenPlus1 on 2012-03-18
+1 for Lubuntu
+1 for noatime

---

