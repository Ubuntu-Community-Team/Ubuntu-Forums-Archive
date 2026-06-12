---
title: "Formating Question"
date: 2010-05-10
forum: General Help
---

### Post by khryss on 2010-05-10
i have a (many) external drives. in order to be usable in linux do i need to reformat them in ext2, 3 ,4 or can i just leave them in ntfs and it will be ok?

---

### Post by arsenic23 on 2010-05-10
It'll be fine.
You could format them if you wanted, but you'll be able to access your ntfs drives from Ubuntu.

---

### Post by khryss on 2010-05-10
and it doesnt matter how long i read/write to them (ntfs) in ubuntu they will maintain readability in both windows and ubuntu ??(not that i ever plan to go back to windows but if i ever have to it would be nice to have all my stuff)

---

### Post by mister_playboy on 2010-05-10
I would suggest leaving them NTFS until the time you are ready to go 100% Linux only... :)  Assuming you ever choose to do that, of course. ;)

---

### Post by florus on 2010-05-10
Ubuntu can read/write ext3, ext4 and ntfs file systems. Windows can only use ntfs so if you want to access your data from both systems you must use ntfs.

---

### Post by DJ_Max on 2010-05-10
> **khryss said:**
> and it doesnt matter how long i read/write to them (ntfs) in ubuntu they will maintain readability in both windows and ubuntu ??(not that i ever plan to go back to windows but if i ever have to it would be nice to have all my stuff)
No you still need Windows to defrag NTFS. At least you need access to one to occasionally defrag it

---

### Post by khryss on 2010-05-10
Dj_Max,
"you still need Windows to defrag NTFS. At least you need access to one to occasionally defrag it"
would i be able to defrag that with a windows install on a virtual machine?

---

### Post by DJ_Max on 2010-05-10
> **khryss said:**
> Dj_Max,
"you still need Windows to defrag NTFS. At least you need access to one to occasionally defrag it"
would i be able to defrag that with a windows install on a virtual machine?
I don't see why not

---

### Post by srs5694 on 2010-05-10
IMHO, more important than defragging is the need to run CHKDSK on NTFS volumes after power failures, system crashes, or accidentally unplugging the disk from the computer without first unmounting it. If you do that, you won't be able to access an NTFS drive from Linux until it's been checked from Windows.

In theory, you should be able to do this from Windows run in a virtual machine; however, in practice it depends on how the VM is configured. Specifically, it must be given direct access to the relevant Linux device file. I imagine that most VMs permit this, but I can't make any promises on that score.

---

### Post by bheussler on 2010-05-25
I have a dual boot, triple partition system.  My two OS's are Mac OS X and ubuntu 10.04.  I have a 30GB HFS+ Journaled parition for Mac operating files and a 20GB ext4 parition for linux operating files.  Then I have 200GB NTFS Data partition that allows me to read/write back and forth from each partition.  Is it possible to defrag the ntfs partition from linux using a disk utility program or wine to run a windows disk utility program?

---

### Post by mgol on 2010-05-25
> **mister_playboy said:**
> I would suggest leaving them NTFS

If it has NTFS on it at all. Imagine that - I bought external WD Elements HDD, 1 TB space. It was formatted to... FAT32. One partition. This was the only moment in my life when I saw a terabyte-sized FAT32 partition.

BTW, Windows default tools don't allow partitions larger than about 25 GB to be formatted to FAT32...

---

### Post by srs5694 on 2010-05-25
> **bheussler said:**
> I have a dual boot, triple partition system.  My two OS's are Mac OS X and ubuntu 10.04.  I have a 30GB HFS+ Journaled parition for Mac operating files and a 20GB ext4 parition for linux operating files.  Then I have 200GB NTFS Data partition that allows me to read/write back and forth from each partition.  Is it possible to defrag the ntfs partition from linux using a disk utility program or wine to run a windows disk utility program?

Not AFAIK. Furthermore, NTFS is a very poor choice for a Linux/OS X shared-data partition. The reason is that there are, AFAIK, no good tools for NTFS maintenance in either of the OSes you're using. When the system suffers a power failure or crash, the NTFS partition is likely to be left in a state that will require a disk check, and with no tools to do that, you may become unable to access the partition until you move the drive to a Windows system to do the job.

IMHO, you should switch that NTFS partition to either HFS+ or FAT. HFS+ works well in both OSes, and of course OS X has solid HFS+ maintenance tools. OTOH, you may need to adjust your permissions to get everything working with it, and you'll have to use it in unjournaled mode or Linux won't be able to write to it. FAT also works, and there are maintenance tools for it in Linux and OS X; however, it's got limits on file sizes and it can be slower than a more modern filesystem.

---

### Post by mgol on 2010-05-25
> **srs5694 said:**
> FAT also works, and there are maintenance tools for it in Linux and OS X; however, it's got limits on file sizes and it can be slower than a more modern filesystem.

And it gets fragmentation like hell. I use mainly Linux so I made most of my partitions to be ext3/ext4, but if I wanted to share data between Windows and Ubuntu, I'd choose NTFS - for its speed, moderate lack of fragmentation etc.

With OS X it's obviously different; I don't know if you can even write data to an NTFS partition under OS X.

---

