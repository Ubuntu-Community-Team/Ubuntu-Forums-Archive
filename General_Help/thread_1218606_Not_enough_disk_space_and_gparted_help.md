---
title: "Not enough disk space and gparted help?"
date: 2009-07-20
forum: General Help
---

### Post by KneoMattrix on 2009-07-20
Hello,

I am brand new to Ubuntu. I just installed it yesterday and have running in a dual boot with Vista. I got it installed no problem, however when I try to run updates I get the message Not enough free disk space. I have read I can increase the size of  partition using gparted. I created a live cd but I am confused how to use it. I have tried taking a screen shot in gparted using my set up and it says it saves it to the /root. However I don't see it in the root folder. I can't even access the /root.

I am needing some help on how to use gparted to increase the partition so I can run the updates. 

Is there anyone that can help me?

---

### Post by michy99 on 2009-07-20
What is the output of these commands in the terminal?  (Applications->Accessories->Terminal)```
sudo fdisk -l
df -h
```A screen shot from Gparted would be really helpful. Try saving it to the Desktop.

---

### Post by merlinus on 2009-07-20
Use vista's disk management tool to shrink its partition after defragging several times.  Then you may be able to extend the ubuntu partition into the freed-up space.

You may wish to post a screenshot of gparted to get more info on exactly how to do this.

---

### Post by drs305 on 2009-07-20
Here are two very good links to partitioning:
[HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

[http://ubuntuforums.org/showthread.php?t=282018]("http://ubuntuforums.org/showthread.php?t=282018")

Here are my basic rules:
1. Backup your important data.
2. If you are going to change the Windows partition, defrag it *at least* once.
3. You may want to change the Windows partition with a Windows partition manager. I have had no problems with gparted, but if you are already comfortable with a Windows partitioner, use it to change the Windows partition.
4. Run gparted from the LiveCD or a SystemRescue CD. You must do this because the Ubuntu system partitions must be unmounted to change them.
5. To access gparted from the LiveCD: System > Administration > Partition Editor.
6. Unmount any swap partitions (linux-swap). Select the swap partition, then from the main gparted menu: Partition > "swapoff".
7. No partitions you are trying to change should be mounted. Mounted partitions have a "keys" symbol in the lower section of gparted.
8. When expanding partitions, the free space must be touching the partition you want to grow. 
8a. *Both* the free space and the partition must be in the same area - both inside the extended partition, or both outside the extended partition. The extended partition has a light blue border. In the simplest terms, there can be no light blue line between the two partitions or free space you are working with.
9. Resizing a large partition can take a long time - more than an hour or longer. The bigger the partition, the longer the time. Don't stop the operation until it completes.

When asking for help, a screenshot is very valuable. To take a screenshot, from the Ubuntu Main Menu: Applications, Accessories, Take Screenshot. The screenshot by default is saved on the user's Desktop. To add it to a post, at the bottom of the post page is a section called "Additional Options". Click on "Manage Attachments", browse to the Desktop and add the screenshot.
Good luck.

---

### Post by KneoMattrix on 2009-07-20
> **michy99 said:**
> What is the output of these commands in the terminal?  (Applications->Accessories->Terminal)```
sudo fdisk -l
df -h
```A screen shot from Gparted would be really helpful. Try saving it to the Desktop.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b24829c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1321    10606592   27  Unknown
/dev/sda2   *        1321       30076   230971576    7  HPFS/NTFS
/dev/sda3           30077       30401     2610562+   5  Extended
/dev/sda5           30077       30379     2433816   83  Linux
/dev/sda6           30380       30401      176683+  82  Linux swap / Solar

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 1.4G     0  1.4G   0% /lib/init/rw
varrun                1.4G  108K  1.4G   1% /var/run
varlock               1.4G     0  1.4G   0% /var/lock
udev                  1.4G  176K  1.4G   1% /dev
tmpfs                 1.4G  504K  1.4G   1% /dev/shm
lrm                   1.4G  2.4M  1.4G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
/dev/sda1              11G  9.3G  861M  92% /media/Recovery
/dev/sda2             221G   45G  177G  21% /media/disk


I am not sure how to save the screenshot in gparted to a different save location. It tells me it saves it to \root when I take the screenshot but I can't even access that folder to look. Can you tell me how to change the save location in gparted?

Thank you

---

### Post by michy99 on 2009-07-20
drs305's post a couple of posts above this one is a good guide to what you need to do. Shrink sda2. Grow sda3, then grow sda5. I would suggest at least 10 Gig.

This screenshot shows where to click to change the save location of a screenshot.

---

### Post by KneoMattrix on 2009-07-20
I finally got a screenshot of gparted to work

[IMG]http://i32.tinypic.com/bbx9z.png[/IMG]

---

### Post by michy99 on 2009-07-20
It usually works best to shrink the Vista partition using the Vista partition manager (or whatever it's called) so do that first and then boot into the Live CD again.

---

### Post by drs305 on 2009-07-20
Follow the steps I posted earlier. I agree with michy99 that shrinking Vista would best be done with a Windows partitioner you are comfortable with, but it is not absolutely necessary.

The order you will do things after you are back in the LiveCd with the partitions unmounted:

1. Shrink sda2, if you didn't do it from within Vista. Highlight it, then Partition, Resize, and drag the right border to the left. Leave at least 7GB of free space. How much more you want to give to Ubuntu is up to you. The more you shrink sda2, the more you can give to Ubuntu. Personally, I'd shrink it by 20GB-30GB since you have lots of space, but that's just me.

2. Highlight the Extended partition in the lower window (sda3). Select Partition, Resize and drag the left edge until it touches the right edge of sda2. You should now have about 8GB of free space minimum between the unallocated space and what is inside sda3. 

3. Select the linux partition (sda5). Partition, Resize and drag the left edge all the way to the left. The Linux partition should now be a minimum of 10GB.

4. I would make the swap 1GB. If you want to do this, in step three move the right edge of the Ubuntu partition to the left until there is about 800KB of free space on the right side.

5. Select the swap partition, and move the left edge to the left up against the Ubuntu partition. That should give it about 1GB total. 

6. Take a look at the sizes. The Ubuntu partition should now be approximately 10GB (minimum) and the swap partition about 1GB.

7. Hit apply. It may take a long time to run. Don't interrupt it.

---

### Post by KneoMattrix on 2009-07-20
I finally got it working. Thank you all for the help. I really appreciate it.

---

### Post by drs305 on 2009-07-20
KneoMattrix,

If you had to repartition things, could you post a shot of your final gparted setup? 

With the number of new users having this problem lately I am considering creating a post specifically for this matter. It would help to have a few good screenshots of the before/after partition scheme.  Thanks.

---

### Post by michy99 on 2009-07-20
> **drs305 said:**
> KneoMattrix,

If you had to repartition things, could you post a shot of your final gparted setup? 

With the number of new users having this problem lately I am considering creating a post specifically for this matter. It would help to have a few good screenshots of the before/after partition scheme.  Thanks.

I have been wondering why this comes up so often. It is always the same size / partition (2.3 Gigs) There is obviously some easily chosen error in the installation procedure that leads to this result.

---

### Post by drs305 on 2009-07-20
> **michy99 said:**
> I have been wondering why this comes up so often. It is always the same size / partition (2.3 Gigs) There is obviously some easily chosen error in the installation procedure that leads to this result.

I would definitely like to know what steps are being taken to cause this result. If it isn't a bug, then something in the installation process is obviously not clear enough for Linux newbies to figure it out.

The errors all result in the same size installation because I am sure that is the general size the Ubuntu installer determines is the minimum size required to install the basic system. I've seen posts of installs varying from 2.1 to 2.3GB, but the partition itself has constantly been 2.3Gb. As soon as the user tries to update or add more packages, the OS fails.

---

### Post by KneoMattrix on 2009-07-21
Sorry, I  missed you post asking for a screenshot of my new gparted. I will do that tonight when I get home.
 
Thank you,
 
KM

---

### Post by KneoMattrix on 2009-07-21
Sorry it took me so long. Here is my latest gparted 

[IMG]http://i31.tinypic.com/9k18c3.png[/IMG]

---

### Post by drs305 on 2009-07-21
> **KneoMattrix said:**
> Sorry it took me so long. Here is my latest gparted 

[IMG]http://i31.tinypic.com/9k18c3.png[/IMG]

Thank you KneoMattrix. I've created a guide to correct situations such as yours since it seems to be happening to others as well. A bit late for you but hopefully others can use it.
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by 3rdalbum on 2009-07-21
> **drs305 said:**
> I would definitely like to know what steps are being taken to cause this result. If it isn't a bug, then something in the installation process is obviously not clear enough for Linux newbies to figure it out.

I installed Ubuntu on a friend's machine, as dual-boot, with him sitting alongside me. The problem is that the bar chart with the resizing handle appears at the bottom of the window, underneath the "Manual" partitioning option, not underneath the "Resize /dev/sda" option. It doesn't look like the bar chart is related to the resizing options.

The installer was changed in 9.04 from its previous layout, and this is what's causing those problems.

---

### Post by drs305 on 2009-07-21
> **3rdalbum said:**
> I installed Ubuntu on a friend's machine, as dual-boot, with him sitting alongside me. The problem is that the bar chart with the resizing handle appears at the bottom of the window, underneath the "Manual" partitioning option, not underneath the "Resize /dev/sda" option. It doesn't look like the bar chart is related to the resizing options.

The installer was changed in 9.04 from its previous layout, and this is what's causing those problems.

Thanks 3rdalbum. I'll take a look in one of my VM's now that I know what to look for and try to get a few screenshots.

Added: I see how new users can mistakenly end up with a 2.5GB Ubuntu partition. I have created a thread describing the problem and providing a snapshot. It is here: [SOLVED: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

---

