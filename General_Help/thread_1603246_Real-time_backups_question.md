---
title: "Real-time backups question"
date: 2010-10-22
forum: General Help
---

### Post by etech22 on 2010-10-22
Hello,

I have several VirtualBox VMs that are backed-up regularly on an Ubuntu 10.04 64-bit server. They are Windows XP or Vista guests. Right now, I have the VMs shutdown, copy the .vdi files, then boot the VMs back up. My question is, would backing up the virtual disks while the VMs are running cause any problems? 

I'm not sure how the Linux filesystem works for large file copies; does it take a 'snapshot' of a large file before copying it, or will real-time changes made to the disk image during the copy be included? (assuming the changes are on a part of the disk that hasn't been copied yet?)

Also, this is just a simple file copy, not a clone/copyhd VBoxManage process.

Simple or detailed answers welcome!

Thanks,

etech22

---

### Post by blueridgedog on 2010-10-22
I believe that a file system level copy of a large changing file will result in unpredictable errors.  I would either backup with the vm's off or use the clone tool.

---

### Post by psusi on 2010-10-22
> **etech22 said:**
> 
My question is, would backing up the virtual disks while the VMs are running cause any problems? 

Yes.

> **etech22 said:**
> I'm not sure how the Linux filesystem works for large file copies; does it take a 'snapshot' of a large file before copying it, or will real-time changes made to the disk image during the copy be included? (assuming the changes are on a part of the disk that hasn't been copied yet?)

No.  Copying just reads the source file and writes it to the destination.  If parts of it change before you read them, then you get the change, otherwise, you don't.  This means that some some parts of the copy will be up to date and some won't, giving you a corrupt file.

If you use LVM then you can create a logical volume to use for the VM, then shut down the vm for just a moment, create an lvm snapshot, then restart the vm and back up the snapshot while the vm makes changes to the original.

---

### Post by etech22 on 2010-10-22
> **psusi said:**
> If parts of it change before you read them, then you get the change, otherwise, you don't.  This means that some some parts of the copy will be up to date and some won't, giving you a corrupt file.
Ok, thanks for the clarification.

> **psusi said:**
> 
If you use LVM then you can create a logical volume to use for the VM, then shut down the vm for just a moment, create an lvm snapshot, then restart the vm and back up the snapshot while the vm makes changes to the original.
This sounds pretty useful, I'll look into using a logical partition. Thanks.

---

### Post by etech22 on 2010-10-22
Follow-up question:

How would someone handle backing up a VM in a high-availability environment, where it's ideal to keep the VM running, without having to restart services after a reboot? Would a RAID mirror or another solution take care of this?


etech22

---

### Post by blueridgedog on 2010-10-22
vboxmanage on the command line may be able to make a backup of a live image.

---

