---
title: "Good size for an OS partition?"
date: 2011-03-26
forum: General Help
---

### Post by kop4 on 2011-03-26
Just installed ubuntu on my first homebuilt and i loves it!!

I have a 500gb hardrive and I was thinking of making a partition for ubuntu (maybe 10gigs) and leaving the rest for my file storage. Im assuming though that and packages/programs I download will go to the os partition.

Will 10 gigs be enough??


also, looking at disk utility I see that my partitions are this:

/dev/sda1 - 489gb ext4 (<--what does this mean??)
/dev/sda2 - extended 11gb
/dev/sda5 - 11gb swap space

I take it that but taking down the size of sda1 will make another in between sda1 and 2?? I really dont know how this works..


Any help is appreciated


&#1046;aden

---

### Post by Dark_Stang on 2011-03-26
How much RAM are you going to have in this box? Why would you need 11GB of swap space?

For root, 10GB should be enough as long as you don't plan to compile or things on that partition. On the servers that I setup, I usually just use 4-5GB for root. But on my personal machines I like to compile items in /usr/src (and I don't make a separate partition for that) so I just give root 15-20GB.

---

### Post by msandoy on 2011-03-26
> **kop4 said:**
> 

Will 10 gigs be enough??


/dev/sda1 - 489gb ext4 (<--what does this mean??)
/dev/sda2 - extended 11gb
/dev/sda5 - 11gb swap space



Well, /dev/sda1 - 489gb ext4, means that device sda1 (Partition 1 on disk number 1) is 489GB large, and formatted with filesystem ext4 (Its a linux version of the more publicly known NTFS from Microsoft.) So, that is a rather large partition.

/dev/sda2 - extended 11gb, would mean the same thing in MS world. It is a part of the disk that has been prepared to contain multiple partitions.
/dev/sda5 - 11gb swap space, this is a bit overkill. Swap space is the same as Windows swap file. Now, with large amounts of RAM in computers, I personally set swap to the same as the amount of RAM. It is very seldom used at all.

Since you are not mentioning Windows, I believe you will use the whole thing for linux. So I will suggest the following:
While installing, choose manual partitioning.
Remove all partitions on the disk.
create the first partition for swap, 2-4 gb and mark it to be used as swap.
Second, make a primary partition of about 15 GB, format as EXT4 and set mountpoint /.
Third, make an extended partition with the rest of the disk space.
Fourth, Inside the extended partition, make a partition with the desired size, I would use it all. format with EXT4 and set mountpoint /home.

Then you go ahead with the install, and your Home will be on a separate partition, so for future installs of linux, you will not loose any of your saved files. 15GB / (root) partition should cover most normal uses of a desktop computer, and leave space for an upgrade.

---

### Post by foutes on 2011-03-26
Here is how I partitioned my 250gig laptop hd.


1gig partition mounted at       /boot

10 gig partition mounted at    /       

4 gig swap partition   which is double the physical memory for hibernation 

235 gig partition mounted at   /home



I use ext3 because hibernate only works for my laptops with ext3.


Screen shot of disk utility.

---

### Post by newbuntuxx on 2011-03-26
Can you run: 

```
df -kh 
```

And post the output please.

---

### Post by oldfred on 2011-03-26
I have installed a lot of applications and have used about 6GB. You may also use 4GB in /tmp if writing a DVD. I usually make my / about 20 to 25GB if  drive has room. But as others have done you can have smaller roots and they will work.

Are you ever thinking of installing another system or trying Natty or the next version without overwriting your current install. I like to have an extra root or two of 10 or 20GB just for testing.

---

### Post by kop4 on 2011-03-26
> **newbuntuxx said:**
> Can you run: 

```
df -kh 
```And post the output please.


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             121G  3.2G  112G   3% /
none                  491M  268K  491M   1% /dev
none                  496M  356K  496M   1% /dev/shm
none                  496M  104K  496M   1% /var/run
none                  496M     0  496M   0% /var/lock
/dev/sdb1            1006M   32K 1006M   1% /media/7C60-50D9


> Well, /dev/sda1 - 489gb ext4, means that device sda1 (Partition 1 on  disk number 1) is 489GB large, and formatted with filesystem ext4 (Its a  linux version of the more publicly known NTFS from Microsoft.) So, that  is a rather large partition.K thanks, was a little confused


11gb swap space was just the default. Ill take it down a bit.


I guess I should ask that this would just make it easier to update ubuntu if all my important stuff is separate and untouched from the os?

I take it I should set it as /home when I do this too...




&#1046;aden

---

### Post by msandoy on 2011-03-26
> **kop4 said:**
> 
I guess I should ask that this would just make it easier to update ubuntu if all my important stuff is separate and untouched from the os?

I take it I should set it as /home when I do this too...


If you do as suggested by everyone in this thread, and divide your HD into three parts, relatively small swap, 10-20GB for Root, and the rest for home, then you can upgrade ubuntu or even install another distro, without loosing whatever you have in your home partition.

---

### Post by kop4 on 2011-03-26
> **msandoy said:**
> If you do as suggested by everyone in this thread, and divide your HD into three parts, relatively small swap, 10-20GB for Root, and the rest for home, then you can upgrade ubuntu or even install another distro, without loosing whatever you have in your home partition.


Sweet will do. I love how involved this forum is... most forums I would get a response for a few days :)

---

