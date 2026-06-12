---
title: "Grsync copies everything everytime"
date: 2012-08-29
forum: General Help
---

### Post by canek1 on 2012-08-29
Im using Grsync to backup my home directory to an external FAT32 hard drive. Every time I sync, it syncs everything, not just the files that have changed. 
I know about the time difference problem with FAT drives, and tried the option "--window-modify=3600" to compensate for different timestamps. Also tried "size only" option, and "always checksum" option. No dice.
The rsync command that's being created is:
> rsync -r -t -p -v --progress --delete -l -s /home/myname /media/Verbatim HD/Backup Folder
I don't understand most of it. I'd be grateful for any suggestions.

---

### Post by dcstar on 2012-08-30
> **canek1 said:**
> Im using Grsync to backup my home directory to an external **FAT32 **hard drive.
.........

Total waste of time.

Do not back up Linux to rubbish Windows filesystems, they are **not** compatible.

Format the external drive with a Linux filesystem or just stop wasting your time as your backup will be partially useless.

---

### Post by canek1 on 2012-08-31
The drive is full of other backups and I can't offload them now. Thanks for the thought though. 

Can anybody else help me out here?

---

### Post by Lars Noodén on 2012-08-31
I wouldn't keep anything you care about on FAT.  So I echo dcstar's recommendation and move to a serious file system ASAP so you don't lose your files.

About the rsync formula, it is important to remember closing slashes for the directories.  Also, -a for archive is useful, it's the same as -rlptgoD

```

 rsync -av --progress --delete /home/myname/ /media/Verbatim HD/Backup Folder/ 

```

You can also use -n for dry run to see what it will update or copy.

---

### Post by Dennis N on 2012-08-31
> **canek1 said:**
> 
I know about the time difference problem with FAT drives, and tried the option "--window-modify=3600" to compensate for different timestamps. 

To prevent all files copying due to the time stamp difference, a correct option is: 

--modify-window=1

I've used this for a long time to do rsync to FAT filesystems including flash drives and it works. No problems.

---

### Post by canek1 on 2012-08-31
yes, i tried --modify-window=1 but no success. the problem might be the trailing / on the directories but I don't see why as long as the target and source don't change each time I run the program. I havent got my hard drive here to test at the moment, I'll try it out next week.

thanks for warnings re. FAT32. I'll keep it in mind for my next drive but for now any solutions should take into account that thsi is what Im stuck with.

---

### Post by oldfred on 2012-08-31
Just to add to why not FAT32.

I was backing up to FAT32 but it was a compressed file. I wondered why it always was 4GB even as system seemed to grow. Then I learned 4GB is maximum that FAT32 can save. It also does not have a journal, so chkdsk is harder to run.

Also any system files like the . files in /home will lose permission and ownership. Your data files if less than 4GB should be ok.  So at least parts of your backup will be difficult to restore.

---

### Post by Dennis N on 2012-09-01
> **oldfred said:**
> Just to add to why not FAT32.



Linux filesystem on the rsync destination is best, but it depends on the situation. For example, the destination is a flash drive (or external HD) where the files are going to be also used with a Windows computer. Then, you don't want a Linux file system on that flash drive.

---

### Post by oldfred on 2012-09-01
Unless it is a camera flash drive, mp3 player or other device that requires FAT32, then NTFS is better for compatibility with Windows. Not sure about Macs and what they might require.

NTFS has a journal so chkdsk from a Windows repairCD can often repair it and it supports files over 4GB. 

But if Linux system files you need to be backing up to a Linux file system to preserve ownership and permissions. 

Data can be backed up to anything that works with your other systems. Permissions or ownership can be reset if required easily on data, but system files vary in ownership, not always root and permissions. So it can be very difficult to reset. Resetting permissions & ownership in /home is possible since the owner is the owner and permissions are 664 for files and 775 for folders, with only a couple of exceptions.

---

