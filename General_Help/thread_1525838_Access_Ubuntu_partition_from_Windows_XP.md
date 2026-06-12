---
title: "Access Ubuntu partition from Windows XP ?"
date: 2010-07-07
forum: General Help
---

### Post by user1001 on 2010-07-07
Hi

the title says it all :)

any suggestions, btw none of these worked :S 
[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)

thanks.

---

### Post by mikewhatever on 2010-07-07
The article you posted lists ext2 and ext3 file systems, whereas the current Ubuntu installations use ext4 by default. You could either select ext3 during the installation of Ubuntu or look for another tool.

---

### Post by warfacegod on 2010-07-07
From what I understand, the ext2/3 drivers for Windows are iffy at best. I'm not sure an ext4 driver even exists yet and, if it does, it's likely to be a very long time before it's even close to stable.

Normally Windows can't read Linux filsystems and MS likes it that way just fine.

The only reasonable option is to have your /home folder in a Windows readable format such as FAT32 or NTFS. On the other hand, that *can* cause Ubuntu issues. So it's somewhat of a trade off.

---

### Post by snowpine on 2010-07-07
Microsoft has omitted this basic functionality from their operating system for some bizarre reason. :(

---

### Post by warfacegod on 2010-07-07
> **snowpine said:**
> Microsoft has omitted this basic functionality from their operating system for some bizarre reason. :(

It's not bizarre at all. They see it as making it easier for their customers to use the competition.

---

### Post by user1001 on 2010-07-07
I downloaded ext2 volume manager it says the file system is ext3 but when I go to my computer and try to open the partition it says it's not formatted and asks me if I'd like to format it :S:S
BTW I am using ubuntu 10.04LTS

---

### Post by philinux on 2010-07-07
> **user1001 said:**
> I downloaded ext2 volume manager it says the file system is ext3 but when I go to my computer and try to open the partition it says it's not formatted and asks me if I'd like to format it :S:S
BTW I am using ubuntu 10.04LTS

I would not do that.

If you did a default 10.04 install then the ubuntu partition will be **ext4**.

The volume manager does not support ext4.

---

### Post by user1001 on 2010-07-07
> **philinux said:**
> I would not do that.

If you did a default 10.04 install then the ubuntu partition will be **ext4**.

The volume manager does not support ext4.

hmm, :( it looks like there is no way to access the files from windows :\..

---

### Post by dnguyen1963 on 2010-07-07
No, there is no way you can access Ubuntu folders from Windows. It is so much easier to access Windows folders from Ubuntu.  Just paste the Linux files into Windows folder then reboot into Windows to access the files.  BTW, you might have to install ntfs-3g and ntfs-config before you can mount the windows partition.

---

### Post by philinux on 2010-07-07
> **user1001 said:**
> hmm, :( it looks like there is no way to access the files from windows :\..

If you create a data partition in ubuntu you can format it ntfs and then put files there.

Both linux and windows can then access the files.

---

### Post by user1001 on 2010-07-07
> **philinux said:**
> If you create a data partition in ubuntu you can format it ntfs and then put files there.

Both linux and windows can then access the files.

yeah =)..

though I was trying to access the var folder :)

---

