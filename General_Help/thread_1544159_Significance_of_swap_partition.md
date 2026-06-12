---
title: "Significance of swap partition"
date: 2010-08-02
forum: General Help
---

### Post by satish_j on 2010-08-02
I need to know the necessity of swap partition in Ubuntu..
I have recently bought a new HD and installed Ubuntu(with NO swap,only Ubuntu on a single partition) on it and am facing frequent,random hanging issues with it..
Earlier,my old HD used an swap partition along with main partition and i never faced hanging issues at that time..
Actually,when in hanging mode,the cpu light keeps blinking continuously and the mouse movement is very slow,the screen also becomes dim.After sometime,it comes out of hanging mode and mouse movement becomes normal.Sometimes,even after waiting for 15-20 minutes,it does not come out of hanging mode and the system has to be restarted.(this is what forced me to look for a possible solution to this)
It is my guess that swap might be the cause of this issue..
Any ideas??

---

### Post by deathadder on 2010-08-02
Hi,

The swap partition only ever gets used when you're running out of physical memory. What happens is the kernel determines that the amount of physical memory free is low, moves some older elements from RAM into the swap partition, then reallocates the memory. 

So presuming you're running out of memory you'll get applications hanging because they can't allocate memory. If this is happening then you'll need to create a swap partition.

---

### Post by satish_j on 2010-08-02
Thanks for your reply..
What i found on searching is that swap is needed in case of small amounts of RAM in the system.If there is no swap and the available RAM is used up,then GNU will try to kill some programs to free up RAM.
On my old HD,i had 712MB of RAM(512+256),but one of them(256MB)got damaged.So,now iam using 512MB of RAM on my new HD.
Can this hanging issue be linked to reduced RAM on my system??

---

### Post by dcstar on 2010-08-02
> **satish_j said:**
> I need to know the necessity of swap partition in Ubuntu..
.........

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by satish_j on 2010-08-06
OK frnds,
I have 850MB of unused space on HD and want to utilize it for a separate swap partition..
Pls help me with the steps to be followed to achieve the same.

---

### Post by pipemartinm on 2010-08-06
You'll need to partition it off and format in swap format. I suggest you use something like the gparted live cd to resize your partitions without losing data. Then mount it in fstab 
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda2          none                  swap      sw                 0            0

```If you're able to it'd probably be easier to just wipe the box and reinstall using the default settings, it'll setup a swap partition for you.

---

### Post by What Rights on 2010-08-06
Oh my gosh, you are running with 512mb of probably slow ram, yes you need a swap.

You can create one with gedit, or just do a fresh install.

The latter of the two is your best option.

---

### Post by satish_j on 2010-08-06
> **pipemartinm said:**
> You'll need to partition it off and format in swap format. I suggest you use something like the gparted live cd to resize your partitions without losing data.
Can you pls be more elaborate??i have the Hardy heron Live CD,but do not have any idea on Gparted thing mentioned by you..
> If you're able to it'd probably be easier to just wipe the box and reinstall using the default settings, it'll setup a swap partition for you.
At time of installation,i tried creating swap on the unused space,but the setup gave me some error(i did not took the screenshot).I remember it was something related to 'partition table not edited'..

---

### Post by Ginsu543 on 2010-08-06
To convert your 850 MB unused space to swap, first format the 850 MB unused space to linux-swap using Gparted (i.e., create a separate swap partition). You need to then add the new swap partition to your system by mounting the swap partition. To do this, you need to identify the UUID for the new swap partition. In Terminal, run:
```
sudo blkid
```Look for the entry with TYPE="swap." You need to save the UUID number. Using gedit, you then need to edit your /etc/fstab file and add the following line to the end of the file:
```
UUID=**insert your UUID number here**  none  swap  sw  0  0
```Save your fstab file and reboot your computer. Your computer should now have recognized and mounted your new swap partition for use.

Just for comparison, this is what my /etc/fstab file looks like:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>  <mount point>  <type>  <options>  <dump>  <pass>
proc  /proc  proc  nodev,noexec,nosuid  0  0
# / was on /dev/sda1 during installation
UUID=d3a34845-4a86-419a-85b0-5df6e2e0ba6d  /  ext4  noatime,errors=remount-ro  0  1
# /home was on /dev/sda2 during installation
UUID=ee7c6f2a-743a-4e3e-b2a2-b26cd60ace15  /home  ext4  defaults,noatime  0  2
# swap was on /dev/sda3 during installation
UUID=e473ee9b-5fe0-4e9d-b070-4ee51ada1424  none  swap  sw  0  0
# mount /tmp in RAM
tmpfs  /tmp  tmpfs  defaults,noatime,mode=1777  0  0
```

---

### Post by HermanAB on 2010-08-06
Simple solution:
Read the 'swapon' man page and set up a swap file.  It is not any slower than a swap partition and in this case much less hassle to set up.

---

### Post by satish_j on 2010-08-06
can i use Ubuntu Live CD to create ONLY swap partition(and NOT re-installing the entire Ubuntu) out of this Unused space..

---

### Post by Grenage on 2010-08-06
Yes, with Gparted.

That said, heed the words of HermanAB, and look at swapon.

---

### Post by satish_j on 2010-08-06
> **Grenage said:**
> Yes, with Gparted.

That said, heed the words of HermanAB, and look at swapon.

what HermanAB suggested was the process to create Swap file(somewhere in root file system),whereas i want to go for swap on a separate partition..

---

### Post by Grenage on 2010-08-06
If I recall correctly, one can use *swapon* to make a swap partition active.

---

### Post by satish_j on 2010-08-06
> **Grenage said:**
> If I recall correctly, one can use *swapon* to make a swap partition active.

Frnd,i think we are getting close now..
I know i can use swapon to ENABLE(AND NOT MAKE)a swap partition..
```

mkswap /dev/**hda4**
swapon /dev/**hda4**

```
In above commands,hda4 is incorrect..
I do not know the name of the partition as it is not parttion(it is unused space).I want to make it a swap partition.After that,i can use above 2 commands to initialize swap..
My question is :How to convert this unused space to an swap partition??

---

### Post by Grenage on 2010-08-06
If you boot using a LiveCD, you can run Gparted.  Gparted will show you the free space, and you can create a new partition in it; then you can set it's 'type' to Swap.

Is that what you're after?

---

### Post by satish_j on 2010-08-06
> **Grenage said:**
> If you boot using a LiveCD, you can run Gparted.  Gparted will show you the free space, and you can create a new partition in it; then you can set it's 'type' to Swap.

Is that what you're after?

Thanks for that..Now,after booting from Live CD,how should i access Gparted??
Also,cant this Gparted be accessed directly from ubuntu without booting into Live CD??

---

### Post by Grenage on 2010-08-06
On the Ubuntu LiveCD, it should be listed under Administration.  You can't do it while logged in normally, because the disc you're running the OS from is the disc you're repartitioning.  There are probably ways around it, but I wouldn't go there!

---

### Post by rawlins02 on 2010-08-06
Here's a good how-to on setting up partitions, including swap, using gparted:

[http://linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/2/](http://linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/2/)

---

### Post by rawlins02 on 2010-08-06
satish:

One tool that can be accessed from installed Ubuntu (ie. not the live CD) is System -> Administration -> Disk Utility.  This is a more limited tool than gparted, since it is running while linux partitions are mounted.  I used this Disk Utility recently to format an external hard drive and a flash drive.

Best bet is gparted from the CD for setting up swap partition.

---

### Post by satish_j on 2010-08-08
Ok,i used gparted from LIve CD to create an new partition,but got the error as shown in attached screenshot:
It shows that i have ran out of max allowed primary partitions(4)..THough the error is self-describing,what i cannot understand is:How come the partition(/dev/sda5) be an primary partition inside the extended partion /dev/sda2..It should be logical partition???
How should i proceed now??

---

### Post by Ginsu543 on 2010-08-08
That seems a bit funky to me as well. Have you tried creating your swap partition as an extended partition? That should get around whatever primary partition limit. Ubuntu doesn't care whether your swap partition is a primary or extended partition.

---

### Post by dcstar on 2010-08-09
> **Ginsu543 said:**
> 
.........
Ubuntu doesn't care whether your swap partition is a primary or extended partition.

Yeah, especially if it is rarely or never used.

---

### Post by satish_j on 2010-08-09
> **Ginsu543 said:**
> That seems a bit funky to me as well. Have you tried creating your swap partition as an extended partition?

I right-clicked on the unallocated space and selected 'New' and the error was popped out..didn't even got the chance to select 'Primary' or 'extended'...
I have confirmed from system monitor that my system is suffering due to the lack of swap..512MB of RAM is rapidly being used out..
I have disabld some sservices,then also,75% of RAM is being used under idle condition..
Also,I do not want to go for the swap space instaed of an separate Swap parrtition..

---

### Post by john newbuntu on 2010-08-09
I think one of the options for you would be to go into Windows ( I presume you have that OS) and then try and shrink /dev/sda5 (D-Drive) by about 1 GB since it has 27 GB of unused space.  This will free up space for you to create a new logical partition called /dev/sda6 within your extended partition using Gparted.
Create this new partition as swap and assign it as swap in fstab as others have pointed.

The other options is time-consuming and might result in data loss.  It involves moving sda4 and sda3 to the right. Then increase your extended partition and finally create swap.  All this to just get 800 MB of space - not worth it.

---

### Post by satish_j on 2010-08-09
what if i go for deleteing the extended partition(/dev/sda2),which will obviously delete the primary partition(/dev/sda5) and then go for creating the extended partition afresh,an logical partition in it(D drive) and an swap partition..
sda1,sda3,sda4 will be unaffected...
Ps:I will obviously take backup of D-drive before proceeding with above..
Any inputs on Above????
Also,i wanted to know of any setting in GParted which can show whether the partition is primary or not???

---

### Post by john newbuntu on 2010-08-09
If you have more time on your hands... sure.  But essentially you are accomplishing the same thing - 2 logicals in an extended.  

Backing up D-drive is always a good idea.  If you are allowed to use your "DO NOT USE" drive (/dev/sda3), it has 40 GB of unused space.  Just create a folder there and copy your D-Drive data (12GB) in there for safekeeping.

---

### Post by satish_j on 2010-08-09
> **john newbuntu said:**
> If you have more time on your hands... sure.  But essentially you are accomplishing the same thing - 2 logicals in an extended.  

Backing up D-drive is always a good idea.  If you are allowed to use your "DO NOT USE" drive (/dev/sda3), it has 40 GB of unused space.  Just create a folder there and copy your D-Drive data (12GB) in there for safekeeping.

Thanks..So,iam proceeding with the idea..I will be using /dev/sda4 for the backup..
BTW,the 'DO NOT USE' drive has been kept reserved for Fedora as i intend to triple boot my system in future..The name,so that my brothers do not use it for storing their files into it...

---

### Post by satish_j on 2010-08-09
Well,I proceeded with deleting the EXtended partition and creating the swap partition on 894MB of unallocated space..The swap partition was created,but now,i cannot use the unallocated 40GB to create an extended partition.
I have,now,4 primary partitions and want to create an extended partition on the remaining space,but GParted gives the same(Primary partitions limit) error on right-clicking and selecting 'New' on the unallocated space..
Screenshot is attached...:(:(

---

### Post by Ginsu543 on 2010-08-09
I don't quite understand how you've set up your system. Are you dual-booting Ubuntu and Windows? What's on your two NTFS partitions? If the data on /dev/sda3 is just data (and not programs), I would do the following:

1) Backup the data on /dev/sda3 to /dev/sda1 temporarily
2) Unmount and delete your swap partition on /dev/sda2
3) Delete the swap partition on /dev/sda3
4) Combine the two unallocated spaces into one NTFS partition (new /dev/sda2)
5) Copy the data you backed up in step 1 back to the newly created data partition
6) Reformat the unallocated space at the end as linux-swap (new /dev/sda4)

This way you'll have a much larger (~80 GB) data partition which can be shared by both Windows and Ubuntu and you'll stay under the four primary partition limit.

---

### Post by john newbuntu on 2010-08-10
satish_j, you should not have created the swap partition /dev/sda2. Unmount and delete it.

What I was talking about in post #27 was to create an "Extended partition" on the 39.06GB of unallocated space just like how you had before.  This way, you will be within the 4 primary partition limit.

Then, within this Extended partition, create 2 logical partitions:
a. An NTFS partition of size, say 37.5GB
b. A swap with the remaining space (>1GB).

Done.

Yeah, I am not sure on why you need this many NTFS partitions.  But of course you have your reasons.

---

### Post by satish_j on 2010-08-10
> **john newbuntu said:**
> satish_j, you should not have created the swap partition /dev/sda2. Unmount and delete it.

What I was talking about in post #27 was to create an "Extended partition" on the 39.06GB of unallocated space just like how you had before.  This way, you will be within the 4 primary partition limit.

Then, within this Extended partition, create 2 logical partitions:
a. An NTFS partition of size, say 37.5GB
b. A swap with the remaining space (>1GB).

Done.

Yeah, I am not sure on why you need this many NTFS partitions.  But of course you have your reasons.
i need to know why my current setting is not working..i have 4 primary partitions now and i want to create an Extended partition on the remaining space..But,the gparted pops the error on selecting 'New' i.e even before the type of partition is selected..
Also,need to know: Does the OS partition type must be Primary???

---

### Post by satish_j on 2010-08-10
our basics were wrong..The limit(4) for primary partitions includes Extended partition.
Meaning: one can have,on a disk:
4 primary partitions 
OR
3 Primary partitions + 1 Extended Partition..
So,i am now considering to delete the newly created swap partition and combining the 2 Unallocated spaces(39GB+894MB)into one and creating an extended partition out of this..
Prob is i dont know how to combine the 2 unallocated spaces??
Any ideas??

---

### Post by john newbuntu on 2010-08-10
> **satish_j said:**
> our basics were wrong..The limit(4) for primary partitions includes Extended partition.
Meaning: one can have,on a disk:
4 primary partitions 
OR
3 Primary partitions + 1 Extended Partition..

which is why i suggested adding a logical partition to an already existing extended partition.

As far as your new strategy of combining the 39GB and 894MB partitions go, it is time consuming and please make a backup of your partitions(or entire disk) before doing this.

One way would essentially involve moving sda3 and sda4 to the left, kinda like a jigsaw puzzle. i.e, drag the left part of /dev/sda3 first till it meshes with /dev/sda1's right.  Then drag the right side of it till the size is about 44GB.  Hit apply. Do a similar thing for /dev/sda4 and then you would have your combined (~40GB) unallocated partition at the end.

After all that, you will need to reinstall grub and change fstab values if it is referenced by UUID.

I don't know if all this is worth the effort to just get 894MB of space.  You might as well give that 894MB to /dev/sda4 and create the extended on the 39GB space.

---

### Post by satish_j on 2010-08-10
> **john newbuntu said:**
> 
I don't know if all this is worth the effort to just get 894MB of space.  You might as well give that 894MB to /dev/sda4 and create the extended on the 39GB space.
And,how should i give/combine that 894MB to /dev/sda4?If i delete the swap partition,it will result in 894MB of unallocated space..
Will i have to delete /dev/sda4 also in order to combine them???

---

### Post by john newbuntu on 2010-08-10
After deleting swap, you just have to resize sda4 - click /dev/sda4, go to partition in menu, then resize/move. In the window that pops up, drag the right arrow all the way to the right.  Click resize and hit apply.  Here's an example:
[URL="http://gparted.sourceforge.net/larry/resize/resizing.htm"]
http://gparted.sourceforge.net/larry/resize/resizing.htm[/URL]

---

### Post by satish_j on 2010-08-11
> **john newbuntu said:**
> After deleting swap, you just have to resize sda4 - click /dev/sda4, go to partition in menu, then resize/move. In the window that pops up, drag the right arrow all the way to the right.  Click resize and hit apply.
That did the trick..Successfully merged the 894MB with sda4 and created an extended partition on remaining unallocated(39GB) space.2 Logical partitions(swap + ntfs)were then created on this extended partition..
So,entire HD is utilized..
Also,enabled swap in fstab and it is now showing in system monitor.What remains to be tested now is to open many applications at a time and see whether the system hangs or not??
Thanks john newbuntu and others for your time...):P):P

---

