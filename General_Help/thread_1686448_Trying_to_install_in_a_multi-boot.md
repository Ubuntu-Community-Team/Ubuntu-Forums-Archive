---
title: "Trying to install in a multi-boot"
date: 2011-02-12
forum: General Help
---

### Post by cptrohn on 2011-02-12
Hello on this beautiful saturday morning!

OK, here is my issue....

I am trying to install Ubuntu 10.10 on a 4rth partition that is right at 275 GB.  For school I have to have WinXPpro, Vista Business and Win7Pro all installed in their own partitions.  

So here is where I am in the install process and the error message that I am getting, First of course I booted the livecd, then connected to the internet so I can go ahead and update and install some codecs during installation.... then I clicked next and got to the partitioner.

Here is where things are giving me problems.  I have not used the advanced options in ubuntu's partioner before so I was hoping that I could just find an install in free space option (like Fedora uses) Seemed to be one but it is not working for me.. So I used a Gparted live CD to create an ext4 partition in the free space I had allocated on the HD.  Restarted the install process got back to the partioner, got to the advanced options and set it up to install to the ext4 partion.  It starts the install process and then I get this error after a few seconds. 
```
No Root Filesystem is defined
please correct this from the partitioning menu
```

Am I missing a step in the process?  

Any help or ideas is greatly appreciated, thanks!


Never Mind, Solvesd

---

### Post by Habeouscorpus on 2011-02-12
If you're doing a manual partition, you have to label it / and bootable. It doesn't do it on it's own.

---

