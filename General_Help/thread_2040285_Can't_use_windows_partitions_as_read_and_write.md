---
title: "Can't use windows partitions as read and write"
date: 2012-08-10
forum: General Help
---

### Post by Chelidze on 2012-08-10
I wanted to mount windows partitions in ubuntu on start up managed to do this task with using **Storage device Manager** but sadly now i can not use this partitions as read and write

see here what happens when i try to change settings

[Video]("http://youtu.be/S6sYBr1lcDg?hd=1")

thank you for your time

---

### Post by Morbius1 on 2012-08-10
Before you used storage device manager were you able to mount it manually through Nautilus as writeable?

If you were then post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```
[COLOR=Blue]EDIT: Sorry misspelled fstab[/COLOR]

If not then it looks like you have a driver missing:
```
sudo apt-get install ntfs-3g
```

---

### Post by Chelidze on 2012-08-10
> **Morbius1 said:**
> Before you used storage device manager were you able to mount it manually through Nautilus as writeable?

If you were then post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fsatb
```If not then it looks like you have a driver missing:
```
sudo apt-get install ntfs-3g
```

thank you for the reply, I will not lie i do not remember if i could write

```
levan@Saturn:~$ sudo blkid -c /dev/null
[sudo] password for levan: 
/dev/sda1: UUID="A274AD5474AD2BCB" TYPE="ntfs" 
/dev/sda2: UUID="84BAB032BAB0231A" TYPE="ntfs" 
/dev/sda3: UUID="BEEA60D8EA608E89" TYPE="ntfs" 
/dev/sda5: UUID="e3288f78-a96c-4d70-9ba6-e62d5ca68db9" TYPE="swap" 
/dev/sda6: UUID="e7aedb19-a323-4e14-96af-bcd336df8f85" TYPE="ext4" 
/dev/sdb1: UUID="01CCA6ED048CD460" TYPE="ntfs" 
levan@Saturn:~$ cat /etc/fstab
proc                                       /proc        proc  nodev,noexec,nosuid                 0  0  
UUID=e7aedb19-a323-4e14-96af-bcd336df8f85  /            ext4  errors=remount-ro                   0  1  
UUID=e3288f78-a96c-4d70-9ba6-e62d5ca68db9  none         swap  sw                                  0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
levan@Saturn:~$ ^C
levan@Saturn:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
levan@Saturn:~$ 


```

---

### Post by Morbius1 on 2012-08-10
> /dev/sda3 /media/sda3  ntfs  nls=iso8859-1,users,umask=000,user  0  0  Although I wouldn't have written the line that way it should have worked.

Unmount the partition:
```
sudo umount /media/sda3
```And re-mount it this way:
```
sudo mount -a
```Does it give you any error messages?

---

### Post by Chelidze on 2012-08-10
> **Morbius1 said:**
> Although I wouldn't have written the line that way it should have worked.

Unmount the partition:
```
sudo umount /media/sda3
```And re-mount it this way:
```
sudo mount -a
```Does it give you any error messages?

no errors 

```
levan@Saturn:~$ sudo umount /media/sda3
[sudo] password for levan: 
levan@Saturn:~$ sudo mount -a
levan@Saturn:~$ ^C
levan@Saturn:~$ 



```


I have a question why am not i the owner of this partition ??
[IMG]http://i.imgur.com/Txu90.png[/IMG]

---

### Post by Morbius1 on 2012-08-10
Run the following command:
```
mount
```And look for the line that specifies /dev/sda3. Dos it look like this:
> /dev/sda3 on /media/sda3 type fuseblk ([COLOR=Blue]**rw**[/COLOR],nosuid,nodev,allow_other,default_permissions,blksize=4096)The key here is the [COLOR=Blue][B]rw

EDIT: [/B][COLOR=Black]You are not the owner because you didn't specify that you wanted to be the owner. We can fix that - in fact we can fix a few other things as well but we need to see if it's mounting rw and if not why not.[/COLOR][/COLOR]

---

### Post by Chelidze on 2012-08-10
> **Morbius1 said:**
> Run the following command:
```
mount
```
And look for the line that specifies /dev/sda3. Dos it look like this:
The key here is the [COLOR=Blue]**rw**[/COLOR]

```
levan@Saturn:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/levan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=levan)
/dev/sdb1 on /media/01CCA6ED048CD460 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/sda2 type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
[FONT="Comic Sans MS"]**/dev/sda3 on /media/sda3 type fuseblk (ro,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4**096)[/FONT]
levan@Saturn:~$ ^C
levan@Saturn:~$ 

```

it is written ro I am sorry i have no idea what does all of this mean

---

### Post by Morbius1 on 2012-08-10
And yet sda2 which has the exact same options list in fstab is mounting as rw. Wow, I'm at a loss at the moment.

This is a dual boot I assume? Does Windows have a problem with that partition?

---

### Post by Chelidze on 2012-08-10
> **Morbius1 said:**
> And yet sda2 which has the exact same options list in fstab is mounting as rw. Wow, I'm at a loss at the moment.

This is a dual boot I assume? Does Windows have a problem with that partition?

not that i have noticed should i re install ???

and thank you for your effort sorry that you lost time on this 

thank you again

And one more thing now i remember even before i changed any thin in storage mount manager past option was always faded out [IMG]http://i.imgur.com/LHGOu.png[/IMG]
it worked but it looked like it should not 
in the installation process it asked me the permission to download updates and i ticked **yes  ** 
can this be the cause of the problem ??

---

### Post by Morbius1 on 2012-08-10
Long time Linux users hate the reinstall option. Besides it's not clear to me it would result in a different outcome. These sorts of thing tend to be binary - they either work for all ntfs partitions or they don't for any.

If you're thinking of reinstalling try one more thing and see if there's any difference:

Edit /etc/fstab and change this line:
> /dev/sda3 /media/sda3  ntfs  nls=iso8859-1,users,umask=000,user  0  0  To this:
```
UUID=BEEA60D8EA608E89 /media/sda3 ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```Then unmount the partition:
```
sudo umount /media/sda3
```
[COLOR=Blue]EDIT: Sorry that should have been sudo umount /media/sda3[/COLOR]

And re-mount:
```
sudo mount -a
```

---

### Post by Morbius1 on 2012-08-10
Just read your update:
> And one more thing now i remember even before i changed any thin in storage mount manager past option was always faded out  So it was like that from the beginning. Even before you added anything to fstab. I need to think about this one.

Sorry, it's like 2 hours past the time I usually sign off. It's likely that there's something obvious I'm missing here but I just don't see it at the moment.

I'd let this sit for a while and see if 2nd shift can see what I'm missing. If it was like this from the original install a reinstall isn't likely to fix it especially since it's affecting only one of your ntfs partitions.

---

### Post by Chelidze on 2012-08-10
> **Morbius1 said:**
> Long time Linux users hate the reinstall option. Besides it's not clear to me it would result in a different outcome. These sorts of thing tend to be binary - they either work for all ntfs partitions or they don't for any.

If you're thinking of reinstalling try one more thing and see if there's any difference:

Edit /etc/fstab and change this line:
To this:
```
UUID=BEEA60D8EA608E89 /media/sda3 ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```Then unmount the partition:
```
sudo umount /media/sda3
```
[COLOR=Blue]EDIT: Sorry that should have been sudo umount /media/sda3[/COLOR]

And re-mount:
```
sudo mount -a
```

I think you might be right about problems about ntfs partition it might have some problems 
 so what happened to me couple of days ago 
I drooped my external usb HDD and it was mostly not working giving out some errors 

 so i decided before i would throe it away install ubuntu on it and see what would happen 
 booted pc selected cd/dvd selected install ubuntu 12.04 and in installation type selected ,,something else" now i remember here i selected external **usb drive ** after i pressed continue installation started, then i sow that external usb lights where not blinking  so i realized it was not installing on external hdd no it decided to install itself on internal hdd ,, pretty sure it failed and could not install on usb hdd and instead of giving me an error it decided to use internal hdd. so when i noticed this i cut electricity to the pc then i had to rush install windows 7 to some how save some files so i had to buy software that managed to restore some files from formatted HDD thank god Recover My Files managed to recover some of them, so now I think that there is a danger that my ntfs partition is not mounted properly good think i started using online backup 

 so it really might be fault of my ntfs partition who knows

---

### Post by sisco311 on 2012-08-10
I'd check the partition for errors in Windows. You could also use ntfsfix (from the ntfsprogs package) in Ubuntu to fix some common NTFS problems, reset the NTFS journal file and schedule an NTFS consistency check for the first boot into  Windows.

```
sudo umount /dev/sda3
sudo ntfsfix /dev/sda3
```

---

### Post by Chelidze on 2012-08-10
> **sisco311 said:**
> I'd check the partition for errors in Windows. You could also use ntfsfix (from the ntfsprogs package) in Ubuntu to fix some common NTFS problems, reset the NTFS journal file and schedule an NTFS consistency check for the first boot into  Windows.

```
sudo umount /dev/sda3
sudo ntfsfix /dev/sda3
```

checked it no errors 

[IMG]http://i.imgur.com/sVG8k.jpg

```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda3 was processed successfully.
levan@Saturn:~$ 

```

---

### Post by Morbius1 on 2012-08-11
sisco311 knows far more about the internals of this than I do ( luckily for you ) so I have a question:

Do you think it's possible that the partition id and the partition type don't match? Blkid lists the type as ntfs but if you run the following command:
```
sudo fdisk -l
```
[COLOR=Blue]*That's a lower case "L"*[/COLOR] [COLOR=Blue]*at the end*[/COLOR]

Does it show something like this:
> Device    Boot      Start         End      Blocks   Id  System
/dev/sda3          xxxxx xxxxx xxxxx  [COLOR=Blue]**7**[/COLOR]  HPFS/NTFS/exFATOr is the [COLOR=Blue]**7**[/COLOR] another number.
[COLOR=Black]
There&#8217;s a way to fix that using fdisk. I'd have to find the procedure in my notes unless sisco311 knows it from memory.
[/COLOR]

---

### Post by Chelidze on 2012-08-11
> **Morbius1 said:**
> sisco311 knows far more about the internals of this than I do ( luckily for you ) so I have a question:

Do you think it's possible that the partition id and the partition type don't match? Blkid lists the type as ntfs but if you run the following command:
```
sudo fdisk -l
```
[COLOR=Blue]*That's a lower case "L"*[/COLOR] [COLOR=Blue]*at the end*[/COLOR]

Does it show something like this:
Or is the [COLOR=Blue]**7**[/COLOR] another number.
[COLOR=Black]
There&#8217;s a way to fix that using fdisk. I'd have to find the procedure in my notes unless sisco311 knows it from memory.
[/COLOR]

sorry can not understand what you meant by

```
Device Boot Start End Blocks Id System
/dev/sda3 xxxxx xxxxx xxxxx 7 HPFS/NTFS/exFAT
```

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6d9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   174581759    87187456    7  HPFS/NTFS/exFAT
/dev/sda3       174581760   583194623   204306432    7  HPFS/NTFS/exFAT
/dev/sda4       583196670   625141759    20972545    5  Extended
/dev/sda5       621142016   625141759     1999872   82  Linux swap / Solaris
/dev/sda6       583196672   621142015    18972672   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4089 MB, 4089446400 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7987200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9ec5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     7987199     3992576    7  HPFS/NTFS/exFAT
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 7515 MB, 7515537408 bytes
1 heads, 62 sectors/track, 59188 cylinders, total 3669696 sectors
Units = sectors of 1 * 2048 = 2048 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               0  4294967294  4294967294   ff  BBT
Note: sector size is 2048 (not 512)

Disk /dev/sdc1: 7515 MB, 7515537408 bytes
1 heads, 62 sectors/track, 59188 cylinders, total 3669696 sectors
Units = sectors of 1 * 2048 = 2048 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdc1p1               0  4294967294  4294967294   ff  BBT
levan@Saturn:~$ 

```

is there a possibility that ubuntu just installed badly ???
because. If yes it would explain everything I remember i could not install two additional languages it told me some error can not install languages

I think this is a odd case with your permission i will reinstall

---

### Post by Morbius1 on 2012-08-11
The checking the partition id with fdisk was just a hunch on my part because frankly I've run out of ideas.

The problem with the bad install idea is that sda2 is sitting there mounted the exact same way but has no issues at all. It really does sound like somethings wrong with the partition but all indications are that it's fine. 

You could try an experiment - Boot into the Install DVD not to reinstall but to "Try Ubuntu". Then click on the partition in Nautilus to mount it and se if it's writeable. 

If it is then it's something about your install that's affecting one ntfs partition but not another. If it's not writeable then there's something wrong with the disk or something you've done in Windows that's making it read only.

---

### Post by Chelidze on 2012-08-11
> **Morbius1 said:**
> The checking the partition id with fdisk was just a hunch on my part because frankly I've run out of ideas.

The problem with the bad install idea is that sda2 is sitting there mounted the exact same way but has no issues at all. It really does sound like somethings wrong with the partition but all indications are that it's fine. 

You could try an experiment - Boot into the Install DVD not to reinstall but to "Try Ubuntu". Then click on the partition in Nautilus to mount it and se if it's writeable. 

If it is then it's something about your install that's affecting one ntfs partition but not another. If it's not writeable then there's something wrong with the disk or something you've done in Windows that's making it read only.

 i will try live cd :)

---

### Post by sienile on 2012-08-11
I'm an Ubuntu noob myself, but I have mountmanager installed and there are options to mount a drive in read-only mode. You could see about installing mountmanager from the Software Center and see if you can mount it with that and change the read-only setting. It may not work, but it's worth a shot, especially since you seem unfamiliar with the command line.

---

### Post by Chelidze on 2012-08-11
> **Morbius1 said:**
> The checking the partition id with fdisk was just a hunch on my part because frankly I've run out of ideas.

The problem with the bad install idea is that sda2 is sitting there mounted the exact same way but has no issues at all. It really does sound like somethings wrong with the partition but all indications are that it's fine. 

You could try an experiment - Boot into the Install DVD not to reinstall but to "Try Ubuntu". Then click on the partition in Nautilus to mount it and se if it's writeable. 

If it is then it's something about your install that's affecting one ntfs partition but not another. If it's not writeable then there's something wrong with the disk or something you've done in Windows that's making it read only.

read and write works from live cd
but even there past button was faded out, it worked
I will try with ubuntu 10.04 and see how  it looks from there
in ubuntu 10.04 every thing looked and worked perfectly 

> **sienile said:**
> I'm an Ubuntu noob myself, but I have mountmanager installed and there are options to mount a drive in read-only mode. You could see about installing mountmanager from the Software Center and see if you can mount it with that and change the read-only setting. It may not work, but it's worth a shot, especially since you seem unfamiliar with the command line.
thank you for the effort 
but did not work with software i tried
this video shows behavior of ubuntu
[http://www.youtube.com/watch?v=S6sYBr1lcDg&feature=youtu.be&hd=1](http://www.youtube.com/watch?v=S6sYBr1lcDg&feature=youtu.be&hd=1)

---

### Post by Chelidze on 2012-08-13
Re installed ubuntu and now it works

---

