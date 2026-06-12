---
title: "Gparted/Ubuntu not properly reading my partitions."
date: 2010-08-31
forum: General Help
---

### Post by alanmoortician on 2010-08-31
Hello to all the wonderful people in this fabulous community. Please forgive my noobishness.

I'm new to learning about computers and different OS's, so I decided to get my feet wet. I've been trying to dual boot ubuntu on my laptop with windows 7 currently installed, and I've gotten to the stage where I'm creating the partition devoted to ubuntu. 

When I opened Gparted, it didn't read my partition information correctly. First off, it reads two of the files as "unknown" under File System. Second, the labels don't match the disk space. For example, according to my windows disk manager my C: drive is 218.88 GB, but according to Gparted, the 218.88 GB drive is labeled "recovery". It doesn't add up.

I tried posting on the Gparted forum but no one's responded. 

Next, I tried creating the partition on windows disk manager, and when I boot ubuntu from the CD to install it, I get to the "partition selector" screen of the install process and it still doesn't read my partition info correctly. 

I'm stumped, and more than a little bewildered. It's like my computer is schitzo. The Windows side reads the partitions as fine and healthy, and the Ubuntu side can't even read the info properly. I was hoping someone out there knew what was wrong, or if someone could ask me specific questions to help troubleshoot the problem. Or maybe this problem is already solved and I just haven't found the right thread. 

Thanks

---

### Post by rockager on 2010-09-01
> **alanmoortician said:**
>  
Next, I tried creating the partition on windows disk manager, and when I boot ubuntu from the CD to install it, I get to the "partition selector" screen of the install process and it still doesn't read my partition info correctly. 
 
 
elaborate

---

### Post by alanmoortician on 2010-09-01
thanks for responding rockager

On windows, I created a 20GB partition from my C: drive via windows disk manager. I reboot and get on ubuntu from the boot disc and clicked the "install ubuntu" desktop icon. I get to the part where I have to setup the partition layout, and it reads my hard drive information incorrectly, just as Gparted does.

I thought it would be a Gparted error, but it turns out that the whole "Ubuntu" side of my computer can't quite read my hard drive info.

In the situation that I'm writing about, I've already created an unallocated partition, but I used windows disk manager to do it. That unallocated partition doesn't show up as free space when i go to setup the partition layout. It doesn't show up at all in fact.

I'm a self proclaimed noob when it comes to all this stuff, and I'm not quite sure how to handle this situation, and I'm sorry if I don't describe my situation with the most clarity. It's the first time I've encountered these types of problems and I'm not entirely sure what I'm looking for.

---

### Post by rockager on 2010-09-01
try formatting the unallocated partition to fat32
then see if ubuntu recognises the partition
if it does then reformat the partition (which was previously fat32) to ext 2/3/4 and install ubuntu to it.
 
p.s have you tried any other disk management utility in ubuntu?

---

### Post by utnubuuser on 2010-09-01
which version of Windows?  Vista can be problematic...

---

### Post by alanmoortician on 2010-09-01
Windows 7

---

### Post by srs5694 on 2010-09-01
First, "unallocated partition" is an oxymoron. Disk space can be either unallocated (in which case it's not a partition) or allocated (in which case it is one or more partitions).

Second, I'm not convinced that there's anything wrong. Windows uses drive letters (C:, D:, and so on) to refer to partitions, but Linux doesn't. Windows and Linux recognize different filesystems and use different methods to determine which drives they'll even examine for filesystems. Thus, a partition that's shown as, say, D: in Windows might turn up with a completely different label (Data, or Unknown) in a Linux partitioning tool. Your initial description of the problem is incomplete, but what little information you provided doesn't lead me to believe there's anything more going on than this.

To be sure, though, I recommend you post a screen shot of the Windows partitioning tool along with either a screen shot of GParted's view of the disk or the text-mode output of typing "sudo fdisk -lu" at a shell prompt. Either action will enable us to see what's going on with the disk in a relatively precise way.

---

### Post by Mark Phelps on 2010-09-01
Don't use the Win7 Disk Management utility to create partitions; only use it to shrink and/or move NTFS partitions.

You should leave the unallocated space as is (unformatted) and allow the Ubuntu installer to format it by choosing "largest free space" when you do the install.

IF you didn't do that, boot using an Ubuntu LiveCD, open up the Partition Editor, and remove the partition(s) you created for Ubuntu under Win7.  Then, reboot using the CD and install as I mentioned above.

---

### Post by alanmoortician on 2010-09-01
alright, I'll try some of these fixes.

Thanks rockager, utnubuuser, srs5694, and Mark Phelps for your suggestions so far. I'll post how it turns out.

---

### Post by alanmoortician on 2010-09-04
Well, I'm still having some trouble. To help illustrate my problem, heres what I'm seeing.

[IMG]http://i497.photobucket.com/albums/rr336/alanmoortician/rsz_windows_screen.jpg[/IMG]

Taken from windows 7 disk manager. Volumes and Sizes are clearly labeled. Nothing appears to be wrong

Now heres what I see when I boot ubuntu from the CD and try to manage the same disk volumes using Gparted

[IMG]http://i497.photobucket.com/albums/rr336/alanmoortician/rsz_3screenshot.jpg[/IMG]

If this is a magic trick, its not a very good one. I hate to admit this, but I'm not entirely sure what I'm looking it, I just know it doesn't add up. The volume labels are matched up with the wrong sizes, and there are ! error symbols everywhere. I inspected the partition marked /dev/sda3 in Gparted, and this is the info it gave me: 

[IMG]http://i497.photobucket.com/albums/rr336/alanmoortician/rsz_screenshot-3.jpg[/IMG]

I can't really make heads or tails of this, and I'm not sure where to begin.

I've taken screenshots of the error info on all the volumes. If you need to see those too, just ask and I'll post them up.

---

### Post by sje46 on 2010-09-04
I recently installed Mint on my machine (which is based off Ubuntu) and I had a similar problem.  What happened is this: I had four primary partitions: C:// , HP_TOOLS, boot, and recovery.  I initially tried to set the C partition to 25GB...whoops.  This made it unreadable.  Yet I could still get on Windows...even though it performed an autocheck each time.  All my files were, to my knowledge, still there.  But I could not move or resize or partition anything to the unreadable C partition, nor could I add a logical/extended partition or anything to the other ones.  Eventually I had to move all my files to another computer and completely restore windows.  This *might* be what you have to do.  Then after that you have to make sure you don't have four primary partitions, so you may have to delete HP_TOOLS, which I still don't understand what that is.

To restore windows, I had to press F11 at boot (well, first ESC for me, then F11...depends on your model, really).  Until I did that, I could not do anything with my partitions.  Neither with the windows 7 partitioner, GParted, or the Mint LiveCD

---

### Post by srs5694 on 2010-09-04
I think the problem may be that your Windows partitions are all marked as "dynamic." I'm not an expert on this partition type, but I believe this is a synonym for the Windows Logical Disk Management (LDM), which in turn is similar to a Linux Logical Volume Management (LVM) configuration. I believe that Linux won't be able to directly mount these partitions as NTFS; instead, they'll be either inaccessible or accessed much like logical volumes in an LVM configuration, via files in /dev/mapper. Try posting the text-mode output of both of the following commands to give us more information:

```

sudo fdisk -lu /dev/sda
ls /dev/mapper

```

You may be able to resize the LDM partition(s) within Windows, but I'm not very familiar with the Windows partitioning tool, so I'm not sure precisely how you'd do this. Note that, if I'm right, you need to resize the LDM partition(s), not the C: or D: drives, which are contained within the LDM partition(s).

---

