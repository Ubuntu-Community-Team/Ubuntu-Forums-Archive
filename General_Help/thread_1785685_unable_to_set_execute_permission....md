---
title: "unable to set execute permission..."
date: 2011-06-18
forum: General Help
---

### Post by jainanupam on 2011-06-18
Hello Everyone,

I have a triple boot system with Ubuntu 11.04, Windows 7 and Windows-XP on it.

My disc configuration is something like this... ('cause I think it would be required for you to understand my problem) :confused:

I have a 250GB hard disk which was originally partitioned with Windows-XP in six partitions C,D,E,F,G and H (All NTFS type) with 'C' drive having Windows-XP on it and 'D' drive having Windows-7 on it. 

I installed Ubuntu on the 'H' drive by partitioning it into two halves of approximately 20GB each. One partition is named 'New Volume' as per Windows naming scheme. On the other partition I installed my Ubuntu-11.04 OS. As per my plan I would be using this 'New Volume' for all my Ubuntu related data and software only.

I want to install 'Ant' build tool for Java to be usable on my Ubuntu. For this, as described on the Apache Ant user manual I downloaded the 'apache-ant-1.8.2-bin.tar.gz' and extracted it. All this I did in the 'New Volume' drive. 

Now as per the 'Ant' manual I needed to change a file's ('/media/New Volume/ubuntu files/software files/apache-ant-1.8.2/bin/ant') permission to executable, which is currently set to '-rw-------' and I want it to be '-rwx------'. I've tried various things such as 'chmod/sudo' and also tried changing the permission with the 'root' user, but so far I've not been able to change the permissions for this file. However, if I copy the 'apache-ant-1.8.2' folder to '/home' directory then I've been able to change the permission for the concerned file.

Please help me as to what should I do so as to be able to use this folder in my 'New Volume' drive itself?

(duh... M tired now writing such a long post... and would really appreciate you reading this much stuff for me... Thanks) :)

---

### Post by monko909 on 2011-06-18
If you install NTFS-Config and give yourself read/write permissions, that should do it.

---

### Post by jainanupam on 2011-06-19
> **monko909 said:**
> If you install NTFS-Config and give yourself read/write permissions, that should do it.

Thanks monko909. Can you please also tell me how to do that? I'm pretty new to Linux world. Do I have to format the drive for this?

---

### Post by nothingspecial on 2011-06-19
> **jainanupam said:**
>  

As per my plan I would be using this 'New Volume' for all my Ubuntu related data and software only.



ntfs does not support linux file permissions. As you have said this partition is for ubuntu related stuff only, I would format it with a file system that does (ext4 for example).

If you wish to keep it ntfs, then you have to set permissions when you mount it, but simply formatting it would be simpler.

---

### Post by jainanupam on 2011-06-19
> **nothingspecial said:**
> ntfs does not support linux file permissions. As you have said this partition is for ubuntu related stuff only, I would format it with a file system that does (ext4 for example).

If you wish to keep it ntfs, then you have to set permissions when you mount it, but simply formatting it would be simpler.

Thanks, I formatted it with ext4 type and the permissions are now set. Thanks a lot.. :D

---

