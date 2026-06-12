---
title: "Live CD Hdd storage"
date: 2009-10-13
forum: General Help
---

### Post by jahoehn on 2009-10-13
Hi, I was just wondering where do documents get saved on the HDD when your using a live disc. I just installed flash while on the ubuntu live cd and this just seemed somewhat odd to me. I figured most file types would just be stored in memory or swap space on the disc but being able to install programs just seems.... not possible.

---

### Post by lotuseclat79 on 2009-11-07
Hi jahoehn,

To save a document on your hard drive you need to issue a few commands:
1) Issue the command:

$ sudo fdisk -l

Sample output follows:
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fd95fd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   83  Linux
/dev/sdb2              14        9538    76509562+  83  Linux
/dev/sdb3            9539        9729     1534207+  82  Linux swap / Solaris

This will let you know what disks/partitions you have available for storage.  For example, I have a Linux distributions installed on its own separate hard drive, and the above output is relative to it.

In the following example set of commands, assume you are the Live CD default user with the text file document you wish to save, doc.txt, in the Desktop directory, i.e. /home/ubuntu/Desktop.

2) Create a mount point for mounting your hard drive:

$ sudo mkdir /tmp/disks-conf-sdb2

3) Issue the mount command:

$ sudo mount -v -t ext3 /dev/sdb2 /tmp/disks-conf-sdb2
Note: the type of file system on the installed Linux is ext3, the device name is /dev/sdb2, and the mount point which the above mkdir command created is as shown.

4) Become root:

$ sudo -i

5) Navigate to the root directory of your hard drive

# cd /tmp/disks-conf-sdb2/root

5) Make a directory for documents:

# mkdir Documents

6) Visit the Documents directory:

# cd Documents

7) Issue the following commands to save the document on your hard drive, assuming you are the default Live CD user (ubuntu):

# pushd ~ubuntu/Desktop
# cp -p doc.txt /tmp/disks-conf-sdb2/root/Documents
# pushd
# ls -lt doc.txt
# popd
# umount /dev/sdb2

You are now back in your Desktop directory as user ubuntu (if that is where you started from before the above command to become root, i.e. sudo -i, and the document, doc.txt has been saved to your hard drive and can be deleted from Desktop if it is no longer needed for the current Live CD session.

-- Tom

---

