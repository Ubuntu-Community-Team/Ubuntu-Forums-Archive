---
title: "Help with a FAT32 drive."
date: 2009-10-13
forum: General Help
---

### Post by ppirilla on 2009-10-13
I have hard drive in an external enclosure, formatted as FAT32.

There should be ~60 GB of data on this 200GB drive.

When I mount it in Ubuntu, the system tells me that there is ~60 GB of used space, but no files actually show up in the directory listing.

**Edit: to be more specific, the directory structure is present on the disk, but each folder is empty.**

I'm not sure what diagnostic tools are available for FAT disks under Linux so any suggestions or links would be appreciated.  A Google search turned up many advertisements for windows software, but nothing linux-based.

Thank you.

---

### Post by oldfred on 2009-10-13
Are you mounting it correctly, for Fat & NTFS all permissions are given at the time of mounting.

HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu
[http://ubuntu.swerdna.org/ubufat32.html](http://ubuntu.swerdna.org/ubufat32.html)

Explanation is in above link for variables:
mount -t vfat -o umask=0000,utf8 /dev/sda3 /path_to/mount_point

You can also download storage device manager from synapic and it has settings for all drives, but is intended for permanent mounts to fstab.

---

### Post by beastrace91 on 2009-10-13
I also recently had issues mounting a friend's 500 gig external hard drive (which was formatted to fat32 ICK) What ended up working for me was attaching it to a Windows VM and then returning it to my Ubuntu system. Not sure exactly what this did - but it worked. Personally unless you have some reason for it I would recommend formatting any drive over 4gigs to ext3 (or ntfs if you need Winblows to see it)

~Jeff

---

### Post by prshah on 2009-10-13
> **ppirilla said:**
> 
I'm not sure what diagnostic tools are available for FAT disks under Linux so any suggestions or links would be appreciated.

For linux, you can use dosfsck. The drive (partition) to be checked MUST be unmounted. So, if it is mounted, please unmount it (ie, right click on desktop icon and choose unmount, or use the umount command from the terminal).

After unmounting, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo dosfsck -a /dev/sdb1
``` (replace /dev/sdb1 as suitable). This will run an autorepair ('-a').

Note that there is a possibility of data loss so you do this at your own (minimal) risk. Sometimes, dosfsck may need to be run multiple times.

Post back if you need further help.

---

### Post by ppirilla on 2009-10-13
> **prshah said:**
> For linux, you can use dosfsck. The drive (partition) to be checked MUST be unmounted. So, if it is mounted, please unmount it (ie, right click on desktop icon and choose unmount, or use the umount command from the terminal).

After unmounting, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo dosfsck -a /dev/sdb1
``` (replace /dev/sdb1 as suitable). This will run an autorepair ('-a').

Note that there is a possibility of data loss so you do this at your own (minimal) risk. Sometimes, dosfsck may need to be run multiple times.

Post back if you need further help.


Well, it "fixed" the drive.  Now it reports that the drive is completely empty.  I'm fairly certain that there was nothing on the drive of high importance, so I'm not going to worry about it.

I had just wanted to double-check my backups before reformatting.  I'll just assume they were up to date and move on.

---

