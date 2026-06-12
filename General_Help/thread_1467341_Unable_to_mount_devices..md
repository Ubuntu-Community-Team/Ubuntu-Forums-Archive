---
title: "Unable to mount devices."
date: 2010-04-30
forum: General Help
---

### Post by bladze_dcotl on 2010-04-30
I just upgraded to 10.04 and after the install I haven't been able to access any of my other partitions, or any of my external storage devices.  It always tells me that I don't have authorization, and I can't seem to find them using "sudo nautilus."

Thanks in advance

---

### Post by bladze_dcotl on 2010-04-30
Well I was able to mount them using "sudo Dolphin," so I used the opportunity to change the permissions on it.  All said and done, even when I set myself as owner I cannot unmount them, still says I'm not authorized.  So now I'm really confused.

---

### Post by GSF1200S on 2010-04-30
Do you want the devices to be mounted at boot time (are these flash drives, USB hard drives, or internal partitions)? If so, you can just add them to /etc/fstab and they will be mounted when you startup. If not, then you can create a set of bash alias' (very easy) which will allow you to mount and unmount the device at will.

I would tell you how to do it via your desktop, but I dont know exactly what the problem is or where to start. Let me know the answers to above questions though and ill get you setup.

If you decide you want them loaded at boot or you want to use bash aliases, please post the contents of:
```
sudo gedit /etc/fstab
```
and the output of:
```
sudo fdisk -l
```

---

### Post by bladze_dcotl on 2010-04-30
Thank you for the reply.  The answer to your question is:  there are both internal partitions and usb devices that I am having trouble mounting.  I don't need them to mount on boot, but I would like to mount them at will.  If you have any more questions I am monitoring the thread fairly closely.

Thanks again

---

### Post by dcharvey on 2010-05-02
I've been seeing this too, another thread pointed me to the permissions/group memberships (I tried fuse and the admin profile)which I tried tweaking with "sudo users-admin" to no avail so far :(

---

### Post by dcharvey on 2010-05-02
Mine started behaving after a reboot and the group changes I mentioned in the end.  This might help out..

[http://ubuntuforums.org/showthread.php?t=1336847&page=2](http://ubuntuforums.org/showthread.php?t=1336847&page=2)

---

### Post by nitstorm on 2010-05-02
ubuntuforums.orgubuntuforums.org/newreply.php
have you tried *sudo mount *??

if you have ignore the rest of my post..
1. Create a folder to mount your partition into.
```

sudo mkdir path/to/your/folder/where you want to mount the partition
usually
sudo mkdir /media/Storage   (Storage being the name of the folder you want the partition mounted on to

```

2. Learn the partition name from the following code (usually /dev/sda* *here means some number)
```

sudo fdisk -l

```

3. Mount the partition on to the folder that you created in step 1:
```

sudo mount /dev/sda* /media/Storage

```

---

### Post by tcturner on 2010-05-02
found this page it helped me 100% check it out
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by mclode on 2010-05-04
I had the same problem after upgrading from 9.10 to 10.04. I just removed the /media/usb* mount points. Actually I was not that brave, I moved them to a backup folder. My USB devices now mount automatically, with their device names, not just usb0 or usb1 etc.

---

### Post by mclode on 2010-05-04
I also had a problem with another machine, where I could only mount USB devices using the System > Administration > Disk Utility. I got around that one by deleting the FUSE directory from my home directory. I am not sure what side effects that might have though, I have not seen any yet...

---

