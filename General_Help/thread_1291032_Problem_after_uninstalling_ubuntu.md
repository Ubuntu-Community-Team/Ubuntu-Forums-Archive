---
title: "Problem after uninstalling ubuntu"
date: 2009-10-14
forum: General Help
---

### Post by akssps011 on 2009-10-14
Hello

I upgraded my ubuntu 8.04 to 9.04 with dual boot with windows XP
I removed  ubuntu and when i was formatting windows XP. it showed me 3 unpartitioned space 
1st one was c drive( windows partition)
2nd one was of 836 MB ( which was the size of swap area in ubuntu)
3rd was the ubuntu partition size
What to do to merge them ?

---

### Post by justleen on 2009-10-14
delete the partition, create 1 new one in the unpartitioned space

---

### Post by akssps011 on 2009-10-14
> **justleen said:**
> delete the partition, create 1 new one in the unpartitioned space
How can I delete an unpartitioned space.it doesn't contain anything...the winXP shows three of them as RAW. So how to approach now ?

---

### Post by QIII on 2009-10-14
Are you trying to completely start over with a pure Windows installation on that disk?

---

### Post by uberg on 2009-10-14
There is way to do this from the command line.  However, I am not going to talk about that.  Probably the easiest thing to do would be download PartedMagic ([http://partedmagic.com/](http://partedmagic.com/)) and burn it to a CD.  Boot from this LiveCD and you will have all the tools you need to delete, repartition, and format your hard drive.  It's about 70 meg that you need to download but it is well worth the effort and will you save you some headache.  If you have the time I would even suggest you download Ultilix ([http://ultilex.linux-bg.org/](http://ultilex.linux-bg.org/)) and burn that as a LiveCD because that is just nice to have laying around.  It's about 200 meg but it includes PartedMagic as one of the options and has a multitude of other tools to repair and save your machine.

---

### Post by akssps011 on 2009-10-14
> **QIII said:**
> Are you trying to completely start over with a pure Windows installation on that disk?
yes.. as i have to keep my system dual boot as my family members are not well acqainted with ubuntu and i don't like to use windows. had some other probs.so trying to start afresh.

Thanks a lot  uberg for parted magic thing. But I have heard that parted magic have some negative impact on HDD. Is it true ?
Is there any other option to get out of this problem ?

---

### Post by DeMus on 2009-10-15
Boot from your Windows CD and choose for the installation.
When it comes at the stage where you choose where to install XP you get a list of all available partitions.
You can delete those by pointing at them using the cursor-keys and the key combination D - Enter - L (one after the other)
Do this for all partitions you have.
When done your disk has 1 large unoccupied part choose to create a partition, with a size of let's say 10% of your disk, with a minimum of 5GB. This will be your C-drive.
Create a second partition of 45% of your disk space. This will become the D-drive for data.
Point to the first partition and install Windows on that partition.

Now in Windows you can move My Documents to D, so it is separated from the C: drive.

Now it gets nice: installing Ubuntu.
At step 4 of the installation process choose manual partitioning.
[LIST]
[*]Create a partition for / (root) again about 10% of your disk.
[*]Create a swap partition:
[*]-- 0-1GB ram: size of partition 2GB
[*]-- 1-2GB ram: size of partition 2GB
[*]-- >2GB ram : no swap partition
[/LIST]Create in the rest of your disk a /home partition for your data.

Success.

---

### Post by uberg on 2009-10-15
> **akssps011 said:**
> But I have heard that parted magic have some negative impact on HDD. Is it true ?

That is the first I heard anything negative about PartedMagic.  I actually have Ultilix on several CD's and have used it pretty hard to repair and setup many computers.  I use PartedMagic from this CD to do a lot of setup.  When you are doing some weird parting setups it is easier to partition and format with PartedMagic and THEN go install the various Operating Systems of choice in their pre-partitioned and formatted spots.

---

### Post by akssps011 on 2009-10-15
> **DeMus said:**
> Boot from your Windows CD and choose for the installation.
When it comes at the stage where you choose where to install XP you get a list of all available partitions.
You can delete those by pointing at them using the cursor-keys and the key combination D - Enter - L (one after the other)
Do this for all partitions you have.
When done your disk has 1 large unoccupied part choose to create a partition, with a size of let's say 10% of your disk, with a minimum of 5GB. This will be your C-drive.
Create a second partition of 45% of your disk space. This will become the D-drive for data.
Point to the first partition and install Windows on that partition.

Now in Windows you can move My Documents to D, so it is separated from the C: drive.

Now it gets nice: installing Ubuntu.
At step 4 of the installation process choose manual partitioning.
[LIST]
[*]Create a partition for / (root) again about 10% of your disk.
[*]Create a swap partition:
[*]-- 0-1GB ram: size of partition 2GB
[*]-- 1-2GB ram: size of partition 2GB
[*]-- >2GB ram : no swap partition
[/LIST]
Create in the rest of your disk a /home partition for your data.

Success.
Wel thanx for such an elaborative post
but the problem is that their are 3 different chunks of unpartitioned space which I was not able to do away with windows CD ( see my first post). 
Thankyou uberg...I  am surely going to try partedmagic. 
One more thing..How can I avoid this thing to happen again since I will again install ubuntu on another partition ( not inside windows) ? For installing I just follow the steps given in the documentation, can you suggest what precaution or steps I should follow to prevent this again ?

Secondly, is there any tool through which we can install windows inside ubuntu ?

---

### Post by QIII on 2009-10-15
So, right now you have no working OSs on any partition?

You want do a clean installation of both Windows and Ubuntu in a dual boot configuration?

---

### Post by akssps011 on 2009-10-15
> **QIII said:**
> So, right now you have no working OSs on any partition?

You want do a clean installation of both Windows and Ubuntu in a dual boot configuration?

yes exactly......as a make shift arrangement I have installed windowsXP on one partition and made the res of the unpartitioned spaces as two windows drives .. one is of 836 MB( that is of the sixe of swap area I allocated for ubuntu) and another is 5GB( in which ubuntu was installed) which were shown as separate unpartitioned spaces at the time of installatio.)
I want to clean install both.

---

### Post by akssps011 on 2009-10-15
> **realisticp said:**
> Hi,

I was facing same problem but after got the perfect solutions from here,i solved it successfully.

So,want to replay "Thank You Very Much."

  so  is there any problem with ubuntu or is it something  we are doing wrong ?

---

### Post by Khartaras Vankar on 2009-10-15
1. Installing Windows XP ONLY:

A. Insert your XP CD and boot from it
B. In the XP Install menu delete ALL partitions.
C. Make 1 partition (full HD size)
D. Install on that partition.

2. Installing XP and Ubuntu

A. Insert your XP CD and boot from it
B. In the XP Install menu delete ALL partitions.
C. Make 2 partitions (60% Windows / 40% Ubuntu)
D. Install Windows on the Windows partition.
E. Insert Ubuntu LiveCD
F. Select Install Ubuntu
G. Install on the Ubuntu partition

Good luck! :popcorn:

---

### Post by QIII on 2009-10-15
> **akssps011 said:**
> so  is there any problem with ubuntu or is it something  we are doing wrong ?

The poster has only one bean (how many questions could one possibly have asked and discussed on his first bean?) and has three links to commercial websites in his signature.

I'm not judging, of course ...

---

