---
title: "Format...."
date: 2009-07-01
forum: General Help
---

### Post by Sabrage on 2009-07-01
Hey. I just need to know the command to write to delete the whole harddrive in terminal. It´s  a newbie question I know...

---

### Post by -kg- on 2009-07-01
OK, not sure what you're asking here.  Since a hard drive cannot be deleted :p you either want to remove all partitions off the hard drive, or all the files in one or more partitions on the hard drive.

The answer to either one of these is, yes.  Which one do you want to do, and what are you trying to do?

---

### Post by Sabrage on 2009-07-01
Ok sorry what I meant was delete the files on the harddrive.... the easiest way I found was to use a ubuntu-disk and install ubuntu, but there has to be a command?

---

### Post by -kg- on 2009-07-01
OK.  The easiest way to delete the files (ALL the files, mind you) on a partition would be to launch GPartEd and reformat the partition.  Of course, this can't be done on a partition that is mounted (i.e., if you're looking to delete all files on your /root partition, the only way to do this is to boot to the Live CD).

There is also the "rm" command, but care must be taken with it.  It is quite destructive and, depending on what you're trying to do, can wipe out a lot of stuff with one misstep.

What is it, exactly, you're trying to do?

---

### Post by Sabrage on 2009-07-01
I´m trying to **delete all files on my harddrive, and I have ubuntu installed**......

---

### Post by -kg- on 2009-07-01
OK, if you delete all the files on your hard drive, then your Ubuntu installation will go with it.  Is that what you want to do?

---

### Post by Geoff918 on 2009-07-01
Is this your primary hdd or a secondary hdd? There are commands both to format a hdd and also to simply remove all of the files which is what I think the other poster was replying to.  Are you attempting to change the file system (e.g. from ext3 to ext4 or FAT32 to NTFS)? Are you attempting to "uninstall"/erase Ubuntu? If you include your goals it would make responding a bit easier.

---

### Post by -kg- on 2009-07-01
Exactly.  My response would need to be tailored to what you're trying to accomplish.  I could just give you a reply, but cause you to delete something that you didn't want to be deleted.

---

### Post by Sabrage on 2009-07-01
OK here´s the deal: I had an old computer that I wanted to give away. It had Ubuntu on it (8.04 I think) and some files I was not able to delete. I don´t understand why I wasn´t able to delete those files from the thrashcan, but I didn´t have the permission. So then I thought: the next best thing is to delete all the files on the computer. But I couldn´t even do this! So the third option that I just did was to re-install ubuntu because then I knew all the files would be deleted. That´s it. But I would be grateful if you could say how I can delet files I don´t have permission to delete.

---

### Post by -kg- on 2009-07-01
OK.  No problem.

I will assume you have a Live CD.  Boot to the Ubuntu Live CD (or the GPartEd Live CD would be even better, if you have one), boot to the Desktop, and launch GPartEd from "System/Administration/Partition Editor".

Once GPartEd scans your disk, you will be presented with a graphical representation of your Hard disk and all the partitions on it.  One by one, select each of the partitions and mark it for Deletion.  Once you have all the partitions marked for deletion, click the "Apply" button on the top toolbar.

Once all the operations have completed and the disk re-scanned, you will see the entire hard disk represented with no partitions on it.  It has been completely wiped of all information.

A note...if you re-installed Ubuntu, this will wipe the former information off of the partitions _only if_ you format the previous partitions in which you install.  If you do not select to format the partitions, the information will remain...only the default installation files will be changed.

I tell you to delete the partitions off the hard drive...that is tailored to your situation.  Alternatively, you can select the partition(s) you wish to wipe and, instead of deleting them, you can reformat them.  That will also wipe all the files off of them, saving you having to re-create them afterwards.

That is the quick and easy way.  The "rm" (remove...much the same as the "del" command in DOS or the Windows Command Line Interface) command can also be used.  Go to a terminal and type:

```
man rm
```

This will pull up the manual on the "rm" command and it's parameters, and will explain how this command can be used.

<edit> I re-read your last post.  If you re-installed Ubuntu, I will assume that you did the "Manual Partitioning" method and installed (and reformatted) the original partitions.  If not, you will have installed Ubuntu on separately created partitions, side by side with the original.

I say this because it's a common mistake I've seen.

---

### Post by Sabrage on 2009-07-01
Thanks -kg-! This was the information I was looking for! I´m sure I will be in the same situation soon and then I will know what to do. Thank you!

---

### Post by -kg- on 2009-07-01
No problem, and glad I could help.

---

### Post by merlinus on 2009-07-01
Understand that just because you deleted partitions does not mean the files cannot be recovered.  

The best way is to burn dban to a disk, boot from it, and then delete everything.  That way you can be sure the files cannot be recovered without someone spending thousand of dollars to do so, and even then it may not be possible.

---

