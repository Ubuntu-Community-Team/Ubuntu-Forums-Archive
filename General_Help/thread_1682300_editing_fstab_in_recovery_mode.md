---
title: "editing fstab in recovery mode"
date: 2011-02-05
forum: General Help
---

### Post by apesa on 2011-02-05
Hello, I have made an entry in fstab that is keeping me from booting. I am able to get into recovery either from entering "M" as it is trying to mount my bad entry or from Grub. 

However once in recovery I am unable to save my edits in vi. I have tried several attempts at saving my edits to no avail. What trick will I have to impose in order to clean up my fstab so I can boot successfully.

Thanks much,
Pat

---

### Post by quadproc on 2011-02-05
> **apesa said:**
> 
However once in recovery I am unable to save my edits in vi. I have tried several attempts at saving my edits to no avail. What trick will I have to impose in order to clean up my fstab so I can boot successfully.

This sounds like you don't have privilege while running vi; try
```
sudo vi /etc/fstab
```and see if that works.

Another thing to watch out for is the ownership and permissions of your edited file.  It may be easier and safer to copy your original fstab to your home directory, edit it there, save it there, set its ownership and permissions there, then copy it back to /etc/fstab.

quadproc

---

### Post by apesa on 2011-02-05
Thanks, but I think it is more than that. I have tried sudo as well as cp. I am getting the error, Cannot "do whatever I am trying to do": Read Only Filesystem.

I get this when trying to edit as sudo vi or when trying to cp to another dir..

Must be some trick in managing the filesystem or modes

When trying to edit in vi I am getting the following error:

W10: Warning: Changing a readonly file
E303: Unable to open swap file for "fstab". recovery impossible

---

### Post by quadproc on 2011-02-05
> **apesa said:**
> Thanks, but I think it is more than that. I have tried sudo as well as cp. I am getting the error, Cannot "do whatever I am trying to do": Read Only Filesystem.

This sounds like you are in recovery mode.  If you booted from the recovery mode entry, the system will have mounted / as a read-only volume.  So you won't be able to write to any file on that partition.

If you have another working OS on the disk in another partition, you could use that to access and fix the fstab in question.  You will need to either chroot or to mount the partition with the damaged fstab.

Otherwise, you will need something such as a Live CD (likely either CDROM or USB stick) to boot from.  While running the Live CD you will be able to mount the partition and work on it with the editor.  Please remember to umount the partition when you are finished with it.

quadproc

---

### Post by apesa on 2011-02-05
Thanks, that worked. I did not realize the filesystem was specifically readonly in recovery mode. It seemed to easy to vi a couple lines out and reboot.

Thanks again, 

Pat

---

