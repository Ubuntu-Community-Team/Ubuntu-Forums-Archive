---
title: "why there is no snapshot tool in ubuntu"
date: 2011-12-17
forum: General Help
---

### Post by grvsaxena419 on 2011-12-17
Hello all, I am currently using ubuntu 11.10, it had deja dup pre-installed on the system, its a backup and restore utility, but it doesn't support snapshots. There is no such tool for snapshotting in ubuntu. I know that taking snapshots requires Filesystem support, are there any other problems associated ? I would like to know this. 
I want to write a system backup and restore utility which could have continuous backup so I want to know if any already exists.

---

### Post by claracc on 2011-12-17
You can install different snapshot software in ubuntu:
[http://askubuntu.com/questions/76914/ubuntu-screenshot-program](http://askubuntu.com/questions/76914/ubuntu-screenshot-program)

---

### Post by guestolo on 2011-12-17
Is this software more of what you are talking about?
[http://backintime.le-web.org/](http://backintime.le-web.org/)

---

### Post by grvsaxena419 on 2011-12-17
@claracc sorry but , I was talking about system backup and restore not screenshot. A backup of system is known as snapshot.
@guestolo This is a backup software, I am interested in something similar to windows system restore.

---

### Post by dcstar on 2011-12-17
> **grvsaxena419 said:**
> @claracc sorry but , I was talking about system backup and restore not screenshot. A backup of system is known as snapshot.
@guestolo This is a backup software, I am interested in something similar to **windows system restore**.

"windows system restore" only exists because of how crappy and fragile Windows always has been.

People move from Windows to Linux because it **isn't** an OS that need crutches like "windows system restore".

---

### Post by grvsaxena419 on 2011-12-17
Hello dcstar ,
> **dcstar said:**
> "windows system restore" only exists because of how crappy and fragile Windows always has been.

People move from Windows to Linux because it **isn't** an OS that need crutches like "windows system restore".
Actually this isn't a windows vs linux thing, everyone needs backup of their important data, whatever the OS may be, it isn't like if you use linux you would never ever have a data loss, linux also needs data backup and there are things like LVM in linux similar to windows VSS. I just wanted to know what are the disadvantages of LVM or any other existent snapshot technology in linux.

---

### Post by vasa1 on 2011-12-17
> **grvsaxena419 said:**
> .., everyone needs backup of their important data...

Isn't Windows "restore" limited to OS-specific settings and the My Documents folder or whatever it's called? If one stores important data anywhere else, it isn't covered?

---

### Post by wildmanne39 on 2011-12-17
Hi, you can use the backup software that comes with ubuntu it is called deja dub, if using an older release then 11.10 you will need to intsall it, or make a clone of your drive using clonzilla also very good.

There is no restore software that I am aware of.
Thanks

---

### Post by grvsaxena419 on 2011-12-17
Hello Vasa1 , 
> **vasa1 said:**
> Isn't Windows "restore" limited to OS-specific settings and the My Documents folder or whatever it's called? If one stores important data anywhere else, it isn't covered?
In windows7 its not like that , windows system restore is done using VSS [http://en.wikipedia.org/wiki/Shadow_Copy](http://en.wikipedia.org/wiki/Shadow_Copy)
this is not specific to documents folder rather its much more featured. It works with filesystem support and you can restore versions of each file also ie per file based restore, its much better than windows XP used to have. Anyways I wanted to know about disadvantages in such softwares available in linux not go into windows. I just gave windows as an example of such software other examples could be LVM.

---

### Post by grvsaxena419 on 2011-12-17
Hello wildmanne39, Thanks for your reply.
> **wildmanne39 said:**
> Hi, you can use the backup software that comes with ubuntu it is called deja dub, if using an older release then 11.10 you will need to intsall it, or make a clone of your drive using clonzilla also very good.

There is no restore software that I am aware of.
Thanks

Yes I have used deja-dup , I am using ubuntu 11.10. But I don't think it uses filesystem support and can work on fat/fat32 also. Does it ? It works without filesystem support also its not continuous? Clonezilla I have not used but I would like to know whether it uses file-system support, does it create an image of whole partition ?

---

### Post by wildmanne39 on 2011-12-17
Hi, yes clonezilla can clone your whole drive including window partitions or you can set it to clone what you want it too.
Thanks

---

### Post by grvsaxena419 on 2011-12-17
Hello wildmanne39, Thanks for yor help.
> **wildmanne39 said:**
> Hi, yes clonezilla can clone your whole drive including window partitions or you can set it to clone what you want it too.
Thanks
Thanks I will use that, also are softwares like LVM snapshots better than clone-zilla or deja-dup? Could you tell me which to prefer ?

---

### Post by wildmanne39 on 2011-12-17
Hi, LVM is a logical partition as far as I know it there is not a software called that for backing up your system, you can google it though.

I use deja-dup to do daily backups of my home folder and a few others but I use clonezilla once every so often to make a clone of my drive in case my hard drive fails or file corruption so bad that I have to reinstall, however a person all most never has to reinstall ubuntu, usually it can be fixed by coming to the forum and asking questions.

---

### Post by grvsaxena419 on 2011-12-18
Hello wildmanne39,

> **wildmanne39 said:**
> Hi, LVM is a logical partition as far as I know it there is not a software called that for backing up your system, you can google it though.

I use deja-dup to do daily backups of my home folder and a few others but I use clonezilla once every so often to make a clone of my drive in case my hard drive fails or file corruption so bad that I have to reinstall, however a person all most never has to reinstall ubuntu, usually it can be fixed by coming to the forum and asking questions.
Yeah I know LVM is a logical partition, its a system in which you can take snapshots of your system and then revert your system to older state, its a system restore type program not a backup program and I think we have it listed as a backup program for linux [http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware](http://davestechshop.net/ListOfFreeOpenSourceLinuxUbuntuBackupSoftware) I just wanted to know what disadvantages are there in deja dup against LVM or vice versa. 
Ok nice thanks I will prefer deja dup .

---

### Post by cryptotheslow on 2011-12-18
If you are developing / testing lots of different configurations etc. you may want to consider using VirtualBox on top of your base OS to run virtual machines with which to mess around in without endangering your base system. VirtualBox has a nice feature that you can take snapshots of a VM that can easily be rolled back to if something goes horribly wrong.

Just a thought that may or may not suit your use case.

---

### Post by The Cog on 2011-12-18
If you are interested in snapshotting, you might ifnd the idea of btrfs snapshots interesting. 
[http://blog.rot13.org/2010/02/using_btrfs_snapshots_for_incremental_backup.html](http://blog.rot13.org/2010/02/using_btrfs_snapshots_for_incremental_backup.html)

---

### Post by grvsaxena419 on 2011-12-18
Hello cryptotheslow, Thanks for your reply.

> **cryptotheslow said:**
> If you are developing / testing lots of different configurations etc. you may want to consider using VirtualBox on top of your base OS to run virtual machines with which to mess around in without endangering your base system. VirtualBox has a nice feature that you can take snapshots of a VM that can easily be rolled back to if something goes horribly wrong.

Just a thought that may or may not suit your use case.
Yes I know about virtualbox, actually I wanted to snapshot my whole system rather than just virtual machine.

---

### Post by grvsaxena419 on 2011-12-18
Hello The Cog, Yes btrfs is for snapshot.
> **The Cog said:**
> If you are interested in snapshotting, you might ifnd the idea of btrfs snapshots interesting. 
[http://blog.rot13.org/2010/02/using_btrfs_snapshots_for_incremental_backup.html](http://blog.rot13.org/2010/02/using_btrfs_snapshots_for_incremental_backup.html)
Could you please give me some disadvantages of btrfs.

---

