---
title: "Access Ubuntu ext4 ext. disk within WindowsXP"
date: 2009-07-08
forum: General Help
---

### Post by pepe_cz on 2009-07-08
[FONT=Verdana]Hello all,


I have my Ubuntu 9.04 with ext4 file system installed on external disk. 
I want to connect to this external disk (Ubuntu ext4) via USB and access from WindowsXP SP3.
Is there any utility  to allow accessing external disk with ext4 file system (at least read) within WindowsXP?
Thank you!

Regards,
Pete
[/FONT]

---

### Post by 5nak3 on 2009-07-08
I could be very wrong, but I thought windows could only use NTFS and Fat file systems.

In which case the ext4 system would not be accessable by windows.

---

### Post by pepe_cz on 2009-07-08
It means there is no way how to read/write ext. disk with ext4 file system(my ubuntu 9.04)?
Peter

---

### Post by credobyte on 2009-07-08
Not sure if it will read ext4, but .. give it a try : [http://www.fs-driver.org/](http://www.fs-driver.org/) ;)

---

### Post by 5nak3 on 2009-07-08
As I said I'm not 100% sure, but if I am correct in saying that windows cannot read ext4 then you will not be able to access it....unless there is a software solution.

I'm not sure, but i've not seen anything to do what you are describing.

---

### Post by michy99 on 2009-07-08
There are windows drivers to access ext2/3 filesystems, but I don't know if there are any that work with ext4.

---

### Post by cariboo on 2009-07-08
You'll just have to wait for the windows guys to catch up again.

There is a possibility you may be able to acces the files, have a look at this [article]("http://www.linuxjournal.com/article/9449").

---

### Post by pepe_cz on 2009-07-08
I just give a try to  [http://www.fs-driver.org/](http://www.fs-driver.org/) - and it seems that it doesn't work for ext4 file system.
Peter

---

### Post by zo3adams on 2009-07-08
One idea worth considering is to install Linux in a Virtual Machine under Windows, you can forward the USB port that the port is plugged into to that VM.

The "host" Windows OS and the Virtual machine can easily share folders so this route will give you access to the drive from Windows Explorer. Though it may be overkill for just achieving disc access.

Highly recommend Virtual Box, install and usage is painless, can find out more here:
[http://www.virtualbox.org](http://www.virtualbox.org)

VMware free trial is another option.

---

