---
title: "Running 10.10 on Assus eepc 4g"
date: 2011-11-29
forum: General Help
---

### Post by Jacob72 on 2011-11-29
Hello,

I am running Ubuntu 10.10 on my now old Eee pC 4gb. Due to the small hard drive I am not able to update to a newer version. That is OK with me, Ubuntu seems to working fine. I have about 1.1gb left on the drive but have to be really careful with updates e.t.c.. 

I would like advice on what I can do to keep within my drive capacity/and even increase the capacity if possible? whilst getting the most out the computer.

I have an external Sd 8gb hardrive and will try and use portable versions of programs I need. 

Am I able to link folders between the external hard drive and say Desktop or Places Documents?

Edit: Can I get portable software via the Ubuntu Software Center and have it installed on my external hardrive?

Any help is appreciated.

Thanks

---

### Post by JRV on 2011-11-29
You can Use your 4 gig drive as / and put /home on an SD card.

There is a catch that stops the installer from installing on a small drive that will cause problems. To get around this check out my thread on this problem:

[http://ubuntuforums.org/showthread.php?t=1876241](http://ubuntuforums.org/showthread.php?t=1876241)

---

### Post by Jacob72 on 2011-11-29
Thanks, Sounds great but I am a novice and sounds a bit above me at the mo. 

Does / mean partition?

I have been going through and removing some of the software that comes with the install.

Edit: Now that I removed the software it says I have less free space than before?

---

### Post by JRV on 2011-11-29
> **Jacob72 said:**
> Thanks, Sounds great but I am a novice and sounds a bit above me at the mo. 

Does / mean partition?

Yes, the main system partition is called /, that is it's mount point.
> 
I have been going through and removing some of the software that comes with the install.

Edit: Now that I removed the software it says I have less free space than before?

That sounds weird, how are you removing it?

> 
Am I able to link folders between the external hard drive and say Desktop or Places Documents?

Edit: Can I get portable software via the Ubuntu Software Center and have it installed on my external hardrive?


That won't work, software installs in your / partition.


Localepurge is a good utility to save disk space, see my tutorial here:

[http://ubuntuforums.org/showthread.php?t=1867813](http://ubuntuforums.org/showthread.php?t=1867813)

---

### Post by Jacob72 on 2011-11-29
I removed them via software center.

Edit;
>  Localepurge is a good utility to save disk space, see my tutorial here:

Wow, these must have been the first set of instructions that have worked for me straight off

Thanks

---

### Post by JRV on 2011-11-29
Open a terminal and run these commands:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

---

### Post by Jacob72 on 2011-11-29
Done that - seemed to work. Now / is back to having 1.2gb free space, which is strange because I Open Office was oneof the programs I removed.

---

