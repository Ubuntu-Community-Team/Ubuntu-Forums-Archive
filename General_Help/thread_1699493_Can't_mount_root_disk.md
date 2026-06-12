---
title: "Can't mount root disk"
date: 2011-03-03
forum: General Help
---

### Post by klasko! on 2011-03-03
Hello, I can't mount my Ubuntu partition.

I was using my PC when it suddenly crashed, so I rebooted. When Ubuntu started again, it said that it was mounting, but I rebooted again. 

So, now when I start it tries to mount the main partition but it can't. Then appears <initramfs> and I don't know what to do.

Thanks, and sorry if you can't understand me, my mother language is the spanish.

---

### Post by TeoBigusGeekus on 2011-03-03
Boot up with a live cd, open a terminal and
```
sudo fsck /dev/sda1
```
Replace sda1 with actual root partition. You can find it with 
```
sudo fdisk -l
```
fsck will check your partition for errors and try to fix them.

---

### Post by klasko! on 2011-03-03
> **TeoBigusGeekus said:**
> Boot up with a live cd, open a terminal and
```
sudo fsck /dev/sda1
```
Replace sda1 with actual root partition. You can find it with 
```
sudo fdisk -l
```
fsck will check your partition for errors and try to fix them.

I've tried to boot with an Ubuntu 7.10 live CD and it shows me the same screen that showed Ubuntu when I booted from the HDD. 

Then I tried with a 10.10 live CD and it had an error. Apparently, it can't read some metadata.

I'll try with a USB key.

---

### Post by klasko! on 2011-03-03
I booted from a live CD and I can open my Windows partition, but I cant open Ubuntu-s partition.

When I try, it displays the following message > 

Unable to mount 79 GB Filesystem

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---------

---

### Post by klasko! on 2011-03-04
Can anyone help me?

---

### Post by roopeshmicasa on 2012-02-18
> **klasko! said:**
> I booted from a live CD and I can open my Windows partition, but I cant open Ubuntu-s partition.

When I try, it displays the following message > 

Unable to mount 79 GB Filesystem

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---------

Hi Klasko! 

Have you solved your problem with mounting your system drive. If yes, then please look into my problem. Here is link to my problem. 
[http://ubuntuforums.org/showthread.php?t=1914197](http://ubuntuforums.org/showthread.php?t=1914197)

Sorry, This reply is not solution but asking for help. I am new to ubuntu and linux based OS and don't have that much of knowledge here. I am not that Techie :( . Please look into the problem and see if this problem can be resolved. My problem seems to be much like your problem. Help will be much appreciated. Thanks in advance

---

