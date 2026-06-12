---
title: "taking snapshot in kvm"
date: 2012-03-05
forum: General Help
---

### Post by akshay.sulakhe on 2012-03-05
Hello friends, i am working on a project where i need to take a snapshot of the ubuntu system i am running and save the snapshot file on my hard disk.i have to do it with certain requirements though.firstly i need the kernel with symbol generation enabled,which i have done. I have also installed kvm,libvirtd,virt manager,virt goodies. But i dont know what to do after this,how to takethe snapshot of the system i am currently running,i researched a bit,but its not going smooth. Can anyone tell how to take a sbnapshot. I am currently running ubuntu desktop 11.10. I hope the details are enuf.

---

### Post by Ms. Daisy on 2012-03-08
Are you running Ubuntu in a virtual machine?

Is this homework?

---

### Post by akshay.sulakhe on 2012-03-08
No,ubuntu is my host os,but want to take snapshot of my host os only.

---

### Post by comperocean on 2012-03-13
> **akshay.sulakhe said:**
> Hello friends, i am working on a project where i need to take a snapshot of the ubuntu system i am running and save the snapshot file on my hard disk.i have to do it with certain requirements though.firstly i need the kernel with symbol generation enabled,which i have done. I have also installed kvm,libvirtd,virt manager,virt goodies. But i dont know what to do after this,how to takethe snapshot of the system i am currently running,i researched a bit,but its not going smooth. Can anyone tell how to take a sbnapshot. I am currently running ubuntu desktop 11.10. I hope the details are enuf.
kvm-img snapshot -c $(snapshot-name) $(image file)

---

### Post by bodhi.zazen on 2012-03-14
> **akshay.sulakhe said:**
> No,ubuntu is my host os,but want to take snapshot of my host os only.

Snapshots are for guests, not the host.

Are you looking for a backup strategy for the host ?

See

[https://help.ubuntu.com/community/Bacula](https://help.ubuntu.com/community/Bacula)

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by akshay.sulakhe on 2012-03-14
@comperocean :- what do i put in the snapshot name and what is the type of image file,i want it raw without any encryption.

@bodhi.zazen :- truly speaking,it wont matter for me,i want to take a snapshot of the system,which has a  kernel with symbol generation enabled.

---

### Post by bodhi.zazen on 2012-03-14
> **akshay.sulakhe said:**
> @bodhi.zazen :- truly speaking,it wont matter for me,i want to take a snapshot of the system,which has a  kernel with symbol generation enabled.

you need to clarify what you mean by "snapshot of the system". There are at least two "systems" - host and guest.

If you are talking about a snapshot of the host, you can not do that with kvm snapshot.

If you are talking about a snapshot of the guest, you have several options. Perhaps the easiest is to simply copy (backup) the virtual image.

---

### Post by akshay.sulakhe on 2012-03-14
Thanks for the reply. I talked with my professor,he said for guest os.so,i need to modify the guest kernel to enable symbol generation,which i know how to do. Can u guys tell me how to take a snapshot of guest ubuntu in rawformat,or shall i use the command given before in the thread??? Many thanks. Sorry for being so troublesome. :-)

---

### Post by bodhi.zazen on 2012-03-14
you would make a snapshot with the command you were given. Just be sure you understand the difference between a snapshot and a backup.

from man kvm

> -snapshot

Write to temporary files instead of disk image files. In this case, the raw disk image you use is not written back. You can however force the write back by pressing C-a s.

form man kvm-img

> snapshot [&#8722;l | &#8722;a snapshot | &#8722;c snapshot | &#8722;d snapshot ] filename

List, apply, create or delete snapshots in image filename.

[http://linux.die.net/man/1/qemu-kvm](http://linux.die.net/man/1/qemu-kvm)


[http://man.cx/kvm-img%281%29](http://man.cx/kvm-img%281%29)

---

### Post by akshay.sulakhe on 2012-03-14
@bodhi thanks for the information. It is really helpful. I want to save the entire system state,thus the snapshot,to a raw file,which i will process further. So i guess i will need to use C -a -s. Thank you very much.

---

### Post by akshay.sulakhe on 2012-03-18
@bodhi.zazen  & @comperocean :- Just one last thing,while taking the snaphot only i want to save the image on my other hard disk. So,should i just cd into the directory where i want to save the snapshot or do i need to do something else? And the final command i would need is 

kvm-img snapshot C -a -s $(snapshot-name) $(image file)

Thanks for all the help all you guys.

---

### Post by akshay.sulakhe on 2012-03-18
Someone had also asked me,is this my homework. No,its not. I need the image for my project. I was preparing to start my work,so,gathering data.:-)

---

### Post by bodhi.zazen on 2012-03-18
> **akshay.sulakhe said:**
> @bodhi.zazen  & @comperocean :- Just one last thing,while taking the snaphot only i want to save the image on my other hard disk. So,should i just cd into the directory where i want to save the snapshot or do i need to do something else? And the final command i would need is 

kvm-img snapshot C -a -s $(snapshot-name) $(image file)

Thanks for all the help all you guys.

I am not really sure what you want or if you understand what a snapshot in KVM is.

A snapshot is a record of how the system was at a certain point in time and is part of the data stored in your disk image.

The way you keep phrasing the question makes me think you want a backup, and in that case you simply shut down the machine and copy the disk image.

The copy will include any snapshots as the snapshot data is stored in the disk image.

---

### Post by akshay.sulakhe on 2012-03-18
@bodhi :- to be more clear,this is what i am trying to do. the following link below is a software which i have to run on the image i obtain. Kindly go in the section:- Mounting a virtual disk image. This is a directed link from parsing debugging symbols,which is a little bit on the upper hand of the webpage. This will say everything i must. Many thanks again for the patience u show.

Link:- 
[http://code.google.com/p/insight-vmi/wiki/LinuxDebugSymbols#Mounting_a_Virtual_Disk_Image](http://code.google.com/p/insight-vmi/wiki/LinuxDebugSymbols#Mounting_a_Virtual_Disk_Image)

---

### Post by bodhi.zazen on 2012-03-18
The work "snapshot" is nowhere on that page.

---

### Post by akshay.sulakhe on 2012-03-18
Thanks for the reply. This is what i found important.

"When using KVM or QEMU as the hypervisor, the disks in raw format can be directly mounted into the host's file system. To check if a file, for example image-file.bin, is in raw format, the qemu-img utility can be used: "

So,to get this raw format,dont i need a snapshot of the system,or do i just copy the .img file in /var/lib/libvirt/images/imagename.img and then use it? Sorry for all the confusion. Thanks again.

---

### Post by bodhi.zazen on 2012-03-18
No. A snapshot in virtual machines it roughly the same as hibernation or suspend. You can turn the VM on and it is restored to that state (it does not "boot"). Snapshots have nothing to do with data or backup.

Snapshots have little to do with what  you want.

You want to convert the disk image to raw format.

Converting to a raw image depends on what format it is in now (qcow, etc).

See [http://linux.die.net/man/1/qemu-img](http://linux.die.net/man/1/qemu-img)

There is a whole section on conversion

```
qemu-img <your-image> -O raw name.img
```

---

### Post by akshay.sulakhe on 2012-03-18
@bodhi.zazen :- Thanks for the command,it didnt work though. On the website,it was mentioned as to how to check if the image is raw. I did the test,results are

Terminal output:-

root@akshay-System-Product-Name:/var/lib/libvirt/images# qemu-img info test1.img
image: test1.img
file format: raw
virtual size: 15G (16106126848 bytes)
disk size: 15G


Although it had with the fileformat bin on the webpage,i had img. I also referred to the manpage to try to use the convert option. But no luck.

The real problem is what is the filesystem type of such images. I want to execute a command to mount this image,but it keeps saying,i must specify the filesystem type:-

here is the command execution. Kindly tell me what is the filesystem type to be specified. I tried to search,nothing yet.

root@akshay-System-Product-Name:/var/lib/libvirt/images# DEV=$(losetup --find) && losetup -o $((63 * 512)) $DEV test1.img && mount -o ro $DEV /mnt
mount: you must specify the filesystem type

Kindly let me know. I know i have put you through a lot of trouble today. Many many thanks for all your help.

---

### Post by akshay.sulakhe on 2012-03-18
Finally converted it to bin,i mean the command is still working,i didnt use verbose mode.. :-(. ... Now just one error,could not find any free loop device. That also is done. Just the mount command. :-)

---

### Post by bodhi.zazen on 2012-03-18
test1.img is already raw, you do not need to convert it

---

### Post by akshay.sulakhe on 2012-03-18
@bodhi.zazen :- Thanks yet again for the help.Last step remaining 

root@akshay-System-Product-Name:/var/lib/libvirt/images# DEV=$(losetup --find) && losetup -o $((63 * 512)) $DEV test2.bin && mount -o ro $DEV /mnt
mount: you must specify the filesystem type

I still converted it,as it was in the page. Now this is some problem with mount. Managed to delete unused loop devices too. :-) After this it gets mounted,and life becomes easy.

---

### Post by bodhi.zazen on 2012-03-18
Sorry, but I am not following that command. Without an error message or better understanding of what the command is doing, I do not know. 

Perhaps ask in the project's mailing list.

---

