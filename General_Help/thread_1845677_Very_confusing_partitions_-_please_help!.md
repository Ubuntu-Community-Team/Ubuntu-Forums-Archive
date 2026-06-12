---
title: "Very confusing partitions - please help!"
date: 2011-09-17
forum: General Help
---

### Post by zozza on 2011-09-17
I am very confused about my partitions and hope someone can clearly explain the situation to me.

This is what System / Disk Utility in 11.04 (using GNOME classic) revealed:

/dev/sda1 - 42GB - NTFS. # This is my Windows XP partition.

/dev/sda2 - 114GB - Container for logical partitions.

Within /dev/sda2 are:

/dev/sda5 - 56GB - ext3. # Ubuntu 11.04.
/dev/sda6 - 10GB - swap space.
/dev/sda7 - 46GB - ext4.
/dev/sda8 - 1.1GB - swap space. 

I don't understand what /dev/sda7 is (considering that /dev/sda5 is my Ubuntu partition).

I also don't understand why I have two swap spaces.

/dev/sda3 - 5.2GB - FAT32.

/dev/sda4 - 50MB - EFI (FAT-12/16/32). # This seems to be something to do with booting on my Eee PC.

I don't know what /dev/sda3 is though presumably it is Windows-related.  Although I don't know how it connects with the NTFS partition. 

df shows:

/dev/sda7             44379920   7029332  35096100  17% /
none                    501744       680    501064   1% /dev
none                    508372       172    508200   1% /dev/shm
none                    508372       120    508252   1% /var/run
none                    508372         0    508372   0% /var/lock
/dev/sda1             40717384   8642620  32074764  22% /media/708411CB841194A6
/dev/sda5             53645820  33284460  17636292  66% /media/e7735c70-d291-4105-9cab-d356ccc6cc82

I am totally perplexed. Why is /dev/sda7 (ext4) mounted on / (which is 17% used) while /dev/sda5 (ext3) is mounted at /media/e7735c70-d291-4105-9cab-d356ccc6cc82?

Also: is there a way to discover whether the ext3 (/dev/sda5) is in data=ordered mode?

[LEFT]Thanks!
[/LEFT]

---

### Post by Quackers on 2011-09-17
sda3 could possibly be a Windows recovery partition.
sda7 and sda8 could be from an unsuccessful Ubuntu install sometime. Did that happen?

---

### Post by zozza on 2011-09-17
You have pointed me in the correct direction thanks.

/sda5 (/media/e7735c70-d291-4105-9cab-d356ccc6cc82) is an Ubuntu partition I used to use but which I thought I lost when my computer crashed two days ago.

/sda6 is /sda5's swap.

/sda7 (mounted on /) is what I am currently using.

/sda8 is presumably sda7's swap.

So: is it possible to merge sda5 (ext3 running 10.04) and sda7 (ext4 running 11.04)?

Or: what would be the best situation?  At the moment I have two Ubuntu operating systems and a load of duplicate programs.

Thanks.

---

### Post by Lisiano on 2011-09-17
First, backup everything you need from sda5, then get a LiveCD and GParted. Delete sda5 and 6, move sda7 to left and leave some space for swap (sda8 ), for example if you have 8gb (Like I do) and hibernate then give somewhere from 6 to 8, if you don't hibernate, anywhere from 1gb to 3gb. Get a cup or 3 of some good coffee or tea. Wait for it to finish. Reboot and enjoy.

EDIT: There might be more ways, for example if you have Acronis you can use it (I would prefer using it since it takes a lot less time to move partitions in my experience)

---

### Post by oldfred on 2011-09-17
If you have the room on your drive you can leave it and use it for a new install. I always do a new install to another partition. Then the bits I may have backed up somewhere I can easily find and copy to my new install. I now have several / partitions and have just started to reuse one of my old ones.

Another use would be to convert it to a separate /home or just to a NTFS partition for shared data. I do not recommend directly writing into your XP partition, mount it as read only to avoid issues. Then use the shared partition as read/write for both XP & Ubuntu. I still have my Firefox & Thunderbird profiles in my shared NTFS partition even though I rarely boot XP anymore.

You may want to delete one swap and merge the other with the adjacent partition. Swap can be 2GB, or twice RAM if RAM is 1GB or less. If you have more than 2GB then you only need swap equal to RAM if you want to hibernate.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by zozza on 2011-09-17
> First, backup everything you need from sda5, then get a LiveCD and  GParted. Delete sda5 and 6, move sda7 to left and leave some space for  swap (sda8 ), for example if you have 8gb (Like I do) and hibernate then  give somewhere from 6 to 8, if you don't hibernate, anywhere from 1gb  to 3gb. Get a cup or 3 of some good coffee or tea. Wait for it to  finish. Reboot and enjoy.

I assume that downloading 11.04 from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) constitutes of a Live CD with GParted (since you have the option of editing the partitions).  Correct?

I don't hibernate so, as you say, 10 GB swap is totally unnecessary. 

Thanks!

---

### Post by Lisiano on 2011-09-17
AFAIK, it has GParted, I might be wrong, if it's not you can easily install it with
```
sudo apt-get install gparted
``` or using Synaptic or using USC.

---

### Post by Lisiano on 2011-09-17
+1 on the /home partition idea. You could also use them as a Data partition between Windows XP and Ubuntu.

---

### Post by Quackers on 2011-09-17
You can do what you suggest or one of the options oldfred suggests. It's up to you :-)

---

### Post by srs5694 on 2011-09-17
Others have given good suggestions; I'd just like to comment on one point....

> **zozza said:**
> /dev/sda4 - 50MB - EFI (FAT-12/16/32). # This seems to be something to do with booting on my Eee PC.

An EFI System Partition (ESP) is a FAT partition that's used by EFI (or its newer variant, UEFI) firmware. Typically, the ESP holds boot loader files, EFI drivers, and other files intended for use by the firmware. ESPs are most common on GUID Partition Table (GPT) disks, since EFI-based computers all support GPT and Windows requires GPT when booting on UEFI-based computers. Although there's an official MBR type code for ESPs (0xEF), they're rare on MBR disks.

Given that you're booting Windows XP, and on an MBR disk, the ESP on your disk is almost certainly empty and serves no purpose. That said, it's possible that ASUS is using it in some non-standard way on the EeePC, so I don't recommend you delete it unless you're desperate for another primary partition (which you haven't said you are), and then only after verifying that it's empty.

I've heard of apparently unused ESPs on MBR disks on netbooks in the past. I don't really know why they're there. My hypothesis is that it's easier for the manufacturers to set up the disks in a certain way so that they can be used in a variety of models, or with possible future upgrades in mind, so that some models get ESPs even if they don't need them.

---

### Post by lensman3 on 2011-09-17
What does  "/etc/mtab" show.  mtab is what the kernel writes as file systems and partitions are mounted and what options the file systems were mounted with.  Also as root do a "fdisk -l /dev/sda", see what the hard partions are ID as. Between these two files and "/dev/fstab" you should be able to sort out the partitions.

---

### Post by Hakunka-Matata on 2011-09-17
> **zozza said:**
> You have pointed me in the correct direction thanks.

/sda5 (/media/e7735c70-d291-4105-9cab-d356ccc6cc82) is an Ubuntu partition I used to use but which I thought I lost when my computer crashed two days ago.

/sda6 is /sda5's swap.

/sda7 (mounted on /) is what I am currently using.

/sda8 is presumably sda7's swap.[INDENT] [B][COLOR=Black]So: is it possible to merge sda5 (ext3 running 10.04) and sda7 (ext4 running 11.04)?
[/COLOR][/B][/INDENT]Or: what would be the best situation?  At the moment I have two Ubuntu operating systems and a load of duplicate programs.

Thanks.
merge?  

What is your goal? clean drive with one OS?, or multiple OSes?

please post output of ```
sudo sfdisk -luS && sudo fdisk -lu
```

---

