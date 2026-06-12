---
title: "Hard drive space issue..."
date: 2009-11-23
forum: General Help
---

### Post by danking12 on 2009-11-23
Hi,

I just recently upgraded to Karmic. I did a fresh install and format of all drives. I have a separate 1 TB drive for my home directory. Of this when I do a "df -h", I see that the formatted size is about 917 GB, the size in use is 215 MB and the available size is 871 GB.

Of these values I have two questions, why is the size in use 215 MB? I have one user and it claims my home directory has about 32 MB, where is the almost 200 extra MB going? My second question is why does it say my available size is only 871 GB when my capacity is 917 GB and it says I am only using 215 MB.

Thanks for the info and help.

Dan King

---

### Post by oldfred on 2009-11-24
I thought I read somewhere that it reserved 20% space so some commands show the reserved and some do not.

I then found this link that says it is only 5% and you can adjust the amount:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

settings and lots of info (did not work on ntfs partition):
sudo tune2fs -l /dev/sda1

---

