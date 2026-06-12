---
title: "changing home folder location"
date: 2010-11-06
forum: General Help
---

### Post by RastaManPower on 2010-11-06
hello guys i have a new partition on my first hard disk and i would like to make it as my home folder.
the partition is dev/sda5 and it is a ext4 partition
how do i make this my home folder? i tryed lookign around the foum but i couldnt find a working way to change it. thanck you
[IMG]http://img72.imageshack.us/img72/4282/screenshotuj.png[/IMG]

---

### Post by sohlinux on 2010-11-06
make sure that partition is being mounted at boot as /media/sda5/ if not then you must add it to /etc/fstab file then ...

go to system - admin - users/groups you can change your home folder location in the advanced settings to /media/sda5/home/your_name

---

### Post by RastaManPower on 2010-11-06
this is my fstab file. where and what do i have to add?
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=cc680660-da2e-4995-a2ff-f6223e25217a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=aa5be350-70dc-4971-b0e9-8374f3f44dda none            swap    sw              0       0

---

### Post by sohlinux on 2010-11-06
make a backup of your fstab file

install mountmanager from ubuntu software center then add the mountpoint of partition /dev/sda5/ to /media/sda5 , you can call it /media/home if you like as long as you do the same in users/groups advanced settings 

reboot to make sure it mounts at boot before you the change your home folder location

---

### Post by RastaManPower on 2010-11-06
i dont understand how this program works.. cant i just add a line onn the fstab file?

---

### Post by RastaManPower on 2010-11-06
i managed to setup the automount for the partition...i tryed changing the home directory from  home/nico  to  /media/a90be7ee-abb5-409e-95ef-292972d5cd73
i click ok and everything seems to work.. but after i click on the home icon and it opens up my old home directory...how come its not changing?

[IMG]http://img261.imageshack.us/img261/2066/screenshotot.png[/IMG]

---

### Post by sohlinux on 2010-11-06
did you try rebooting?

---

### Post by dcstar on 2010-11-07
> **RastaManPower said:**
> i managed to setup the automount for the partition...**i tryed changing the home directory from  home/nico  to  /media/a90be7ee-abb5-409e-95ef-292972d5cd73**
i click ok and everything seems to work.. but after i click on the home icon and it opens up my old home directory...how come its not changing?


No. That is totally wrong, /home partitions should only be set up in /etc/fstab.

There are detailed instructions already for setting up separate /home partitions and moving data to them, please search them out and follow them.

---

### Post by sohlinux on 2010-11-07
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by srs5694 on 2010-11-07
The [psychocats link](http://www.psychocats.net/ubuntu/separatehome) provided by sohlinux seems good, although I've only skimmed it. Also, it starts with a description of partition resizing that's irrelevant to RastaManPower, since that seems to have already been done.

I feel compelled to point out that some of sohlinux's other suggestions in this thread are poor. Specifically, you should *not* attempt to mount a new filesystem in /dev/home or change the user home directory location to /dev/sda5/home/your_name. The /dev directory holds device node files, which are a special type of file used to access hardware. For instance, the /dev/sd* files access SCSI disk devices, or non-SCSI disk devices that employ the Linux SCSI subsystem. Normal files, including user home directories, should *not* be stored or mounted in /dev. You can use /etc/fstab to tell the system where to mount the devices (such as mounting /dev/sda5 to /home), and thereafter most other tools will refer to the files and directories on that partition via their mount points (as in /home/your_name). Misunderstanding this issue can lead to serious problems. I'm not sure you'd even be able to log on using a GUI if you were to set your home directory to /dev/sda5/home/your_name. (You can log in using text mode that way, but the system complains about an invalid home directory and doesn't load any account-specific settings.)

---

### Post by sohlinux on 2010-11-07
I was simply going by my own experience which worked just fine but in my case my home folder was set to another drive /dev/sda2. since you only have 1 drive I cant see much point in changing the location, you could simply put a symbolic link to your other partition if you are running out of space.

---

