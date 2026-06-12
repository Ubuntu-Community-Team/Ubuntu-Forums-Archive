---
title: "mounting partitions"
date: 2009-08-07
forum: General Help
---

### Post by franar on 2009-08-07
hi people,
i have on my computer the following structure:

partion 1: windows vista 150gb (ntfs)
partion 2: windows vista recovery 17gb (ntfs)
partion 3: data 200gb (ntfs)
partion 4: Ubuntu 9.04 50gb ext2 or ext3 (i can't remenber now)
partion 5: ubuntu swap 4gb


my music and other stuff are in partition 3. so i must mount the drive each time a need access to it.
my question is: i have to mount it every time, because it is ntfs? if it is type "ext", is it mount by itself?

---

### Post by Diskotekno on 2009-08-07
I use a couple of different methods for this. The first is you can bookmark it in Nautius and it will always appear under "Places". Or You could make a symbolic link to the drive on your desktop.

I can attempt to provide you with more detailed info as needed.

If the drive was ext3 it would come up automatically afaik

---

### Post by NightwishFan on 2009-08-07
Ubuntu is a bit iffy with mounting drives automatically. As far as I know there is no simple graphical tool to configure it, though I may be wrong.

In order to have a drive mount automatically, you can:

[LIST=1]
[*]Partition manually at install time and create a mount point for the drive.
[*]Edit the /etc/ftab file to include the drive. I will look up how to do this, as I have only done it once or twice myself.
[/LIST]

Links:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by michy99 on 2009-08-07
Check out this page:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

---

### Post by burmanabhay88 on 2009-08-07
If you don't want to use commands, I'd advice "Disk Manager", you'll find it in the Add-Remove Programs. It's simple to use, has a great GUI. Do tell me what you use finally, or if you need any assistance with the s/w

---

### Post by franar on 2009-08-07
actually i use windows just for the ipod mmanage with itunes (i have not find something like it, working in ubuntu) and for viewing blu ray discs.

so i will like to reduce/eliminate the ntfs partitions, doing so some weeks ago I try using the gparted, so i start to resize and it said finished, but when i tried to start both system (ubuntu and windows) i did not get sucess....so to format and start again......

which others tool can help me manage partitions on a simpler way to gparted?

---

### Post by Diskotekno on 2009-08-07
> **michy99 said:**
> Check out this page:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)



Cool, this thing is the simplest. Forget my silly work around fixes!

---

### Post by franar on 2009-08-07
excelent!
this must work for me.
thanks You all

---

