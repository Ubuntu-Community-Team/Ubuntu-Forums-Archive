---
title: "undelete a deleted partition"
date: 2012-02-04
forum: General Help
---

### Post by Hadeda on 2012-02-04
I deleted a partition to gain diskspace.

Running the Disk Utility from a live CD/USBstick shows it as free, unallocated space.

a) Grub does not work
b) Murphy's law has it that I need data from the deleted partition  :-(

Can one undelete a deleted partition in Ubuntu?

Other than booting up via live CD I have not used the hard disk. Can someone help please? Thanks.

---

### Post by jerrrys on 2012-02-04
Maybe TestDisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Hadeda on 2012-02-04
Great idea, but I can't get it to work:

After extracting testdisk-6.13.linux26.tar.bz2 there is an executable called testdisk_static which I assume is the program I need. I tried several methods suggested in the forum, ensured cd to the correct directories etc., but I simply cannot get the program to run.

Once extracted, how do you run testdisk_static?

---

### Post by sudodus on 2012-02-04
> **Hadeda said:**
> Great idea, but I can't get it to work:

After extracting testdisk-6.13.linux26.tar.bz2 there is an executable called testdisk_static which I assume is the program I need. I tried several methods suggested in the forum, ensured cd to the correct directories etc., but I simply cannot get the program to run.

Once extracted, how do you run testdisk_static?
I suggest that you download an iso file for a boot CD or USB drive, and run testdisk from there:

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by Hadeda on 2012-02-06
The live CD starts with a bunch of error messages. They scroll too fast for me to read them. In the end I get a terminal prompt but am not skilled enough to give proper instructions. Remember, unable to boot the HDD, I am running a live Ubuntu CD system and the rescue CD is actually a USB stick.

There is a .deb version of testdisk which I eventually managed to install and run.
I thought that I did the right thing and followed instructions, but when re booting, end up where I started:

error: no such partition
grub rescue>

What is the best way forward?



--------------------------------------------------
FYI:
The live USB stick was created from this download:
[http://ubuntu-rescue-remix.org/files/URR/iso/ubuntu-rescue-remix-10-04.iso](http://ubuntu-rescue-remix.org/files/URR/iso/ubuntu-rescue-remix-10-04.iso)

The .deb file is called  testdisk_6.11-1_i386.deb and can be found at
[http://packages.ubuntu.com/lucid/i386/testdisk/download](http://packages.ubuntu.com/lucid/i386/testdisk/download)

---

### Post by Mosome on 2012-02-06
Maybe this link can help as for the grub rescue:

[http://ubuntuforums.org/showthread.php?t=1326788](http://ubuntuforums.org/showthread.php?t=1326788)

---

### Post by jerrrys on 2012-02-06
"[FONT=Verdana]The live CD starts with a bunch of error messages[/FONT]."

Did you checksum; check cd; burn at low speed?

---

### Post by Hadeda on 2012-02-06
Mosome - Thanks, it helped me to get the boot info pasted below, but I still have to undelete the partition somehow.

jerrrys - I created a live USB and not a CD. Anyhow, I got the .deb version of testdisk to work, as explained above.

When running testdisk, frankly, I don't know what I am doing and only guess my next step. Its a new world to me.

I would be very grateful if someone could tell me where I would find specific instructions about  how to UNDELETE a partition when running Ubuntu from a live USB using testdisk.

Thanks.



Below are the first few lines of Results from Boot Info Script  - I am not Ubuntu experienced enough to figure out  what all of that means. I can only guess that sdb1 is my live USB Ubuntu stick. :confused:



============================= Boot Info Summary: ===============================

 => Grub2 ( v1.97-1.98  ) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 8 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22
    Boot sector info:   Syslinux looks at sector 2857434 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the / 
                       directory. According to the info in the boot sector, 
                       sdb1 starts at sector 0. But according to the info 
                       from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

---

### Post by sudodus on 2012-02-07
If it is hard or impossible to undelete the partition, and you need only a few files from the deleted partition, you should try ***photorec***. If the file data are there at all, photorec can recover your data without partition tables and file systems. Browse the internet to find information about photorec. It can be downloaded from the original site

[http://www.cgisecurity.com/](http://www.cgisecurity.com/)

but it might be a good idea to download an ISO file to make a live CD or USB drive with various free rescue tools including photorec.

---

### Post by varunendra on 2012-02-07
> **Hadeda said:**
> Once extracted, how do you run testdisk_static?
What ??

Why do you have to download a .tar file for using testdisk? It is already in the default repositories (universe). If you can connect to internet while running from a live cd/usb, you can simply do (after enabling 'Universe' repository):
```
sudo apt-get update
sudo apt-get install testdisk
``` to install it. Then-
```
sudo testdisk
```to run it within the terminal.

Sorry if I missed some crucial part of your problem that is keeping you from using this simple method.


**_Edit_:**
> **sudodus said:**
> If it is hard or impossible to undelete the  partition, and you need only a few files from the deleted partition, you  should try ***photorec***. In order to use photorec, the OP must first install it, means testdisk (which photorec is just a part of). And if testdisk is installed, it 'should' be a piece of cake to just recover the lost partition (assuming it's not messed up after deletion).


**_Edit2_:**
If you can not connect to internet in a live session, here's the .deb package of testdisk which you can download on another computer, and just double-click from the live session to install it: [http://packages.ubuntu.com/hardy/i386/testdisk/download](http://packages.ubuntu.com/hardy/i386/testdisk/download)

---

### Post by Hadeda on 2012-02-07
I must apologize for not properly outlining the problem I am having right now.

1) I have no problems running testdisk.

2) I am having a problem using it for the purpose of undeleting a partition. 

I am not experienced enough to navigate through testdisk, as most of the time, I don't know what I am looking at let alone how to press the right buttons without goofing things up.

My question is perhaps: 
Does someone know of or have specific (step-by-step)  instructions about how to undelete a deleted partition using testdisk?

Many thanks!

---

### Post by winh8r on 2012-02-07
Try having a look here: 


[http://ubuntuforums.org/showthread.php?t=1917047]("http://ubuntuforums.org/showthread.php?t=1917047")


hope this helps you in some way.

good luck

---

### Post by varunendra on 2012-02-07
> **Hadeda said:**
> My question is perhaps: 
Does someone know of or have specific (step-by-step)  instructions about how to undelete a deleted partition using testdisk?
Here you go: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Hope it helps you getting your partition/data back.

---

### Post by Hadeda on 2012-02-08
Thanks for all your excellent help, folks.

Step-by-step guides are great if the example mirrors one's problem. Mine was totally different as testdisk did not reveal any partitions during the first steps - any of the steps from then onwards were not applicable. 
Screenshots attached for entry * Linux.  The entry for P Linux reported: No file found, filesystem seems damaged.

It is possible that the first trial and error approach goofed things up. Do I have to reformat and do a new install?

Again, many thanks for your generous time spent.

---

### Post by sudodus on 2012-02-08
Don't despair yet, there is still ***photorec*** to recover the files you need. Probably Testdisk has not destroyed anything, at least not the parts of the drive where file data are saved. So before you repartition and/or reformat the drive, try to recover the important files with photorec!

Wait a minute! You can see partitions and the root file system with Testdisk :-) Testdisk can read, and if you let it write the partition table, maybe you'll have it all back without resorting to photorec!

---

### Post by varunendra on 2012-02-08
Hadeda,

First off, do not try to fix the issue unless you are absolutely sure what you are doing! Any wrong attempt may further worsen the condition. This includes any attempts that may "Write" to the MBR or any of the partition tables.

Now,
Please explain in detail which was the partition you deleted (primary or logical, its size, type, etc) The boot info script does not give us any concrete details about the lost partition.

I would suggest to run Gparted from the live usb > list the hard disk in question > take a screenshot > post it back here and add some description of the partition that was lost.

We can then try to match it with any findings of testdisk and accordingly suggest you what to do next. It is always possible to recover the files unless they are overwritten, although it may be difficult (but not impossible) if the partition table got severely damaged. And so far I haven't noticed any activity in your descriptions that suggests any possibility of a 'damage' to the partition info.

There may be many possibilities and the 'gparted screenshot + partition description by you' would help us getting a better understanding of the situation.

And don't worry about our time. We do it because we enjoy it! :)


**_PS_:**
testdisk did reveal partitions. All those 'D' partitions are the deleted ones. We may just have to figure out which is the one that you want back.

---

### Post by Hadeda on 2012-02-10
Thanks to you all!

varunendra:

> >I would suggest to run Gparted from the live usb > list the hard disk in question > take a screenshot > post it back here and add some description of the partition that was lost.Gparted sda 56Gb.png attached.

> > We may just have to figure out which is the one that you want back.Excellent question. Problem is, I am not 100% sure anymore. I think that sda2 ought to be the working partition and have attached GParted sda2 49 Gb.png. But then, the 'unallocated' 2G partition is probably the one 'accidentally' deleted.

sd1 has no data other than the sector information and is probably an old 1st Ubuntu partition.

There is a probability that the unallocated space is the 2nd Ubuntu installation which I reduced to 2 Gb when installing a new installation on sda2. It is the one I accidentally deleted (Disk Utility shows it as "2.1Gb Free". In fact I am reasonably certain that this is the deleted Partition.

To clarify, there ought to be 3 Ubuntu partitions.

I searched for options in GParted:

Partition -> Check     allowed me to "Check and repair filesystem (ext4) on dev/sda1" and "Check and repair filesystem (ext4) on dev/sda2" but not on the other 3 listings.
Naturally I would not press a button without your consent, so here is my question:
 Would this be an easy solution?

p.s.: I am delighted to know that you are having fun. I must admit that it can be quite infectious...  :-)



edit:
I omitted to add the most obvious issue:
When running live USB I CAN mount and see the 4.1Gb partition in Nautilus!
It is just that the homefolder is encrypted and I am not experienced enough to fish through all the other system folders.

The 53 Gb partition cannot be mounted in Nautilus and the following box pops up:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by savanna on 2012-02-10
Rather than downloading testdisk, just install it using apt:

% sudo apt-get install testdisk

Find the binaries:

% dpkg -L testdisk | grep bin

Run each of the binaries with -h or --help

---

### Post by varunendra on 2012-02-11
Sorry but at this point, I'm a bit confused with all the details you have provided so far. So I need you to restate them in a precise, sequential and related manner with the final goal you want to achieve.

Currently the questions in my mind are (please answer all of them, in the sequence they are asked):
> **Hadeda said:**
> a) Grub does not work
b) Murphy's law has it that I need data from the deleted partition  :-(
**Q.1)** Did grub work before the partition deletion?
[B]
Q.2)[/B] Is it some user data that you want to get back or is it just to make the grub boot again (presuming that deleting the partition was the reason why grub doesn't boot anymore).

> **Hadeda said:**
> There is a .deb version of testdisk which I eventually managed to install and run.
I thought that I did the right thing and followed instructions, but when re booting, end up where I started:
error: no such partition
grub rescue>
**Q.3)** Can you remember and tell us what exactly you did (also, how and with which partition) with testdisk in the above attempt?

> **Hadeda said:**
> 
 => Grub2 ( v1.97-1.98  ) is installed in the MBR of /dev/sda ....... core.img is at this location and 
    looks in**[COLOR=Red]partition 8[/COLOR] for /boot/grub**.
[I]..
<snip>[/I]
..
sda1: __________________________________________________________________________
*<snip>*
    Operating System:**  Ubuntu 10.04.3 LTS**
    Boot files:**        /boot/grub/grub.cfg /boot/grub/core.img**
Obviously, grub is looking at a_ non-existent _partition for the boot files, while from the screenshots of testdisk and the above outputs, it seems sda1 contains all necessary files required to boot Ubuntu 10.04 that is installed on it. Based on this info-

**Q.4)** Can you browse sda1 from the Live USB? Is that the "**4.1 GB partition**" you mentioned in the last post? If yes, what tells you it is 4.1 GB when gparted sees no 4.1 GB partition (I doubt a wrong size reporting due to errors in the filesystem or partition table).

Regardless of these errors (if I'm not missing something crucial), I think we can more easily manage to boot this partition by reinstalling grub.

> **Hadeda said:**
> Screenshots attached for entry * Linux.  The entry for P Linux reported: No file found, filesystem seems damaged.
Most definitely it is the 49.25GB partition which although exists, but needs fixing to become usable (or maybe even more screwed, I don't know). So-

**Q.5)** Is that partition an outcome of your initial efforts with testdisk? It may get fixed with the "Check & repair" option of gparted, but as I said, it may also get even more screwed. So I'd say just leave it as it is, at least for now.

> **Hadeda said:**
> 'unallocated' 2G partition is probably the one 'accidentally' deleted. I also think so.

> **Hadeda said:**
> [COLOR=Red]**sd1**[/COLOR] has no data other than the sector information and is probably an old 1st Ubuntu partition. You mean **sda1**, right?

**Q.6)** How can you say it contains no data? Can you browse it from the live cd? I am wondering what has occupied that 3.85GB space on it if there is no data.

> **Hadeda said:**
> When running live USB I CAN mount and see the 4.1Gb partition in Nautilus!
It is just that the homefolder is encrypted and I am not experienced enough to fish through all the other system folders.Well.. I've already asked what tells you it is 4.1GB in size (only the name displayed or have you checked its properties somehow).

**Q.7)** Even though you may not need to, can you browse through other folders freely except for the /home/*<your home>* folder?

> **Hadeda said:**
>  **The 53 Gb partition** cannot be mounted in Nautilus and the following box pops upAgain, you mean 49.25 GB partition, right?:confused:

Lastly, (I may be repeating myself):

**Q.8 )** What kind of data is it that you want to recover? What was its size (approx.)?

With so many installation attempts, I doubt if a running system is all that you want, and the data you are worried about is no user-data at all! If so, that would be the easiest thing to achieve. But if not, and it is really some important user-data, then with appropriate steps and some caution, we can get it back.

My questions may not be very well arranged, but you get the idea. I need a sequential and comprehensive summary of the problem, maybe with some background info that is helpful. I may not get much time until Monday, but there are a few possibilities that it would take no time at all to suggest solutions for.

---

### Post by Hadeda on 2012-02-12
Thanks, Savanna!
I'll try it out.

---

### Post by Hadeda on 2012-02-12
varunendra:

Often, brevity scarifies clarity!

I will answer your questions one by one but wish to clarify a few points which could help you to better help me

1 The different descriptions for the partitions such as 53GB v 49.25GB come from the fact that different programs (testdisk, GParted, Nautilus and Disk Utility) give contradicting reports for the partition sizes.

2 The initial objective was simply to undelete the 'deleted' partition because a) there is a possibility that it contains user data which I forgot to copy and b) the main reason why I installed a third system partition was that the "deleted" partition returned stacks of warnings when running rkhunter and Tiger after continual OCSP server error reports and our inability to log into many reputable https sites such as banks. Because the warnings didn't mean much to me (or anyone else here), and instead of playing a novice Sherlock Holmes, I simply created a new partition and started a brand new system. Although it was not a primary objective, but further research indicates that it might be a good idea to do forensics on the deleted partition in order to find evidence of the cause of the problems we were/are having. Repeat, it is not the primary objective but only a nice bonus, should one be able to get the deleted partition back 'in one piece'.
I have attached a record of the salient parts of the report, simply to show why I decided to ditch a system with 132 suspect files!

3 Reading your questions, yes, it appears that the prime problem right now is the inability to boot the system through grub.

Here are my specific answers to your questions:

> Q.1) Did grub work before the partition deletion?Yes

> Q.2) Is it some user data that you want to get back or is it just to make the grub boot again (presuming that deleting the partition was the reason why grub doesn't boot anymore).If the restoration would make grub work again, yes. Otherwise see my above reasoning.

> Q.3) Can you remember and tell us what exactly you did (also, how and with which partition) with testdisk in the above attempt?The simple answer is, no and frankly, that frustrates me no end because I thought that I was following the step-by-step guide. As explained earlier, my situation did not match the example in the step-by-step guide.

> Q.4) Can you browse sda1 from the Live USB? Is that the "4.1 GB partition" you mentioned in the last post? If yes, what tells you it is 4.1 GB when gparted sees no 4.1 GB partition (I doubt a wrong size reporting due to errors in the filesystem or partition table).Simple answer: Yes. Nautilus calls it a 4.1GB partition with 1.1GB free space. Yours is a good question, but the fact is that nautilus sees it and I do not have a clue why GParted does not. Remember, Disk Utility sees

a)  2.1Gb free on dev/sda
b)  53Gb ext4 on dev/sda2 not mounted
c)  924Mb free on dev/sda
d)  4.1Gb ext4 on dev/sda1 with mountpoint   /media/[string of alpha-numerics]

I do not know how and why the latter is mounted as I am running live USB on dev/sdb1 mounted at /cdrom    [ ??  I do not have a CDROM on this machine]

> 
Q.5) Is that partition an outcome of your initial efforts with testdisk? It may get fixed with the "Check & repair" option of gparted, but as I said, it may also get even more screwed. So I'd say just leave it as it is, at least for now.Perhaps we should leave it alone as I am unable to confidently and affirmatively answer that question.

> Q.6) How can you say it contains no data? Can you browse it from the live cd? I am wondering what has occupied that 3.85GB space on it if there is no data.
I used the wrong word! I meant that Gparted does not 'see' any data. Thanks for pointing it out.

> Q.7) Even though you may not need to, can you browse through other folders freely except for the /home/<your home> folder?Short answer: yes, except for crosses on some (protected?) folders which tell me that the folders are empty. I can freely open the boot/grub folder, but again, the contents do not mean anything to me. If it is important, let me know.

> Q.8 ) What kind of data is it that you want to recover? What was its size (approx.)?See above. The user data is/are relatively small gedit or LibreOffice text file(s). The bonus would be the 132 'infected' system files!
> 
My questions may not be able very well arrangedThey are perfectly logical and sequential. I hope that I gave you sufficient background regarding the ultimate objective(s) and priorities and provided sufficient information surrounding the technical problem. If there is anything else you need, please let me know!
Thanks!

---

### Post by sudodus on 2012-02-13
You guys are doing things above my level. I am reading and learning...

Anyway, good luck :-)

---

### Post by varunendra on 2012-02-13
Hi,

I haven't ever used Tiger or RKHunter, nor do I have any idea  how they work. But the warnings in the attached file seem normal to me.  You should have checked the /var/log/rkhunter.log file for details as  it suggests.

Also, the OCSP, if I'm understanding correctly, may  give errors due to several non-serious reasons, the most common being a  wrong system date on your computer.

Anyway, for now I was just  about to suggest you how to restore grub to get the existing 10.04.3  running, (and concentrate on partition recovery later) but then this  raised another doubt:> **Hadeda said:**
> Remember, Disk Utility sees
a)  [COLOR=Red]**2.1Gb free on dev/sda**[/COLOR]
b)  53Gb ext4 on dev/sda2 not mounted
c) [COLOR=Red]** 924Mb free on dev/sda**[/COLOR]
d)  4.1Gb ext4 on dev/sda1 with mountpoint   /media/[string of alpha-numerics]

I do not know how and why the latter is mounted as I am running live USB  on dev/sdb1 mounted at /cdrom    [ ??  I do not have a CDROM on this  machine]
I believe the highlighted part is just a typo, and  one or more of the entries might be related with sdb, since any one  application can't report two different values for free space on a single  drive.

Also, the usb getting mounted as a 'cdrom' is normal and  an intentional scheme of a live filesystem, since it is meant to behave  like a live cd when you boot from it. But its involvement, coupled with  your doubts, may cause confusion here. Thus I think the first thing we  need is to eliminate the involvement of the USB or any other drives (the  sdc in post #8 for example..) by getting your installed system running.

Accordingly, assuming your live usb is a persistent installation, please install [boot repair]("https://help.ubuntu.com/community/Boot-Repair")  program on it. We will be using it later to fix the booting issue. For  now, just use its "Create BootInfo summary" button to recreate the  report as in post #8, then post its full contents this time (it doesn't  contain any sensitive info, concerning a security issue).

Along with that, please also post the output of:
```
df -h
```

Please wrap all the pasted outputs in  'code tags' by clicking on **#** at the top of the edit box (in which you  create new posts) to generate those tags, then copy-paste the contents  of the generated report in-between those tags. This preserves the formatting, makes the post look tidy and easy-to-read.

I think that is enough for now. Any more suggestions would be appropriate only after getting full boot info summary.

---

### Post by Hadeda on 2012-02-13
Hi varunendra,

1) When done, Bootinfo copied the output to terminal. Problem is that Edit -> select all -> Copy does NOT copy the whole file which I only found out when trying to post it here - it only contained the first page. Although user settings for "Live Session User" (that's me) confirm that I am "administrator" I cannot open /root folder which apparently contains a copy of the file; I have to re do it again tomorrow.

[COLOR=Red]IMPORTANT EDIT UPDATE[/COLOR]: Have re-run BootInfo. The results are at [http://paste.ubuntu.com/841220/](http://paste.ubuntu.com/841220/)

2) >  believe the highlighted part is just a typoI can confirm that there is no typo! If you want to I could post the screenshot here, but it will tell you the same info.

3) Here are the results of df -h

```
Filesystem            Size  Used Avail Use% Mounted on
aufs                  245M  156M   90M  64% /
none                  240M  288K  240M   1% /dev
/dev/sdb1             3.8G  702M  3.1G  19% /cdrom
/dev/loop0            661M  661M     0 100% /rofs
none                  245M  116K  245M   1% /dev/shm
tmpfs                 245M  600K  245M   1% /tmp
none                  245M   84K  245M   1% /var/run
none                  245M     0  245M   0% /var/lock
none                  245M     0  245M   0% /lib/init/rw
```Thanks for your diligence!

---

### Post by Hadeda on 2012-02-13
sudodus:

Hang in there! 

:D

---

### Post by varunendra on 2012-02-14
It seems you have already tried to fix grub so it points to the correct partition now:
> looks in partition 1 for /boot/grubBut I still see at least two issues:

[LIST=1]
[*]The size occupied on sda1 is too small for a proper Ubuntu 10.04 installation. Did you keep /home on a separate partition during installation?
[*]The partition sda1 does not seem to have the very important /etc/fstab file. Can you manually browse to /etc folder in sda1 and see if it is there? If it is, please post its contents, so we can see what should be where to make it boot (if possible).
[/LIST]
If the **fstab** file is missing and/or the **/home** was on a different partition, then I'm afraid the apparently 'workable' 10.04 installation on sda1 is almost 'doomed', and as such, we should rather focus on getting your lost partition/files back, then clean up the entire drive and do a fresh partitioning/installation.


Actually I feel a bit stupid for not thinking of the 'occupied space' thing on sda1 before, and hoping we could easily make it boot again. But I'm still hopeful about the files, and am enjoying the thread. I just wish I could be able to speed it up a bit.




**_PS_:**
If required, you can open nautilus as root to get into the 'protected' folders (those with a cross on them):
```
gksu nautilus
```
This would allow you to freely access the entire filesystem (unless a folder is really corrupt). **But be informed** - any file/folder you copy or modify in this mode, will become owned by 'root' and thus won't be accessible in normal mode. (although you can modify their ownership/permissions again to change them back to normal).

---

### Post by Hadeda on 2012-02-15
Having read your post twice made me pause and take a deep breath:

To recap, I created the second partition because the first one didn't boot. I created the 3rd installation because of many rkhunter warnings about 132 system files. I am surprised that you do not find anything wrong with the warnings. I can't boot now after the "second" partition was deleted to gain space for a 4th installation - and am running a live USB right now.

Is it possible that the weird profile you are seeing has something to with one or all of this:

1) Everytime during bootup, the machine in question came up with an error message that it could not find something (I think that it was /temp and also about encrypt or so), &quot;press F to fix the problem&quot; and it did. It happened after every installation. The disk itself is healthy (disk utility). Because I got so used to the issue it slipped my mind.
In addition, I am increasingly concerned that I did not always have full custody and control over the machine. I do not have a clue as to why fstab is missing.

2) I foundstrange files with weird filenames and sizes on a USB stick  which might give someone like yourself a further clue. (Screenshot posted).

3) When trying to use gksu nautilus another strange message popped up. (screenshot posted).

4) When trying to mount different USB stick I got another weird error message which doesn't mean anything to me but hopefully to you. Does it have something to do with the filestructure problems I am always having? (screenshot posted).

Your enthusiasm and professional dedication to get to the root of this is a real honor.

---

### Post by varunendra on 2012-02-16
This is indeed getting weird. And I don't think I deserve any such complements you are bestowing on me, since we have got nowhere so far.

**1st screenshot (unable to mount 8GB-1 error):** Is that 8GB usb stick formatted as NTFS? How did you format it? Does it work on other computers without problems?

**2nd screenshot (Could not display "Computer:///"):** That error is **normal **when you open nautilus as root and click on 'Computer' icon (because that is not a 'real' location, it is just a presentation of places to a normal 'user' for ease of use, while 'root' is supposed to access them in traditional way). To browse a drive in this mode, you'll have to either mount it manually, or in advance in normal mode.
[B]
3rd screenshot (weird filenames/sizes): [/B]Which USB stick is that? Is it the one from which you are booting, or the one with the first error message (mounting problem), or yet another one? These kind of filenames or sizes are usually symptoms of a corrupt filesystem or a corrupt/failing drive (unless it is some weird kind of 'encryption' method used by some application). Most often it can be corrected by formatting (while of course losing the data on it), but if even formatting fails, then it most certainly is an indicator of a dying stick/memory card.

If these are three different usb sticks, and work well on other computers, then it raises questions about the consistency of the current one's hardware.

A few years ago I experienced similar file corruptions (corrupt winrar archives) which turned out to be caused by a leaked memory module (RAM). Very recently I experienced another similar issue with a defective CPU core. This time, I was experimenting with an 'unlocked core' of a phenom-II-555-BE processor (the core was locked by default). While that 'unlocked' core appeared to be working fine, almost all of the files (re-encoded videos, 7-zip archives) created during its usage got corrupted. Interesting thing in both these cases (with the RAM earlier, and CPU this time) was that the OS or applications did not report any errors during file creation, but when I tried to open them later, they were corrupt (CRC fail, or so..).

So if all these different USB sticks are getting corrupted, files are mysteriously missing, OS installations are failing,... in short, all sort of hell is breaking loose, then I doubt if it is thanks to a defective RAM (most probable) or a defective CPU (extremely rare, unless you are 'experimenting' with locked cores like I did), or some other I/O error (which I've no idea about).

A few things you may check:

[LIST=1]
[*]Run memtest from live USB to check consistency of RAM (24+ hours is recommended, but at least 2-4 hours should do).
[*]Check the live usb itself for integrity. Press any key when you see the purple screen while booting to bring up the advance boot menu of the live USB. Both "Test memory" and "check disk for defects" options are there.
[/LIST]
I think the best way now is to just try getting those files (and partition) back if possible, then wipe the drive completely and start a fresh installation to see how it goes. But to proceed with anything on the current system, you should first confirm at least the RAM is not defective.

At the moment, I see only two options with the partition problem:

[LIST=1]
[*]Attempt repairing the 49GB partition from gparted, hoping we get something useful on it.
[*]Retry photorec on 'each' partition listed as 'D' (deleted) to see if any lists your desired files. (don't 'Write' the partition structure to MBR yet). If any files ever existed on that 'unused' space, photorec 'should' find it since it doesn't depend on partition table for detecting files (it does a physical byte-by-byte search for any data that appears as file)
[/LIST]
**_PS_:**
Oh, and I meant those 132 warnings 'could' be normal, not that they 'are' normal. The reason for those warnings could be as simple as improper access permissions, or could be as serious as corrupt/absent files (!). We could be sure only after reading their detailed logs as the attached file suggests.

---

### Post by Hadeda on 2012-02-16
varunendra

First, answers to your questions:

> Is that 8GB usb stick formatted as NTFS?Yes

> How did you format it?Ubuntu disk utility

> Does it work on other computers without problems?yes and No: 
It gave the same RAID error on another Ubuntu system. 
On a windows XP system one could read the files but it also had problems backing the stick up onto disk.
Ironically, after using it on the windows machine the problem disappeared. 

> when you open nautilus as root.That is interesting! I never ran nautilus as a root before but saw that error ("Computer:///") many times before on all 2 Ubuntu machines.

> Which USB stick is that?It is different. As I am slowly becoming an expert in frequently installing basic Ubuntu (live USB included) I have a stick for post installation user settings. It is non-bootable and contains data only such as Firefox bookmarks.

> If these are three different usb sticksThey are.

> unless you are 'experimenting' with locked coresI am not.

> improper access permissionsIncreasingly, this access/permission stuff concerns me. What does this mean in this context?

> Run memtest from live USBI do not see an option under 'system'. Terminal doesn't like that command either. How do I run it from within the live USB (ramdisk) system? 

On live USB bootup:
a) "check disk for defects"
```
No errors found
```b) "Test memory"
```
Error: "Cannot load ramdisk with an old kernal image"
```

[COLOR=Navy]**There might be a lateral solution:**[/COLOR]

When reloading live USB, the system (accidentally) reverted back to booting from HDD instead of live USB. This was the message:

```
General error mounting file systems. A maintenance shell will now be started. Ctrl-D will terminate this shell and reboot.
root@computername:~#_
```I do not know which partition this is because I used the same username for the different installations. (not a good idea to do that in the future!)
Q: Is there something you want me to type after the flashing cursor, seeing we are in maintenace mode in a non-ramdisk based system?

If not, I will then attempt repairing the 49GB partition from gparted and run photorec on each "D".

I must admit that things are getting more intriguing, making me more determined - with your help :-)

:-k

---

### Post by varunendra on 2012-02-17
A USB flash drive is always expected to have FAT/FAT32 filesystem on it,  and it does not make much sense to format it as NTFS. I don't know how  exactly a filesystem on a USB flash drive is read/written to, but there  are definitely some extra layers involved compared to a traditional hard  disk. I can't tell how this can lead to system confusion/data  corruption, but it is quite often found that a system (especially  regarding booting and/or mounting) behaves differently when you use  different formatting-tools/filesystems on a flash disk. So it is best to  stick with the obvious (fat/fat32), and that too is sometimes required  to be done from a windows OS (evident from some live usb creation  operations in past).

The "Computer:///" error is abnormal if you  get it often even in normal mode. I'd also like to mention that even in  root mode, it is just "Computer", without ":///" in the error IIRC,  although can't say it matters much.

The memtest was actually the  same "Test memory" option in the live boot menu (or memtest.. in grub  menu), so it is not something you can run 'after' an OS is loaded. The  error you are getting may be related to this:  [http://ubuntuforums.org/showpost.php?p=7909226&postcount=16](http://ubuntuforums.org/showpost.php?p=7909226&postcount=16) , which  suggests it might be due to using a third party or modified syslinux  image. By the way, I always create my live USBs using ubuntu's inbuilt  "Startup Disk Creator", and they have never failed me (yes I can also  run memtest just fine from them). I usually boot a VM from a downloaded  iso > connect the (preformatted fat32) usb to it > run inbuilt  "Startup Disk Creator" > let it use the same iso on which the VM is  running.

The access permission in our context means that rkhunter  might not have the type of permissions it needed to properly scan the  files (again, just one of many possibilities). But for just scanning,  any program should required only 'read' permission on the files which  are generally 'On' by default on the files it complained about. So I  wonder if the warnings were due to corrupt or missing files. But there  is another interesting permission (although that is 'on' by default  too). It is 'Execute' permission on the housing directory, which enables  the 'listing' of files it holds. It is but obvious that you can't scan a  file if you can't even list it! Whatever be the cause, if it was  permission related, then unless rkhunter needed 'more than just read  permissions', it was/is abnormal.

Lastly, I'm quite sure the  booting error about "mounting filesystems" must have happened due to the  absence of the /etc/fstab file. Although we can manually create one, as  well as creating a new user in /home to boot into, it doesn't seem to  make much sense now. However, to ensure what partition it has booted  from, you can use following two commands (and post their outputs here  also, so we can see too):
```
fdisk -l
mount
```
The first  would show all currently detected drives/partitions, and the second  will show what is mounted where (and you are booted from the partition  which is mounted as '/')

Although we can try some more stuff in  the maintenance mode to try to repair the system, but as I said above,  firstly there's no point resurrecting it unless it holds something  important that we can't get from the live environment, and secondly it  may reveal further problems pertaining to a corrupt filesystem - making  it unworthy of all those repair attempts.

However, it would be  interesting to see how and where it is booted from (revealed from above  two commands). Although I'm quite sure it is sda1 alone.


> **Hadeda said:**
> If  not, I will then attempt repairing the 49GB partition from gparted and  run photorec on each "D".
^ That is the only thing I can think of at this point. So go ahead. We  may even need to recover a partition by guess, the retry  testdisk/photorec on it to get files back. The only doubt I have is  (seeing the size of that 'unoccupied space' and the number of deleted  'swaps')- what if that 'unused space' turns out to be one of the swap  partitions that have been deleted. So after photorec's initial failure  to list any files, it's just your 'confidence' about it being the  'deleted' partition in question that I am trusting.

---

### Post by Hadeda on 2012-02-17
> due to the absence of the /etc/fstab file
Based on other feedback from you, it is my guess, that this is probably the very first installation which suddenly did not boot. If it is only due to fstab it might be interesting to get it back although it is possible that all data was backed up; but I don't know for sure.

> it would be interesting to see how and where it is booted from
Here it is:  [http://paste.ubuntu.com/846553/](http://paste.ubuntu.com/846553/)

If it tells you anything of importance please let me know as I have to hang on for a few days before I have an undivided opportunity to run photorec.

---

### Post by varunendra on 2012-02-17
> **Hadeda said:**
> Here it is:  [http://paste.ubuntu.com/846553/](http://paste.ubuntu.com/846553/)
Sorry, I should've been more clear. It was a suggestion regarding your last question in your last post: > Is there something you want me to type after the flashing cursor - means, you had to type in those commands when you were booted from HDD with 'root' prompt (where you wouldn't have to add 'sudo').

The current outputs are from live session, which obviously reports the live filesystem mounted as root (/). Although it's almost obvious that it booted from sda1, I just want to see those outputs as confirmation.

As for creating fstab, it would be better if we use UUIDs in it instead of addresses of 'sd*xy'* form. UUIDs can be obtained from the command:
```
sudo blkid
```
or just *blkid* if you run it from the root prompt.

Afterwards we'd also need to add a user to log onto (unless you want to login as 'root' :)). And after that...... we'd have to Cross Our Fingers hoping it boots as expected ;).

---

### Post by Hadeda on 2012-02-20
> ...which obviously reports the live filesystemI feel a bit dumb here. Well, I have learned something :rolleyes:
 Have repeated the test by booting from the HDD:

1) Results of fdisk -l

```
Device Boot    Start    End    Blocks        ID    System
/dev/sda1      1       503       4034228       83       linux
Partition 1 does not end on cylinder boundary.
/dev/sda2      755      7183      51639296    83       linux
```2) Results of mount: see screenshot "mount" (I have redacted info which could be private). 
a) There is reference to ecryptfs (without an 'n') which I don't understand. I remember playing with eNcryption after learning that the machine was not always under my custody and control...
b) A warning told me to check the 'mounts' file (with an 's') which I did and I hope that it reveals data necessary for you to help me.

3) Through blkid I have obtained the UUIDs for sda1, sda2 and sdb1 (live USB).

4) I have also recovered 2 user names, unless it is necessary to create a new one. I am happy to log in as root.

Am I on the right track to recreate fstab in order to boot into my first installation? ;)

---

### Post by varunendra on 2012-02-28
Sorry for such a late response, I got extra busy in my office work.

Anyway, looking at the screenshot, and considering the problems in accessing the home directory, it is almost certainly an encryption issue. Just for reference, please see these:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
and
[http://www.ubuntugeek.com/recover-your-encrypted-private-directory-using-ecryptfs-recover-private.html](http://www.ubuntugeek.com/recover-your-encrypted-private-directory-using-ecryptfs-recover-private.html)

I have never used encryption in Ubuntu myself, and have absolutely no experience with related issues and their solutions. Accordingly, please see if the above links can help you getting booted with existing users to whom those encrypted homes belong. Otherwise you can always create a new user from the root prompt using "*useradd*" then "*passwd*"commands, and boot using that user's id. Following links can be helpful to learn this with examples:
[http://www.cyberciti.biz/faq/howto-add-new-linux-user-account/](http://www.cyberciti.biz/faq/howto-add-new-linux-user-account/)
[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)
[http://www.cyberciti.biz/faq/linux-check-existing-groups-users/](http://www.cyberciti.biz/faq/linux-check-existing-groups-users/)

Frankly, I don't think I can keep up now with that 'encryption' element involved in the issue. I just hope you get your desired data, then do a clean installation on new, fresh partitions.

---

### Post by Hadeda on 2012-03-04
My late response was due to trying out various options.
However, I simply cut my losses and started from scratch.

In hindsight, it helps to understand Ubuntu filestructures right from the start. In which case I am sure that others reading this thread will not encounter the same road blocks and find a solution in this thread. 

[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

Reminder for all users: Never leave your computer unattended when going to seminars and learn these basics: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) 

Thanks varunendra and others!

---

