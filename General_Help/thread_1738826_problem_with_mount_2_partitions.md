---
title: "problem with mount 2 partitions"
date: 2011-04-25
forum: General Help
---

### Post by alaa_rabea2020 on 2011-04-25
[CENTER]when i click palces and mount specific partition ,a message appears
Unable to mount Collection 1
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 1 in /etc/fstab is bad
[mntent]: line 2 in /etc/fstab is bad
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab 

another one when mounting collection 2

Unable to mount Collection 2
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 1 in /etc/fstab is bad
[mntent]: line 2 in /etc/fstab is bad
mount: can't find /dev/sda7 in /etc/fstab or /etc/mtab

this issue happened with 2 partitions collection 1 & collection 2  
and when i boot, i got 

error mounting swap
press s to skip mount swap or press v to manual recovery.
i press s ,,, then
an error occured while mounting collection 1
press s to skip mount collection 1 or press v to manual recovery
i did ,,,, then
an error occured while mounting collection 1
press s to skip mount collection 2 or press v to manual recovery
 i did ,,, finally ubuntu  opened 

and when i write this command "sudo gedit /etc/fstab"
i got this
UUID=5148630128FE30C4 /media/Collection 1 ntfs-3g defaults 0 0
UUID=FE4C11644C1118CB /media/Collection 2 ntfs-3g group,users 0 0
UUID=6e73cf26-edcd-42b0-884c-e2686dd70d15 / ext3 defaults 0 1
UUID= swap swap sw 0 0
UUID=7DF3923D63A29C0E /media/Eng ntfs-3g defaults 0 0
UUID=492905577CF6BDDF /media/Software ntfs-3g defaults 0 0
/dev/sr0 swap udf,iso9660 defaults 0 0

help me plz 
(for notice i am a beginner with ubuntu ) 
[/CENTER]

---

### Post by Morbius1 on 2011-04-25
Change:
> UUID=5148630128FE30C4 /media/Collection 1 ntfs-3g defaults 0 0
UUID=FE4C11644C1118CB /media/Collection 2 ntfs-3g group,users 0 0To this:
```
UUID=5148630128FE30C4 /media/Collection\0401 ntfs-3g defaults 0 0
UUID=FE4C11644C1118CB /media/Collection\0402 ntfs-3g defaults 0 0
```Then run the following command to test for errors and mount the partitions:
```
sudo mount -a
```Linux really hates spaces in things and will not interpret "/media/Collection 1" correctly because of the space before the "1". The 040 is a way to tell linux that this is a space - and it's zero-4-zero.

---

### Post by alaa_rabea2020 on 2011-04-25
i did exactly you told me ,but i got this in terminal
eng-3la2@eng3la2-G31M-ES2C:~$ sudo mount -a
fuse: failed to access mountpoint /media/Collection 1: No such file or directory
fuse: failed to access mountpoint /media/Collection 2: No such file or directory
mount: mount point swap does not exist

---

### Post by Morbius1 on 2011-04-25
It looks like you didn't create the mount point first:
```
sudo mkdir /media/"Collection 1"
sudo mkdir /media/"Collection 2"
```

---

### Post by alaa_rabea2020 on 2011-04-25
thanks [Morbius1]("http://ubuntuforums.org/member.php?u=982144") i dont know what i tell u right now
but there is small problem 
after this command i got this

mount: mount point swap does not exist

but the partitions opened perfectly

---

### Post by Morbius1 on 2011-04-25
This line doesn't look right either:
> UUID= swap swap sw 0 0It should look like this:
```
UUID=some-long-number none swap sw  0 0
```To find "some-long-number" run the following command:
```
sudo blkid -c /dev/null
```You should get something back that looks like this for swap:
> /dev/sdb2: UUID="a6c223bf-f9dc-49a7-9b86-ac8729e95369" TYPE="swap"[COLOR=Blue]In this example[/COLOR] the "some-long-number" is a6c223bf-f9dc-49a7-9b86-ac8729e95369

---

### Post by alaa_rabea2020 on 2011-04-25
after this command "sudo blkid -c /dev/null" ... i got this 

/dev/sda1: UUID="6e73cf26-edcd-42b0-884c-e2686dd70d15" TYPE="ext3" 
/dev/sda3: TYPE="swap" 
/dev/sda5: LABEL="Eng" UUID="7DF3923D63A29C0E" TYPE="ntfs" 
/dev/sda6: LABEL="Collection 1" UUID="5148630128FE30C4" TYPE="ntfs" 
/dev/sda7: LABEL="Collection 2" UUID="FE4C11644C1118CB" TYPE="ntfs" 
/dev/sda8: LABEL="Software" UUID="492905577CF6BDDF" TYPE="ntfs" 

and there is no uuid for swap 
but i made an idea and it works ,,, u can see it [here]("http://ubuntuforums.org/showthread.php?t=1738871")

---

### Post by oldfred on 2011-04-25
With windows I used to use spaces to make some things more readable. With Ubuntu (and all Linux) spaces almost always create problems. Morbius1 gave you the work around to space but it can be a hassle. I found it just easier not to use spaces or change to use underscore.

Not this 
Collection 1
But this
Collection1
or 
Collection_1


When I was sharing folders and still dual booting I went back into windows and stopped using spaces in file names and folders.

---

