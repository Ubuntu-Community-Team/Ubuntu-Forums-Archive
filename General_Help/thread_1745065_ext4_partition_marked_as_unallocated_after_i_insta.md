---
title: "ext4 partition marked as unallocated after i installed win 7 on separate partition"
date: 2011-04-30
forum: General Help
---

### Post by ddr3XD on 2011-04-30
My ext4 partition that Ubuntu was installed on is now marked as unallocated after trying to install Windows 7 on an entirely separate partition. As a matter of fact, I didn't even start the install of windows 7. I was trying to **[COLOR=Blue]re-install[/COLOR]** Windows 7 and had the two old ntfs partitions. The "System Reserved" partition that Windows 7 installs and the actual ntfs partition it installs on. As I like to go about and delete the old partitions before every re-installation, i **[COLOR=DarkRed]carefully[/COLOR]** deleted the two ntfs partitions but when I did I it marked my ext4 partition as unallocated. Immediately sensing something was wrong I quit the install process and restarted on my GParted live cd only to find my ext4 partition was in fact marked as unallocated. I panicked and restarted to Ubuntu hoping that it would work just fine but it would not boot. I don't get it, all I did was remove the two ntfs partitions and the Windows install tool marked my ext4 partition as unallocated. How rude of Windows. :mad: Is there any way to recover this ext4 partition? I kept almost all of my data on that partition. I was going to backup later on but did not have a spare drive lying around. I kindly ask for help in getting my ext4 partition back. Any help would be greatly appreciated.

---

### Post by 3Miro on 2011-04-30
This is why you should always make sure to backup your data before you mess with partitions. Also, windows sux.

Here is something that can help get your data:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by oldfred on 2011-04-30
Testdisk will probably find the partition. Windows does not normally see the Linux partitions, and sometimes then just updates partition table without them. Were they logical partitions in an extended?

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Win7 will install to one NTFS partition if created in advance, it is a primary partition and it has the boot flag.

---

### Post by ddr3XD on 2011-04-30
> **3Miro said:**
> This is why you should always make sure to backup your data before you mess with partitions. Also, windows sux.

Here is something that can help get your data:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

OMG!!! IT worked!!! [COLOR=Red]**Thank YOU THANK YOU THANK YOU**!!![/COLOR]
I followed the instructions under "Lost Partition" using Parted. I didnt even have to download anything and all i had to do was enter like three line of code into the terminal. And i got my ext4 partition back.
Thank you so much. And thanks also oldfred for your advice posted. Even though i got it done with Parted maybe someone might find Testdisk useful as well. What a relief. I'm so Happy now. :guitar:

---

### Post by 3Miro on 2011-04-30
Glad it worked. 

If you have no more questions, please mark the thread as "solved".

---

