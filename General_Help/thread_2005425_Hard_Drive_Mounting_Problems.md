---
title: "Hard Drive Mounting Problems"
date: 2012-06-17
forum: General Help
---

### Post by HTPro on 2012-06-17
So I am really confused about how to get my 3 internal storage drives mounted the way I want them.  I have 4 drives in total 3 for media and 1 for the Ubuntu and applications.  The other 3 are all formatted for NTFS and I have them currently mounted in the media folder. they are named red, blue, and yellow.  Currently they each have 3 folders called red blue or yellow and only 1 of each works.  Also before I can access them on my network I have to load it on the local machine.

How I want it done is 2 folders, folder1 and folder2 within the media folder. I want 2 hard drives to be mounted to folder1 and the other drive mounted to folder2. I also dont want to have to open the drives on my local machine before being able to access them after a reboot. 

I am running Ubuntu 10.04 and here is what I have in my fstab.  If someone can help me out that would be greatly appreciated.

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid                   0  0  
/dev/sda1                                  /               ext4  errors=remount-ro                     0  1  
# swap was on /dev/sda5 during installation
UUID=3b3da673-df17-4ee3-9592-883fb9a5c75a  none            swap  sw                                    0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8              0  0  

 
```

---

### Post by audiomick on 2012-06-17
I can't talk you through that, but here is the relevant page from the Ubuntu documentation. I gather it isn't that hard to work out.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

