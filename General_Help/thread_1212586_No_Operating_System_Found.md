---
title: "No Operating System Found"
date: 2009-07-13
forum: General Help
---

### Post by Chloe24 on 2009-07-13
I am a newbie at using Ubuntu. I installed it off of a Ubuntu live CD onto my PC currently running Windows XP. The hard drive was partitioned successfully. Now, when I remove the Ubuntu CD, I receive the following error message: 'No Operating System Found'. I would like to restore my Windows environment. Any suggestions? Hopefully, I have not caused any damage to my hard drive. By the way, I don't have a recovery CD available. I ran the commands below based on the advise others gave to individuals with a similar problem. Thank you in advance for your help. :cry:
 
$fdisk -l
 
_Device Host_ _Start_ _End __Blocks_ _ID_ _System_
/dev/hda1 1 784 6297448+ 12 Compaq diagnostics
/dev/hda2* 785 12161 91385752+ 7 HPFS/NTFS
 
 
$cat /etc/fstab
 
unionfs / unionfs rw 00
tm fs / tmp tmpfs nosuidg nodev 0 0

---

### Post by iponeverything on 2009-07-13
Boot off the live CD and see if you windows data is still there.

---

### Post by Chloe24 on 2009-07-13
I booted off the live CD. Then I clicked on Plcaes-Network Server. I see there is an icon titled 'Windows Network.' Please tell me if I should be clicking on a different option on the toolbar. Thanks so much.

---

### Post by iponeverything on 2009-07-14
You should see a hard-drive like icon under places.

If you don't see one there, open a terminal and do:

```

sudo bash
mount /dev/hda2 /mnt
cd /mnt
ls

```

See if you see your stuff.

---

### Post by Chloe24 on 2009-07-14
Thanks again. So I entered the code below and the result was 'lost+found'. I recalled that was a folder in the file system. However, the 'lost+found' folder has an 'x' icon above it. When I click on this 'lost+found' folder, I receive the following error message: The folder contents could not be displayed. You do not have the permissions necessary to view the contents of 'lost+found".

---

### Post by merlinus on 2009-07-15
You might try this:

```
sudo mount -t ntfs /dev/hda2 /mnt/hda2
```

and then navigate to that directory using nautilus.

---

### Post by iponeverything on 2009-07-15
I am begining to think that you accidentally nuked your windows partition.

---

### Post by Chloe24 on 2009-07-15
Thanks so much for your help Merlin. I typed in the command you indicated and received the following result:
 
**mount: mount point mnt/hda2 does not exist**
 
What should I do from here?

---

### Post by Superd00per on 2009-07-15
What I usually do when mounting partitions from a live cd is the following:

I open up terminal, enter the following:
```

sudo mkdir /media/windows

```

This should create a directory in /media/ called windows.

Now we mount the NTFS partition to our mountpoint.

```

sudo mount -t ntfs /dev/hda2 /media/windows

```

Get a directory listing:
```

ls /media/windows

```

See if the directory listing contains the normal folders for a windows installation, if it does, then your partition still exists.

---

### Post by Chloe24 on 2009-07-15
Thanks Superd00per. I entered the code you indicated below and received the following result:
 
**mount: wrong fs type, bad option, bad superblock on /dev/hda2, missing codepage or other error.**
 
**In some cases useful info is found in syslog - try dmesg | tail or so**
 
I now type **dmesg | tail. **Several lines initialized except for the following:
 
[17179796.656000] NTFS-fs error (device hda2): read_ntfs_boot_sector(): Primary boot sector is invalid.
 
[17179796.656000] NTFS-fs error (device hda2): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
 
[17179796.656000] NTFS-fs error (device hda2): read_ntfs_boot_sector(): Not an NTFS volume.

---

### Post by Chloe24 on 2009-07-15
One more thing, I clicked on Places-Computer within the Ubuntu toolbar environment. There are four icon. One labeled CD-RW/DVD+-R Drive, the second 6.0 GB Volume:/tmpdisks-onf-hda1, the third casper-cow (when I clicked on this one, I see is pointing to hda2), and the fourth is filesystem. 
 
Thanks again.

---

### Post by Superd00per on 2009-07-16
As you can read, your installation is left without a boot sector, since i get a feeling you are trying to get back on windows, i suggest you go and get a windows cd, boot up with it and use the recovery console to restore the MBR, by entering FIXMBR and FIXBOOT into the console.

If this is not what you are trying to do please leave a message.

---

### Post by Chloe24 on 2009-07-16
That is what I am trying to do. Thank you all for your time and efforts.

---

