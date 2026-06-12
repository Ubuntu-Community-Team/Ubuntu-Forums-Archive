---
title: "gParted issue"
date: 2010-10-31
forum: General Help
---

### Post by iCHRYST on 2010-10-31
Hello everyone.

I've recently switched to Ubuntu and need to convert my 1TB NTFS drive to ext4 so as soon as I boot up my system I can listen to music without having to mount the drive.

I searched google for options and the only option I got was to use gParted to shrink the partion, make an ext4 partion, move data, rinse, wash, repeat. I tried to do this, however gParted failed.

Unfourtinately, I don't have a spare 500GB+ drive to backup my data on and my main filesystem only has a few 100GB's free.

Any help on this matter would be greatly appriciated. I attached a link to the details from the gParted error at my dropbox. You can find the link below.

Kind Regards,
iCHRYST.

[http://dl.dropbox.com/u/14086609/gparted_details.htm](http://dl.dropbox.com/u/14086609/gparted_details.htm)

---

### Post by papibe on 2010-10-31
I was in a similar situation last time I had to shrink a ntfs partition. If I remember correctly it is recommended to (1) do a system clean (remove temps files), and (2) defrag your disk in windows before trying gparted.

If you did that and get the error anyway, you have two options: Vista and Windows 7 both have tools to manage partitions including shrinking. If you have XP, or for some reason you couldn't do it with the last tools: I recommend Norton Partition Magic.

Good Luck!

---

### Post by schmutztaucher on 2010-10-31
I recommend you defrag the drive at least five times before performing any shrinking.

---

### Post by trikster_x on 2010-10-31
You may even need to run a scan of your disks before doing this operation.  Love it or hate it, Gparted actually attempts to make sure it will have the lowest possible chance of data loss when resizing partitions, and this means checking a drive for errors and defragging ntfs file systems.  You can run fsck on it from a linux terminal or live cd for the scanning portion, but I'm afraid I don't know of any defragging software.  If you have windows, I would suggest just mount it there, then defrag and run a chkdsk /f on it.  That should fix your partitioning woes.

---

### Post by ezsit on 2010-10-31
It sounds like you just do not have the tools for the job. You need a temporary storage drive to hold the files while you convert the drive in question. 

You have a 1TB drive with only a small percentage of free space. Any shrinking and converting process takes free space to work properly. Sure, you can attempt it, but don't complain when the process fails and you have lost your data.

To do the job properly, backup your data, reformat the drive in question, and restore your data. Any other advice risks your data. It is your choice.

---

### Post by oldfred on 2010-11-01
While I encourge you to convert from NTFS, you can mount the NTFS partition directly into /home or mount folders into /home using linking. NTFS does not support permissions & ownership but still can share files with windows & Ubuntu. With NTFS you still need a windows repair disk in case you have to run chkdsk.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

---

### Post by iCHRYST on 2010-11-02
Thanks for your help everyone.

I ended up getting the problem sorted (sorry I didn't mean to ignore any of your advice about backing up but I had noway to back up my data).

My solution was as followed (for refrencing):

When setting up the partitions in gParted, if I tried to divide the partitions with big blocks of space (Say, 200GB+) it would fail. What I did, was slowly start dividing my hdd using smaller partioning of about 40GB-80GB. After I did this 3-4 times I was then able to divide my partitions in much larger chunks.

Again, thank you for your help everyone. It was very much appreciated. :)

---

