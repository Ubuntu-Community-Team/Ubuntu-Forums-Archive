---
title: "Low disc space!"
date: 2010-04-11
forum: General Help
---

### Post by gagea on 2010-04-11
I installed ubuntu on external hard drive. I devoted 60 GB of partition to ubuntu. But now I am getting this message after each start up:

"Low Disk Space. This computer has only 199 Mb disk space remaining". How can I solve this problem?

Thanks 

Gagea

---

### Post by StefanSeo on 2010-04-11
Perhaps your HDD is full, you should think to empty it :)

---

### Post by 2hot6ft2 on 2010-04-11
System > Administration > GParted
select the drive in the top right drop down and see if it's really full or if it's the Disk Usage Analyzer that is claiming it is when it's not.

[Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")

---

### Post by gagea on 2010-04-11
> **2hot6ft2 said:**
> System > Administration > GParted
select the drive in the top right drop down and see if it's really full or if it's the Disk Usage Analyzer that is claiming it is when it's not.

[Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")

There is 34.36 GiB free space available on the partition where the ubuntu is installed. But, it still says low disk space.

---

### Post by gagea on 2010-04-11
> **gagea said:**
> There is 34.36 GiB free space available on the partition where the ubuntu is installed. But, it still says low disk space.

Here are screenshots.

---

### Post by alarme on 2010-04-11
Can you post the output of   df -h   ?

---

### Post by gagea on 2010-04-11
> **alarme said:**
> Can you post the output of   df -h   ?


Here it is:

Filesystem            Size  Used Avail Use% Mounted on
aufs                  4.0G  3.1G  659M  83% /
udev                  1.5G  300K  1.5G   1% /dev
/dev/sdb2              40G  4.7G   35G  12% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  1.5G  988K  1.5G   1% /dev/shm
tmpfs                 1.5G   64K  1.5G   1% /tmp
none                  1.5G  128K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1             427G  100M  427G   1% /media/DATA

---

### Post by Slim Odds on 2010-04-11
> **gagea said:**
> Here it is:

Filesystem            Size  Used Avail Use% Mounted on
aufs                  4.0G  3.1G  659M  83% /
udev                  1.5G  300K  1.5G   1% /dev
/dev/sdb2              40G  4.7G   35G  12% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  1.5G  988K  1.5G   1% /dev/shm
tmpfs                 1.5G   64K  1.5G   1% /tmp
none                  1.5G  128K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1             427G  100M  427G   1% /media/DATA

You have a /media/DATA partition that is giant and filled.

You might start my reducing the "reserved" space. Ubuntu defaults to reserving 5% of each ext2/3/4 partition for root only access. This is ridiculous and seems to be an ancient carryover from the olden days. So you're wasting about 21GB of disk space on that partition.

I'd recommend no more than 1% (I change mine to 0% because it's easy to use the Live CD or live flash to repair problems).

For example:
```
sudo tune2fs -m 1 /dev/sdb1
```Check this for more help: [http://www.netadmintools.com/html/8tune2fs.man.html](http://www.netadmintools.com/html/8tune2fs.man.html)

Or: man tune2fs

---

### Post by gagea on 2010-04-11
> **Slim Odds said:**
> You have a /media/DATA partition that is giant and filled.

You might start my reducing the "reserved" space. Ubuntu defaults to reserving 5% of each ext2/3/4 partition for root only access. This is ridiculous and seems to be an ancient carryover from the olden days. So you're wasting about 21GB of disk space on that partition.

I'd recommend no more than 1% (I change mine to 0% because it's easy to use the Live CD or live flash to repair problems).

For example:
```
sudo tune2fs -m 1 /dev/sdb1
```Check this for more help: [http://www.netadmintools.com/html/8tune2fs.man.html](http://www.netadmintools.com/html/8tune2fs.man.html)

Or: man tune2fs

Thanks a lot. I am new to Linux, so can you please explain in plain words so I can improve my computer. Thanks a lot.

---

### Post by 2hot6ft2 on 2010-04-11
> **gagea said:**
> There is 34.36 GiB free space available on the partition where the ubuntu is installed. But, it still says low disk space.
That's because Disk Usage Analyzer looks at /
Which includes everything under it like /media/DATA which is where you're using all the space.
Slim Odds is right.
Had to eat sorry for the delay. I disabled Disk Usage Analyzer because I don't fill things more than 90% anyway.

---

### Post by 2hot6ft2 on 2010-04-11
> **gagea said:**
> Thanks a lot. I am new to Linux, so can you please explain in plain words so I can improve my computer. Thanks a lot.
Slim Odds is telling you to
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo tune2fs -m 1 /dev/sdb1

```
You will have to enter your password which wont be displayed just type it in and hit Enter

---

### Post by gagea on 2010-04-11
> **2hot6ft2 said:**
> That's because Disk Usage Analyzer looks at /
Which includes everything under it like /media/DATA which is where you're using all the space.
Slim Odds is right.
Had to eat sorry for the delay. I disabled Disk Usage Analyzer because I don't fill things more than 90% anyway.

Thanks a lot  and I appologize for asking a lot of questions. I can not understand what Slim Odds means to do as I am new to Linux. What is is solution please?

---

### Post by gagea on 2010-04-11
> **2hot6ft2 said:**
> Slim Odds is telling you to
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo tune2fs -m 1 /dev/sdb1

```You will have to enter your password which wont be displayed just type it in and hit Enter


Thanks. I did run the above command. This is the outs:

sudo tune2fs -m 1 /dev/sdb1
tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

Is it correct situation?

Thanks a lot for your help

---

### Post by 2hot6ft2 on 2010-04-11
> **gagea said:**
> Thanks a lot  and I appologize for asking a lot of questions. I can not understand what Slim Odds means to do as I am new to Linux. What is is solution please?
No need to apologize, we were all new at some time and the only stupid question is the one that's NOT asked.

See my post right above yours while I type out how to stop Disk Usage Analyser from warning you. That is IF you don't want the warnings. If you fill a disk too full you may not be able to access it.

---

### Post by 2hot6ft2 on 2010-04-11
> **gagea said:**
> Thanks. I did run the above command. This is the outs:

sudo tune2fs -m 1 /dev/sdb1
tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

Is it correct situation?

Thanks a lot for your help
Try
```
sudo tune2fs -m 1 /media/DATA
```
But it should have worked the way Slim Odds said

---

### Post by gagea on 2010-04-11
> **2hot6ft2 said:**
> Try
```
sudo tune2fs -m 1 /media/DATA
```


Here you are. This is the result

sudo tune2fs -m 1 /media/DATA
tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Is a directory while trying to open /media/DATA
Couldn't find valid filesystem superblock

---

### Post by 2hot6ft2 on 2010-04-11
Ok, just do it like this
>  Originally Posted by SecretCode
While trying to solve this for myself I came across your post. And this is the solution:

Open gconf-editor (type gconf-editor at the command line), and navigate to the key /apps/gnome_settings_daemon/plugins/housekeeping/.

Double-click the ignore paths name, and remove the paths you want not to ignore any more.

There are some other useful configuration settings here, like free_percent_notify (default 0.05 meaning notify when space is less than 5%) and free_size_gb_no_notify (default 2 meaning don't notify if the free space is more than 2GB).
for the ignore paths you could ADD /dev/sdb1/ to the ignore paths to ignore that drive.

Here's a screenshot of mine. Which means it will ignore ALL drives.

---

### Post by gagea on 2010-04-11
> **2hot6ft2 said:**
> Ok, just do it like this

for the ignore paths you could ADD /dev/sdb1/ to the ignore paths to ignore that drive.


Thanks  a lot. I gone through some of your path and I stop here. The screenshot is uploaded. Hope you can help.

---

### Post by 2hot6ft2 on 2010-04-11
> **gagea said:**
> Thanks  a lot. I gone through some of your path and I stop here. The screenshot is uploaded. Hope you can help.
Just click on Add then add the path you WANT IT TO IGNORE and click Ok.
My data partition has a NTFS filesystem format so it isn't treated the same like Slim Odds was saying.
> **Slim Odds said:**
> 
You might start my reducing the "reserved" space. Ubuntu defaults to reserving 5% of each ext2/3/4 partition for root only access. This is ridiculous and seems to be an ancient carryover from the olden days. So you're wasting about 21GB of disk space on that partition.

I'd recommend no more than 1% (I change mine to 0% because it's easy to use the Live CD or live flash to repair problems).

Might take a look at man tune2fs in a terminal to see how to make the command he gave work right.

---

### Post by 2hot6ft2 on 2010-04-11
Is that DATA partition NTFS by any chance?
Talking about this drive/partition
/dev/sdb1 427G 100M 427G 1% /media/DATA

---

### Post by gagea on 2010-04-11
> **2hot6ft2 said:**
> Ok, just do it like this

for the ignore paths you could ADD /dev/sdb1/ to the ignore paths to ignore that drive.

Here's a screenshot of mine. Which means it will ignore ALL drives.

Thanks a lot. I did the same as you explained above. Here is df -h:

Filesystem            Size  Used Avail Use% Mounted on
aufs                  4.0G  3.6G  235M  94% /
udev                  1.5G  304K  1.5G   1% /dev
/dev/sdb2              40G  4.7G   35G  12% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  1.5G  2.2M  1.5G   1% /dev/shm
tmpfs                 1.5G   44M  1.4G   4% /tmp
none                  1.5G  108K  1.5G   1% /var/run
none                  1.5G  4.0K  1.5G   1% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1             427G  100M  427G   1% /media/DATA
/dev/sda3             7.6G  5.0G  2.7G  65% /media/AAEE7232EE71F743
/dev/sda2             217G  106G  111G  49% /media/S3A6747D002

Hope this solve the problem next time I reboot computer. Thanks agian

---

### Post by 2hot6ft2 on 2010-04-11
If you set it to ignore that partition it shouldn't give the warning.
Is that DATA drive/partition formatted to NTFS?
I think it is and that's why the command wouldn't work.
Because I get the exact same response from mine when I tell it to do it to my NTFS partition.

---

### Post by gagea on 2010-04-11
> **2hot6ft2 said:**
> Is that DATA partition NTFS by any chance?
Talking about this drive/partition
/dev/sdb1 427G 100M 427G 1% /media/DATA


Yes you are right. I originally partitioned 500 GiB external hard drive into 427 GiB NTFS for keeping my data and 40 GiB for installing ubuntu. I can not see the /media/DATA on my computer or desktop. I can only see only the ubuntu drive not DATA one. I am thinking to buy smaller external hard drive for installing ubuntu and keep this 500 GiB for my data. Anyway, thank a lot for your help. Gagea

---

### Post by 2hot6ft2 on 2010-04-11
I should have asked but saw what he was telling you to do and thought he had already found out.
You're welcome. If you need help on anything else just let us know and someone will fix you up.
:guitar:

---

### Post by gagea on 2010-04-11
> **2hot6ft2 said:**
> I should have asked but saw what he was telling you to do and thought he had already found out.
You're welcome. If you need help on anything else just let us know and someone will fix you up.
:guitar:

Thanks a lot for your support and kindness. 

Gagea:)

---

### Post by 2hot6ft2 on 2010-04-11
You're welcome.
And your ubuntu is on the same drive so it considers it an internal drive. That's why it doesn't show up on your desktop as an external drive.

---

### Post by egalvan on 2010-04-11
> **gagea said:**
> 
```
Filesystem     Size  [COLOR="Red"]Used[/COLOR] [COLOR="Blue"] Avail[/COLOR] [COLOR="Lime"]Use%[/COLOR] Mounted on

/dev/sdb1      427G  [COLOR="Red"]100M[/COLOR]  [COLOR="Blue"]427G[/COLOR]   [COLOR="Lime"]1%[/COLOR] **/media/DATA**
```


Can anyone tell me how [COLOR="Red"]100MegaBytes[/COLOR] out of **427,000Megabytes**, which is reported as 1% (**One Percent**) used is considered ``full``?
Or am I seriously missing something here?

Next, in Hardy and Intrepid, anything mounted on /media automatically had an Icon placed on the desktop...
Has this changed in the later versions (Jaunty or Lucid))?

---

### Post by gagea on 2010-04-11
> **egalvan said:**
> Can anyone tell me how [COLOR=Red]100MegaBytes[/COLOR] out of **427,000Megabytes**, which is reported as 1% (**One Percent**) used is considered ``full``?
Or am I seriously missing something here?

Next, in Hardy and Intrepid, anything mounted on /media automatically had an Icon placed on the desktop...
Has this changed in the later versions (Jaunty or Lucid))?


I do not know what is happening. The DATA drive shows itself in the root account. But, when I switch to my personal account, it does not show any desktop or etc icon to reach it.

---

### Post by 2hot6ft2 on 2010-04-11
> **egalvan said:**
> Can anyone tell me how [COLOR="Red"]100MegaBytes[/COLOR] out of **427,000Megabytes**, which is reported as 1% (**One Percent**) used is considered ``full``?
Or am I seriously missing something here?

Next, in Hardy and Intrepid, anything mounted on /media automatically had an Icon placed on the desktop...
Has this changed in the later versions (Jaunty or Lucid))?
Well sheep dip. I didn't even catch that. You're absolutely right.
There are no full partitions there.:confused:

I always disable desktop drive icons first thing so I wouldn't know about the second part.

---

### Post by 2hot6ft2 on 2010-04-11
It's got to be a bug in the Disk Usage Analyzer. I disabled mine a long time ago for the same thing as I stated in the thread I linked to earlier in [post #3]("http://ubuntuforums.org/showpost.php?p=9108638&postcount=3").
> **2hot6ft2 said:**
> System > Administration > GParted
select the drive in the top right drop down and see if it's really full or if it's the Disk Usage Analyzer that is claiming it is when it's not.

[Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")

---

### Post by Slim Odds on 2010-04-11
> **gagea said:**
> I do not know what is happening. The DATA drive shows itself in the root account. But, when I switch to my personal account, it does not show any desktop or etc icon to reach it.

This is how unix file systems work. / is the root of the file system. You can "plant" other file systems into it. They don't have to be within the same partition.

Example:
/media/DATA is an entirely different partition that is mounted into / as /media/DATA

The unix file system is very flexible in this respect. As another example, if you don't create a separate partition for /tmp, it will be on the same partition as /

But, if you later decide to have a separate /tmp partition, you can create it, mount it and it will be use instead of the one on the / partition.

Also, a note to everyone, we should be telling people to use "**df -hT**" instead of "**df -h**", that way is also shows the partition type. Then we would know from the start what we are up against.

---

### Post by 2hot6ft2 on 2010-04-11
> **gagea said:**
> I do not know what is happening. The DATA drive shows itself in the root account. But, when I switch to my personal account, it does not show any desktop or etc icon to reach it.
What do you mean it shows in the root account?
You may have given ownership to root.
If it's NTFS did you enable read/write on it using
System > Administration > NTFS Configuration Tool
if not then you need to.
If you don't have that [click this then Ok to install it]("apt:ntfs-config")

I hate that Disk Usage Analyzer and if it didn't take so many things with it I would have removed it.

---

### Post by Slim Odds on 2010-04-11
> **2hot6ft2 said:**
> What do you mean it shows in the root account?
...

I think that he's confused about / and that everything looks like it's "inside" there.

---

### Post by 2hot6ft2 on 2010-04-11
> **Slim Odds said:**
> I think that he's confused about / and that everything looks like it's "inside" there.
You got that right.
Well he disabled the Disk Usage Analyzer earlier so it shouldn't give any more false alarms.
Still don't believe we missed that 1%.:oops:

---

