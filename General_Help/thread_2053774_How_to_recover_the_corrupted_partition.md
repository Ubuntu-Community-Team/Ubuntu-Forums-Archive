---
title: "How to recover the corrupted partition"
date: 2012-09-06
forum: General Help
---

### Post by bijupp on 2012-09-06
Hello

I am not much familiar with ubuntu.  I have installed ubuntu 11.04 multiboot with windows.  Recently I tried to arrange partitions in my system and ended up with lose of all partitions..  Now the system does not boot... I have tried to correct the error with "testdisk" utility using live CD but at last I found that some the partitions are listed twice or more and some partitions are not seen..  I wish not to loss any files... the detailed screen shots are attached please help me..


Screens of testdisk..
[ATTACH]223745[/ATTACH]

---

### Post by coldraven on 2012-09-06
Firstly I am not going to open a Word document from someone that I do not know. Try attaching PNG or JPG files instead.
Also Testdisc is very powerful and it would be difficult to give advice remotely.

Try using PhotoRec to recover your files before doing any more damage.
PhotoRec comes with Testdisc.
Read the Testdisc documentation, there are good links here:
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by bijupp on 2012-09-06
> **coldraven said:**
> Firstly I am not going to open a Word document from someone that I do not know. Try attaching PNG or JPG files instead.
Also Testdisc is very powerful and it would be difficult to give advice remotely.

Try using PhotoRec to recover your files before doing any more damage.
PhotoRec comes with Testdisc.
Read the Testdisc documentation, there are good links here:
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)


Thank u for your replay

I have run testdisk and Analysed the disk and got the following result that matches with my corrupted partion table

[ATTACH]223749[/ATTACH]


After that I quick search and got the following result

[ATTACH]223750[/ATTACH]


In that I do deeper search and got the following with some replicated disk partitions what i have to do next ?

[ATTACH]223751[/ATTACH]

---

### Post by oldfred on 2012-09-06
It looks like you changed partitions a lot. Testdisk finds most all of the old partitions so you can recover an old partition. But you cannot recover an old one that overlaps a new one unless you want to delete new one. It can be a real puzzle to figure out. But

You current partitions look like they are all there? 

What does this show from Terminal

sudo fdisk -lu
and
sudo parted /dev/sda unit s print

Does gparted show partitions?

---

### Post by dragonfly41 on 2012-09-06
> .. what do I have to do next?

I've recently been through the same process with a failed (corrupted partitions) dual boot.

You should read the testdisk step-by-step manual.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_upted partitions) Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

It is normal to see duplicate lines.  One line represents the sector backup.

You have to go through each entry (in deep search output) line by line and in each line apply P=(list files).   Look for files and if you find any then that is one partition to recover.   The other line (looks like a duplicate) will show no files.

If you see a file structure you can copy them to a mounted backup drive (eg. a USB drive).  You must have a spare drive (repository) with enough space to hold the files you intend to copy.

When you have copied your files you can use the left/right arrow (on the partition which shows files) to switch from D=Deleted to other options such as P=Primary .. you will see the line colour change to green.

You can carry on doing this with the other lines and then WRITE the partition table from the testdisk menu.  This overwrites the corrupted partition table.

It helps if you have kept as a blueprint a copy of the partition layout before your partitions were corrupted.

I'm not saying that this is a simple process .. it takes hours to do each deep search so it is better if you can prepare beforehand and have a large USB drive at hand to copy any recovered files from each partition.   Also if you are copying files make sure that you first cd into that directory or sub-directory and from there launch testdisk .. otherwise if you launch testdisk from your root your recovered files will be mixed up with your root files.

e.g. 
md ~/recovered_files
cd ~/recovered_files
sudo testdisk

or
md ~/recovered_files/windows
cd ~/recovered_files/windows
sudo testdisk

i.e. create a mirror tree structure in your empty USB drive, each subdirectory holding your windows and ubuntu recovered files.  One testdisk run per partition.

I have a drive (/dev/sda) in similar state (but fewer partitions than you) and I have removed it so I can analyse it in slave mode in a USB enclosure.

I intend to use RecoverMyFiles from within Windows since that is the most reliable (windows only) file recovery tool I've used.   There are other windows tools for recovering ext4 partitions. Look for "Raise Data Recovery".

Again read the step-by-step again and again.  The recovery only starts after your deep search.   But if running ubuntu you can be working while this search goes on in background.   You can't "suspend" a deep search so start early in the day or leave the computer running.

---

### Post by Mark Phelps on 2012-09-06
> **dragonfly41 said:**
>  ... I intend to use RecoverMyFiles from within Windows since that is the most reliable (windows only) file recover tool I've used...
BIG +1 for that!  Have had that recovery files better than any other Windows tool.  And, the Windows tools are able to restore the directory and filenames correctly.

You can also try GetDataBack for NTFS -- comes from the same folks (Runtime Software).

Both versions can be downloaded for free and run in MS Windows -- to see what they recover.  But, you have to purchase a license to save the recovered files.

---

### Post by bijupp on 2012-09-08
Thank u all for the replies


while checking the system using Ubuntu live CD I noticed that the C drive is recognized.  Then I tried to recover the windows 7 boot.  I use the install CD of win7 and boot into command prompt from its recovery options  and recovered the command "bootrec /fixmbr".  Then I reboot the system..   

thank god  

my system boot well in windows as earlier.  
[ATTACH]223863[/ATTACH]

Only the difference is that my Ubuntu is not seen..  even after this I have used live CD but It does not show the linux partitions and the NTFS partitions detected by windows
[ATTACH]223864[/ATTACH]


Is ubuntu less powerful than windows  !!!!    
[SIZE=4][COLOR=Red]Is there is any way to recover only the Linux partitions  ???[/COLOR][/SIZE][SIZE=4]
[/SIZE]


Thank u  [[COLOR=#DD4814]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711")   I have done the 2 commands as you have said the and the output as shown below.  
[ATTACH]223865[/ATTACH]     [ATTACH]223866[/ATTACH]


Thank u  [dragonfly41]("http://ubuntuforums.org/member.php?u=1261878")  &   [Mark Phelps]("http://ubuntuforums.org/member.php?u=311399") for your valuable comments...

---

### Post by oldfred on 2012-09-08
You can copy terminal output directly to your message. And if longer, use code tags to make it easier to read & preserve any formating. You highlight like copy and click on # to automatically add code tags. 

Your parted output shows overlapping partitions. It looks like your extended partition starts before the end of the sda1 partition.

It is normal for Windows not to see Linux partitions, but partition table errors create major problems for most system tools.

First backup partition table and copy to an external device.
sudo sfdisk -d /dev/sda > parts_sda.txt

With overlapping partitions the main question is which do you want to save. If you somehow wrote data into both then you will have corruption as one will not have correct data. Often the data is not written to the end of partition and the beginning is more important so you want to shrink the first and preserve the second. Since yours is the extended partition it becomes even more important as it extended is damaged then maybe all the partitions inside will have issues. Backup of partition table or testdisk then may be only solution.

Fix overlaping partition error srs5694 Post #34
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
I reviewed the above and that was more where a full partition was wrong and different than your issue.

I think you are going to have to manually edit the text file you create parts_sda.txt and reimport it like these threads.
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by bijupp on 2012-10-06
I recently downloaded kubuntu I ran the live cd and found that the the lost linux partitions are shown (but most of my data are lost by way of trying various methods to recover it ) but in ubuntu even the partitions are not detected and listed... 


Why ???


I know Ubuntu and Kubuntu are linux based..  


Is kubuntu is better than ubuntu ???  what are the differences between them ???


Is there is any distribution is better than ubuntu ???


Is there is any distribution better in recovering corrupted partitions ???

---

### Post by oldfred on 2012-10-08
You have to fix the overlapping issues. 

Perhaps some software may show one other the other of overlapping partitions, but most just see the problem and do not work.

---

### Post by dragonfly41 on 2012-10-08
I read in a forum a few days ago that puppy linux distro might reach the parts (lost files) that other distros don't reach but I've not tested that  yet.

---

