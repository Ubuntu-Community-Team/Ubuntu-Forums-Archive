---
title: "how to restore root.disk file ?"
date: 2011-06-08
forum: General Help
---

### Post by ankur.trapasiya on 2011-06-08
Hello i want to recover my data contained in root.disk. How can i do it ? I searched over net but didnt find any satisfactory solution. can anyone please help me out ?

---

### Post by linuxinstalledfromhdd on 2011-06-08
Data Recovery on Wubi...   No idea.. You could try this:

[http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/](http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/)

---

### Post by coffeecat on 2011-06-08
@ankur.trapasiya, what is the situation with root.disk? Is it still there but you cannot boot into your Ubuntu Wubi? Or has it been erased somehow? Or something else? The answer will depend on which.

If the root.disk file is still there but you cannot boot into wubi/Ubuntu then it is possible to mount the file as though it were a partition using the Ubuntu live CD. With that you would then be able to access and copy your files - so long as the filesystem is not extensively damaged.

If you want to try that, post back and I can take you through the procedure. I will be offline for an hour or so, but I will check this thread later.

Do you have an Ubuntu live CD, and if so which version. Which version of Ubuntu were you running in your wubi installation?

---

### Post by ankur.trapasiya on 2011-06-10
hello i am having only root.disk file and i have installed another ubuntu in my computer ... can i recover it from the existing installation or i have to use the live cd option only ? n how to check whether or not my root.disk is corrupted or not ?

---

### Post by coffeecat on 2011-06-10
I'm not sure I follow you completely. Let's see if I understand you. You have a root.disk file but it sounds as though you no longer have a Windows installation? Am I correct? Did you delete all of Windows but managed to preserve the root.disk file? 

If you have a conventional  Ubuntu installation on another partition of the hard drive and can boot into it, and you have access to your root.disk then, yes, the root.disk can be mounted from it to extract files from it and repaired if need be. You wouldn't need to use the live CD.

I think the best thing to tell us about your system is to run the boot script. It's designed for booting problems, but don't worry about that. It will hopefully give us all the information we need in order to know what to do to mount your root.disk.

Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot script according to the instructions there and post the output of the RESULTS.txt file.

---

### Post by Rubi1200 on 2011-06-10
+1 to coffeecat's suggestion to run the boot script. It will really help us to help you.

Thanks.

---

### Post by ankur.trapasiya on 2011-06-10
yes ... i have uninstalled ubuntu from windows but i have taken back up of the root.disk file... can it be restored ?? 

i am attaching result.txt file here....

---

### Post by coffeecat on 2011-06-10
I'll repost your RESULTS.txt file so that other thread contributors can see it.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943919 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   533,387,263   532,975,616   7 NTFS / exFAT / HPFS
/dev/sda3         533,389,312   594,198,527    60,809,216   f W95 Extended (LBA)
/dev/sda5         533,391,360   594,198,527    60,807,168   7 NTFS / exFAT / HPFS
/dev/sda4         594,198,528   625,142,447    30,943,920  12 Compaq diagnostics


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       11166737-af54-4f38-af8b-42615df8c711   ext4       
/dev/sda1        4416D87716D86B84                       ntfs       
/dev/sda2        4E94DA8194DA6B4B                       ntfs       
/dev/sda4        5E2EE2502EE220AF                       ntfs       LENOVO_PART
/dev/sda5        22F62B2EF62B0221                       ntfs       LENOVO
/dev/sdc1        7C146C16146BD226                       ntfs       WELCOME TO HELL

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /win                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/4E94DA8194DA6B4B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/LENOVO            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/WELCOME TO HELL   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdd 


```Where exactly is your "other Ubuntu"? There is no Ubuntu partition on your hard drive. How did you run the boot-script? Do you mean you made another wubi install? Where is the root.disk that you want to recover?

---

### Post by Rubi1200 on 2011-06-10
The questions asked by coffeecat where exactly the ones I wanted to also ask :-)

ankur.trapasiya, if you saved the root.disk to an external medium or even in a folder somewhere on the Windows install then you can download and install a utility that works within Windows to get the data.

Use [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk.

---

### Post by ankur.trapasiya on 2011-06-11
hello .... Thanks a lot... ext2read recovered my corrupted installation .. .

now one more query i am having is ..
 
i am having my entire ubuntu backed up... now can i use this folders in my existing ubuntu ?
what i meant to say is i am already having one wubi installation of ubuntu installed now i also recovered my previous ubuntu installation in which my important installations are residing. can i use this recovered folders( e.g. var,usr,opt etc. system folders) in my new ubuntu ?

in short what i want to ask is will it work if i remove all the new ubuntu installation folders and replace them by my recovered data... will the programs will work which i installed in my previous ubuntu ?  ( e.g. netbeans, mysql )....

---

### Post by Rubi1200 on 2011-06-11
ankur.trapasiya,
I am glad you managed to recover the data you wanted. But, I am confused about your current situation. You say you installed another Wubi but it is not apparent from the results of the script you posted.

Is this new Wubi install on another computer or another drive which wasn't plugged in when you ran the script?

And you also keep switching between talking about Ubuntu and Wubi installs. For the sake of clarity, please tell us whether you have a new install inside Windows (Wubi) or on a separate partition/drive which was installed in the normal way (Ubuntu).

I want to be clear  here; yes Wubi is a Windows installer for Ubuntu, but I am having trouble understanding what you mean and this is partly because the script results do not show either type of install.

---

### Post by ankur.trapasiya on 2011-06-12
hello i have installed another wubi install inside the windows..... now will it work if i replace all the recovered system folders with the currently installed ubuntu ??? e.g. replacing recovered usr,etc, ...... folders with newly installed usr,etc... .

---

### Post by coffeecat on 2011-06-12
I would not advise replacing system folders from an old install. I think I understand that you are trying to recover previously installed applications, but this is not something I would risk trying. The potential for a mis-match between what is in /var, /usr and /etc is simply too great, and by copying everything you simply end up with your old installation, with whatever problems there might have been in it.

If you are trying to save bandwidth by avoiding downloading applications again, have a look in your /var/cache/apt/archives folder in the old root.disk. So long as you hadn't run apt-get clean, all the downloaded .deb packages will still be there. Simply copy them to /var/cache/apt/archives in your new installation. Then, when you install an application in your new system, if the appropriate deb package(s) is/are there, the system won't download again but simply install from the cached package(s).

---

### Post by Rubi1200 on 2011-06-12
ankur.trapasiya,
it would be inadvisable to try and selectively copy files or directories over to a new install.

If you have the original root.disk backed up, you can probably use it on the new machine by installing Wubi and then copying (replacing) that root.disk with the one you previously saved.

This may require some modifications to the grub files, but we can walk you through that if needs be.

However, it is also not a good idea to do this if the root.disk you saved contains configurations for a proprietary graphics  driver that is not present on the new machine where you want to install it.

Of course, if we are talking about the same card, then it should theoretically work I believe.

Let us know if you need more help with this.

(thanks to bcbc for providing the extra information)

---

