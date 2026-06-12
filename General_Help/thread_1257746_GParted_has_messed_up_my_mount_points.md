---
title: "GParted has messed up my mount points"
date: 2009-09-04
forum: General Help
---

### Post by ianmillington on 2009-09-04
Can anyone help with this please?

I had 5 partitions on my HDD (self explanatory terms)

Virtual sda1
Data sda2
/ sda5
home sda6
swap

From within kubuntu, using gparted, I deleted sda1 and resized sda2, the purpose being to make the best use of the available free-space. Whilst the operation was successful, the mount point (Data) was lost, and I found no way within gparted of assigning a mount point to the partition.  Worse, the operation seems to have removed key information relating to the others too with the result that on reboot the file system check fails. It seems my fstab file may have got messed up.

I have tried using the live CD. If I try the installation routine, I can assign mount points to the various partitions without formatting - that is with the exception of root. As my system no longer bears any relationship to a new 9.04 install I would like to avoid that if I can. The partitions themselves are there and Okay. In the live CD I can see them and navigate my way through the directories. My question is - is there some utility I can use from the command line that will enable me to recover this?

Thanks in advance

Edit: Here is my (very weird) fstab

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b133a2f8-36d4-402a-a1cc-d463f7c321a6 /               ext4    relatime,errors=remount-ro 0       1
# /Data was on /dev/sda2 during installation
UUID=c659be87-4631-4475-ba75-d36132faf2f7 /Data           ext3    relatime        0       2
# /Virtual was on /dev/sda1 during installation
UUID=f698013e-5397-49f7-982f-d8a12aa453b7 /Virtual        ext3    relatime        0       2
# /home was on /dev/sda6 during installation
UUID=6c9e67c9-8a07-42d0-8cf0-e03bbcf6c06a /home           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=4dfa54b3-e841-4752-b1cb-3d9d57f3f724 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by indytim on 2009-09-04
First off GParted did **NOT** mess anything up.  When you dropped and re-entered the partition, a new identifier was assigned to the new partition, thus YOUR problem.

If you are going to use the uuid method of mount points in /etc/fstab, you will need to find the new uuid for your problem-child partition.  This is accomplished by

```

ls /dev/disk/by-uuid -lh

```

Insert the new uuid into your fstab, re-boot and you should be good-to-go.

IndyTim

---

### Post by ianmillington on 2009-09-04
Thanks.

There are 2 things I don't understand. Firstly, I didn't elect to use a UUID method - I simply removed an unwanted partition (sda1 virtual) and resized (sda2 Data). However, gparted dropped the term Data and would not allow me to assign a name to the mount point (I assume that is different from a "label").

Secondly, I didn't touch sda5 and sda6 at all, so whilst I expected a problem with the enlarged partition I was surprised by what has now happened.

I'll give your suggestion a try.However, your advice on how to insert the output into the fstab file from the command prompt will be most welcome .

Thanks

---

### Post by ianmillington on 2009-09-04
Just to update.

The command that you suggested lists 4 UUIDs. With the exception of the (now defuct) sda1 they are identical to that shown in the fstab file.

---

### Post by ianmillington on 2009-09-04
Further to previous as the UUIDs were identical from the live CD I edited my fstab as follows:

Remove the entry for the Virtual disk and

On all the others I edited the commented out lines so that as an example

"# / was on /dev/sda5 during installation"

now reads

"/dev/sda5" 

Bingo! I am up and running again, so the issue is solved, I am pleased to say. That has saved me hours.

Thanks for the input

---

