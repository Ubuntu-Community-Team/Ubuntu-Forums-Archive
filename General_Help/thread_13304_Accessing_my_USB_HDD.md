---
title: "Accessing my USB HDD"
date: 2005-01-30
forum: General Help
---

### Post by behrangsa on 2005-01-30
Hi

I've a USB HDD and it's plugged into my system. How can I access it using Ubuntu? I can't see it in my "Disks"...

Thanks in advance,
Behrang S.

[BTW - Congratulations on creating such a beast ;)]

---

### Post by TryMe on 2005-01-30
Open a terminal and try this:

Sudo mkdir /mnt/usbhd

mount /dev/sda1 /mnt/usbhd

To make this automatic after you mount it edit your /etc/fstab
add:
/dev/sd?1 	/mnt/usbhd	fat32      rw		0	0

Now reboot your system.

Remember that you USB hard drive must be formatted fat32 for this to work. If it is not you need to change the fat32 in the fstab entry to ext3 or what ever it may be formatted with.

---

### Post by behrangsa on 2005-01-31
[QUOTE=TryMe]Open a terminal and try this:

Sudo mkdir /mnt/usbhd

mount /dev/sda1 /mnt/usbhd

To make this automatic after you mount it edit your /etc/fstab
add:
/dev/sd?1 	/mnt/usbhd	fat32      rw		0	0

Now reboot your system.

Remember that you USB hard drive must be formatted fat32 for this to work. If it is not you need to change the fat32 in the fstab entry to ext3 or what ever it may be formatted with.[/QUOTE]
 Thanks alot.

 My HSDD is NTFS so I guess I have replace fat32 with NTFS... let me try and see it.

Regards,
BS.

---

### Post by TryMe on 2005-01-31
Open up synaptic 
Search for ntfs
Add 
libntfs-gnomevfs
ntfstools

synaptic should sort out any dependences
apply the packeges

Open up a terminal and run:
sudo /sbin/fdisk –l
Look for the line like
/dev/sda1             1      2125   4283968+  07  NTFS/HPFS
The (sda1) part might be different
Terminal run:
sudo mount /dev/sda1 /mnt/usbhd -t ntfs -r 

sudo ls –l /mnt/usbhd

if everything went well you should see your ntfs files. But root is the only user that can see the files. I am not sure but an edit /etc/fstab might just fix that.

edit /etc/fstab
/dev/sd?1 /mnt/usbhd  ntfs uid=1001,gid=root,ro 1 0

Reboot

UID may vary according to user id. you can also simply input username
Keep also in mind that NTFS in Linux is read-only

Hope that helps

---

