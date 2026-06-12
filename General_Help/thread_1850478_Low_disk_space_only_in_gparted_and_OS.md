---
title: "Low disk space only in gparted and OS"
date: 2011-09-26
forum: General Help
---

### Post by oc_alex86 on 2011-09-26
Hello,
I tried to extend my /home partition using gparted since it was almost full. 
I had 18Gb and I added 10 Gb. 
After reboot, I still have the "low disk space" warning message. 
When I check in gparted, 99% of my /home partition is full. 
This is not the case when I check with the "disk usage analyzer". 

What can I do? I tried to do a fsck but the problem remains.

---

### Post by dcstar on 2011-09-27
> **oc_alex86 said:**
> Hello,
I tried to extend my /home partition using gparted since it was almost full. 
I had 18Gb and I added 10 Gb. 
After reboot, I still have the "low disk space" warning message. 
When I check in gparted, 99% of my /home partition is full. 
This is not the case when I check with the "disk usage analyzer". 

What can I do? I tried to do a fsck but the problem remains.
Try:
```
sudo e2fsck -f /dev/whatever
```
or:
```
sudo resize2fs /dev/whatever
```

---

### Post by mcduck on 2011-09-27
> **oc_alex86 said:**
> Hello,
I tried to extend my /home partition using gparted since it was almost full. 
I had 18Gb and I added 10 Gb. 
After reboot, I still have the "low disk space" warning message. 
When I check in gparted, 99% of my /home partition is full. 
This is not the case when I check with the "disk usage analyzer". 

What can I do? I tried to do a fsck but the problem remains.

What does running "df -h" in a terminal say?

The disc usage Analyzer probably isn't giving you the information you think it does. The percentages it shows are not telling  how much of space is used or available. Instead they are showing the amount of data relative to the amount of data in parent directory. And also it's by default set to scan all filesystems, so unless you limit it to just a certain filesystem it's useless for telling the used/free space. 

The purpose of Disc Usage Analyzer is to tell *where* your disk space is being used, not how much disc space you have . For that purpose you can check System Information, use commands like *df* or simply check the values Nautilus or Gparted report.

---

### Post by oc_alex86 on 2011-09-27
Hello,

Thanks a lot!
sudo resize2fs worked for me.

---

