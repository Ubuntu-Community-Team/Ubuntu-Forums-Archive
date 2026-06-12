---
title: "how to increase boot partition size"
date: 2012-04-10
forum: General Help
---

### Post by suresh_vandiyur on 2012-04-10
Hi All,

I am using ubuntu 10.10.my boot partition space is very less 2.3MB.Any one can tell me how remove some kernel or increase my boot partition size,because of this am not install my updates. please help me.

Thank you,

Regards,
Suresh Babu

---

### Post by kc1di on 2012-04-10
You can remove the kernels by installing synaptic if it's not already installed from a terminal ```
sudo apt-get install synaptic
```
when installed go to it and search for kernel then select the ones you want to uninstall and remove them.
you can find the one your using now by typing the following in a terminal
(Note: do not remove that kernel) ```
uname -r
```

If you want to increase the partition size you can do so by using gparted which can also be installed by using synaptic or software center. How ever it will not allow you to resize the partition if it is in use.

---

### Post by drs305 on 2012-04-10
Here is a guide I wrote about expanding your Ubuntu partition (often by taking space from Windows):
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

At the bottom of the first post is a link to a page by *srs5694* that contains a very good treatment of the same subject.

---

### Post by suresh_vandiyur on 2012-04-13
> **drs305 said:**
> Here is a guide I wrote about expanding your Ubuntu partition (often by taking space from Windows):
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

At the bottom of the first post is a link to a page by *srs5694* that contains a very good treatment of the same subject.

Hi,

Thanks for information.I dont have windows in my system. shall I resize the /home partion and increase the /boot partition.

Thank you

---

### Post by drs305 on 2012-04-13
> **suresh_vandiyur said:**
> Hi,

Thanks for information.I dont have windows in my system. shall I resize the /home partion and increase the /boot partition.

Thank you


The methods discussed in the guide are fairly universal for taking space from one partition and moving it to another.

It might be best to post a snapshot of your partitions as displayed by Gparted so the helpers have an idea of your setup.

You mention /boot - if you have a separate boot partition it doesn't need to be very large and 2.3Gb is already larger than necessary. However, you may be referring to your 'root' partition - **/**

This is the main partition and most definitely needs to be larger than 2.3Gb. If you have a very large, separate /home partition you should be able to take some space from /home and move it to /. 

The normal installation size of Ubuntu is about 5-8GB, with /home taking up  less than 1GB of that space (excluding your data files).

---

