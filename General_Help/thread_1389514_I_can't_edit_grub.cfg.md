---
title: "I can't edit grub.cfg?"
date: 2010-01-24
forum: General Help
---

### Post by Linuxman. on 2010-01-24
I'm typing this command in terminal ;
```
sudo -s
my password then ;
gedit /boot/grub/grub.cfg  
```
My windows (system) disk is in /dev/sda5 but when I look grub.cfg file windows system disk is in /dev/sda1. 
When I want to save this file I take an error. 

Could not save the file /boot/grub/grub.cfg.
You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.


**annotation** : error in windows is : missing or corrupt <windows root>\system32\hal.dll.

Best Regards.

---

### Post by Lekensteyn on 2010-01-24
If you want to edit your GRUB options, try startup-manager:
```
suo apt-get install startup-manager
```

---

### Post by mcduck on 2010-01-24
You are not even supposed to be able to edit grub.cfg, that's not the file where Grub2's configurations are made. (Any changes you make to grub.cfg would simply disappear in the next kernel update).

To configure Grub2 you need to edit either /etc/default/grub (for general configurations) or the files in /etc/grub.d/ (to configure the boot options)

(Startup Manager won't help you there, it has very limited support for grub2, pretty much only changing the default boot OS is supported at the monment)

What comes to setting the correct disk for Windows, simply running "sudo update-grub" should do the trick.

---

### Post by 73ckn797 on 2010-01-24
> **Linuxman. said:**
> 

**annotation** : error in windows is : missing or corrupt <windows root>\system32\hal.dll.

Best Regards.

Are you unable to boot into Windows? I assume this due to your comment.

---

### Post by meierfra. on 2010-01-24
> error in windows is : missing or corrupt <windows root>\system32\hal.dll.
Usually the "hal.dll" message is caused by a faulty boot.ini. So this is probably a Windows and not  Grub problem. To get better information, follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt.

---

### Post by 73ckn797 on 2010-01-24
Are you unable to boot into Windows? I assume this due to your comment.

If so then do this:
Boot into the Windows CD and chose recovery. Once at the command Prompt ```
C:\
```
Change directory to the CD folder i386. There you can enter at the command prompt ```
expand hal.dl_ c:\Windows\System32
```

That will copy and replace the corrupted hal.dll with an original "hal.dll.

You should then be able to boot back into Windows.

This procedure works. I had the exact same message on one of my computers recently.

---

### Post by Linuxman. on 2010-01-24
> **73ckn797 said:**
> Are you unable to boot into Windows? I assume this due to your comment.

I'v tried in repair screen fixmbr and fixboot command but commands do not change anything.There are some information about this problem ;
[http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm](http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm)
But it's very trying.I think if I change,way of disk I will be open the system.

---

### Post by Linuxman. on 2010-01-24
> **meierfra. said:**
> Usually the "hal.dll" message is caused by a faulty boot.ini. So this is probably a Windows and not  Grub problem. To get better information, follow these [instruction]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt.

Ok,I will try to fix the problem in Windows.But I'm interesting why my disk is /sd1 in grub.cfg. (/sd5 in Gparted)

---

### Post by meierfra. on 2010-01-24
> Ok,I will try to fix the problem in Windows
If you post the RESULTS.txt, we should be able to help you with that.

> But I'm interesting why my disk is /sd1 in grub.cfg. (/sd5 in Gparted) 
Probably your boot files are on sda1. If  you post the RESULTS.txt, we might be able to tell you exactly.


> expand hal.dl_ c:\Windows\System32

This works if "hal.dll" is actually missing or corrupted. In most case,  "hal.ddl" is just fine, but boot.ini is pointing to the wrong place.

---

### Post by 73ckn797 on 2010-01-24
> **meierfra. said:**
> This works if "hal.dll" is actually missing or corrupted. In most case "hal.ddl" is  just fine, but boot.ini is pointing to the wrong place.

The suggestion I made is what corrected the problem in my case.

---

### Post by meierfra. on 2010-01-24
> The suggestion I made is what corrected the problem in my case.
I don't doubt that.  Of course "hal.dll" can actually get corrupted. And that might actually be the case for Linuxman. Just from what I have seen in the forums, its usually is  caused by a faulty boot.ini.

---

### Post by 73ckn797 on 2010-01-24
> **meierfra. said:**
> I don't doubt that.  Of course "hal.dll" can actually get corrupted. And that might actually be the case for Linuxman. Just from what I have seen in the forums, its usually is  caused by a faulty boot.ini.

Since I have not had that problem does the boot.ini get changed and not point to the Windows directory or incorrect partition? Here is my boot.ini:
```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /PAE
```

---

### Post by meierfra. on 2010-01-24
> multi(0)disk(0)rdisk(0)partition(1)
This works if Windows is the first partition on the first hard drive.

>  does the boot.ini get changed and not point to the Windows directory or incorrect partition?

The "hal.dll" error often happens  after repartitioning or cloning:  Windows place in the partition table has changed, but "boot.ini" stills points to the old location.

Lindeman's Windows is  on logical partition (/dev/sda5). So when Ubuntu was installed it might have been placed in front of Windows in the partition table, causing  boot.ini to point to the wrong place.

---

### Post by 73ckn797 on 2010-01-24
> **meierfra. said:**
> This works if Windows is the first partition on the first hard drive.



The "hal.dll" error often happens  after repartitioning or cloning:  Windows place in the partition table has changed, but "boot.ini" stills points to the old location.

Lindeman's Windows is  on logical partition (/dev/sda5). So when Ubuntu was installed it might have been placed in front of Windows in the partition table, causing  boot.ini to point to the wrong place.
Yes, I see what you mean. I did not think about that aspect of it. Thanks.

---

### Post by Linuxman. on 2010-01-25
I have attached the Result.txt file,you can download it.

---

### Post by Linuxman. on 2010-01-25
up

---

### Post by meierfra. on 2010-01-25
> up 
Please don't bump your thread more than ones every 24 hours.


> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   [COLOR="Red"]/boot.ini /ntldr /NTDETECT.COM[/COLOR]

Your XP  boot files are on /dev/sda1.  So  grub.cfg  also points to /dev/sda1.


> ```
[COLOR="Red"]/dev/sda1  HPFS/NTFS[/COLOR]
[COLOR="Red"]/dev/sda2  HPFS/NTFS[/COLOR]
/dev/sda3  W95 Ext d (LBA)
[COLOR="Red"]/dev/sda4  Linux[/COLOR]
[COLOR="Red"]/dev/sda5  HPFS/NTFS[/COLOR]
/dev/sda6  Linux
/dev/sda7  Linux swap / Solaris

```

Windows counts partitions just as they appear  in the partition table.  But Windows ignores extended partitions. Thus Windows considers XP to be the fourth partition.  So  you need to edit your boot.ini file on /dev/sda1:


```
sudo mount /dev/sda1 /mnt
sudo nano /mnt/boot.ini
```
(use nano, other editors might insert the wrong kind of line breaks)

Change "boot.ini" so that it looks like


```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition([COLOR="Red"]4)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition([COLOR="Red"]4[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

Follow the instruction on the bottom of the screen to save the file ("^" means the "Ctrl" key)

Reboot and you should be able to boot into XP.


If you would like, I can show you how to boot XP directly from /dev/sda5 (rather than from /dev/sda1). Basically you just need to move the boot files from /dev/sda1 to /dev/sda5. But you also need to use testdisk to fix the  boot sector of /dev/sda5)

---

### Post by Linuxman. on 2010-01-25
@meierfra. 

Thank you.I'm writing this message in Windows rightnow.
Problem is resolved.

---

### Post by meierfra. on 2010-01-25
> Problem is resolved.
Great. Have fun with XP, Ubuntu and Pardus.

---

### Post by Linuxman. on 2010-02-02
> **meierfra. said:**
> Great. Have fun with XP, Ubuntu and Pardus.

Pardus performance was slowly.And I have installed the Backtrack.Now,I have same problems.I wrote the new grub but now I can use just Ubuntu not backtrack and windows.Can you show me how can I boot Xp directly and how can I add Backtrack to grub?

---

### Post by meierfra. on 2010-02-02
Could you run the boot info script again and post the RESULTS.txt, so I can have a look at your new setup?

---

### Post by Linuxman. on 2010-02-02
> **meierfra. said:**
> Could you run the boot info script again and post the RESULTS.txt, so I can have a look at your new setup?

Yes.it's in my first message.Look again.

---

### Post by Linuxman. on 2010-02-02
Oh moy god! My 40 gb data disk format is extended.There are so many pictures,films and documents...(!)

---

### Post by Linuxman. on 2010-02-02
I have upload new Result.txt. Now my data disk mounted but when I want to open my windows disk there are this error; 
unable to mount location.
And hal.dll error when I wanna to open Windows.

---

### Post by meierfra. on 2010-02-02
> And hal.dll error when I wanna to open Windows. 

Your Pardus partition was a primary partition and backtrack is logical partition. This shifted the numbers. So edit  boot.ini just as before and change  both "4"'s to "3"'s.


> how can I add Backtrack to grub? 
Grub 2 should be able to detect in automatically. Just run:

```
sudo update-grub
```


> I want to open my windows disk there are this error;
unable to mount location.


How were you trying the open the windows disk?  

The script was able to mount all the partitions.  Try

```

sudo umount /mnt   #just in case /dev/sda1 is still mounted at /mnt
sudo ntfs-3g /dev/sda5 /mnt
```

Does that mount your Windows partition?

---

### Post by Linuxman. on 2010-02-03
Thank you.

---

