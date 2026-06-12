---
title: "GParted - Can't maximize partition?"
date: 2009-12-25
forum: General Help
---

### Post by Roasted on 2009-12-25
I have a disk partitioned as follows:

60gb NTFS
1gb SWAP
15gb EXT4
74gb Unallocated

I booted to an Ubuntu LiveCD hoping I could use GParted to extend NTFS to use the remaining 74gb that's unallocated, but I cannot touch that 74gb unallocated space to save my life. I tried making it a partition, unformatted, unallocated, etc. I just cannot move any of my existing partitions.

What do I do? How do I get a hold of that unused space? I was really banking on being able to do this and not being able to is quite a damper...

---

### Post by wilee-nilee on 2009-12-25
You have to turn swap off I think, but be careful with changing the ntfs partition. If the partitions are in that exact order I am not sure exactly what your able to actually do.

---

### Post by Roasted on 2009-12-25
> **wilee-nilee said:**
> You have to turn swap off I think, but be careful with changing the ntfs partition.

Well, -technically-  I should be safe.

I'm saving the contents of the 80gb partition:
NTFS/Swap/EXT4

And restoring them to a brand new, unused 160gb partition. Therefore if the restore (and resize) tanks on me, I ruin the install on a 160gb drive. So what? Pop the 80 back in and the user is still good to go. :guitar:

Why do you say be careful with changing the NTFS partition? Is there something I should know?

---

### Post by wilee-nilee on 2009-12-25
> **Roasted said:**
> Well, -technically-  I should be safe.

I'm saving the contents of the 80gb partition:
NTFS/Swap/EXT4

And restoring them to a brand new, unused 160gb partition. Therefore if the restore (and resize) tanks on me, I ruin the install on a 160gb drive. So what? Pop the 80 back in and the user is still good to go. :guitar:

Why do you say be careful with changing the NTFS partition? Is there something I should know?

The only thing I have seen is advice to change the ntfs with windows (with vista and W7) but I haven't had any problems myself using gparted with W7. If you have no problems with installing what you need then do what works, I think the swap just has to be off on a live Cd to move stuff around.

---

### Post by sdennie on 2009-12-25
Are you sure you don't have any other partitions?  What you are describing sounds like what happens if you have 4 primary partitions on the disk and unallocated space in a location that is not contiguous with a useful partition.  Try:

```

sudo fdisk -l

```

---

### Post by Roasted on 2009-12-25
> **wilee-nilee said:**
> The only thing I have seen is advice to change the ntfs with windows (with vista and W7) but I haven't had any problems myself using gparted with W7. If you have no problems with installing what you need then do what works, I think the swap just has to be off on a live Cd to move stuff around.

I was running this system off of an Ubuntu LiveCD when I tried this. Is this what you mean? Or do I have to "deactivate" SWAP despite being ran off of a LiveCD?

> **lieqie said:**
> you can only extend your ntfs parttion from continuous space,

so you have to move parttions behind ntfs parttion to make the space just behind the ntfs parttion.

That's what my train of thought was, and what I tried to do. I tried to "move" the EXT4 partition to the back of the drive, along with swap, to organize it like:

NTFS - Unallocated - Swap - EXT4 = therefore expanding NTFS up to the front of Swap. But when I hit "resize/move" for EXT4 to move it to the back of the drive, the only thing it appeared I could do was downsize it - not move it or upsize it.


> **sdennie said:**
> Are you sure you don't have any other partitions?  What you are describing sounds like what happens if you have 4 primary partitions on the disk and unallocated space in a location that is not contiguous with a useful partition.  Try:

```

sudo fdisk -l

```

The only thing I did was I popped in the Windows XP disc, created 1 partition of NTFS @ 60gb, installed. Put in the Kubuntu LiveCD, 1gb SWAP, 15gb EXT4 root. I didn't do anything "out of the ordinary", so whatever the default options would be for a user just slapping together a quick XP Pro + Kubuntu EXT4 setup is what I did.

sudo fdisk -l output:

 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7664    61561048+   7  HPFS/NTFS
/dev/sda2            7665        9726    16563015    5  Extended
/dev/sda5            7665        7786      979933+  82  Linux swap / Solaris
/dev/sda6            7787        9726    15583018+  83  Linux

Picture of GParted:

[http://img684.imageshack.us/img684/2310/snapshot1r.png](http://img684.imageshack.us/img684/2310/snapshot1r.png)

---

### Post by Mahngiel on 2009-12-25
Well, you're not going to be able to extend any of your partitions looking at that.  You're going to have to do some reorganizaion.

I would try to create a new partition of 15gb and put it at the END of the partition table, with all of the free space you between it and your extended partitions.

You can then copy+paste the /sda2 into the new creation.

Once everything has been pasted in order, reboot and check out your unix partition, to make sure everything works and nothing was damaged in the copying.  If all looks good, you can go back into gparted and delete the sda2.

That'll free up all kinds of space to which you can extend for your NTFS

Hope this helps

---

### Post by Roasted on 2009-12-25
> **Mahngiel said:**
> Well, you're not going to be able to extend any of your partitions looking at that.  You're going to have to do some reorganizaion.

I would try to create a new partition of 15gb and put it at the END of the partition table, with all of the free space you between it and your extended partitions.

You can then copy+paste the /sda2 into the new creation.

Once everything has been pasted in order, reboot and check out your unix partition, to make sure everything works and nothing was damaged in the copying.  If all looks good, you can go back into gparted and delete the sda2.

That'll free up all kinds of space to which you can extend for your NTFS

Hope this helps

Hang on, let me try and understand this:

Create a new 15gb partition at the end of the drive and COPY and paste the contents? Is this something I do in gparted? I can actually "clone" a partition within gparted??

I think to be safe I'll have to set up a spare rig in the same format to test with before I try it on a main system...

---

### Post by Mahngiel on 2009-12-25
yes, you can 'right-click' and copy a partition, and 'paste' it elsewhere

> [B]GParted Manual
[/B]Copying and Pasting a Partition

    * GParted Manual
    * Working with Partitions
    * Advanced Partition Actions

To copy a partition:
          
   1.Select an unmounted partition.
                    See Section 5.1.1 &#8213; Selecting a Partition.
                    
                  2.Choose:
                    Partition &#9656; Copy.
                    The application marks the partition as the
                    source partition.
                    
                  To Paste a partition:
          
1.Select an unallocated space on a disk device.
                    See Section 5.1.2 &#8213; Selecting Unallocated Space.
                    
                  2.Choose:
                    Partition &#9656; Paste.
                    The application displays the
                    Paste /path-to-partition
                    dialog.
                    
                  3.If you want you can adjust the size and location of the partition.
                    See Section 5.2.5.1 &#8213; Specifying Partition Size and Location.
                    
                  4.If you want you can specify the alignment of partition.
                    See Section 5.2.5.2 &#8213; Specifying Partition Alignment.
                    
                  5.Click Paste.
                    The application displays the copy partition operation
                    in the Pending Operations pane.
                    
                  The copy of the partition has the same label
          and the same Universally Unique Identifier (UUID)
          as the source partition.
          This can cause a problem when mount actions use the
          partition label or the UUID to identify the partition.
          The problem is that the label and the UUID are not unique.
          
You are advised to do one of the following:
            

    *Change the UUID of the partition.
                      If the partition label is not blank, change the label
                      of the partition.
                      
    *Use some other method to ensure that the source
                      partition and the copy of the source partition
                      are not used on the same computer at the same time.
                      

---

### Post by running_rabbit07 on 2009-12-25
> **Roasted said:**
> Why do you say be careful with changing the NTFS partition? Is there something I should know?

Supposedly, Windows Vista and 7 have issues when their partitions get altered by outside sources.

---

### Post by Roasted on 2009-12-25
Whaaaaaaat. That's awesome.

Curious trivia question - what if I copy the EXT4 root partition, paste it to the back of the drive, and don't delete the existing EXT4 root partition? Essentially, Linux will exist twice on that drive. What happens? Does Grub just auto detect them on the fly and I have two existing usable Linux installs to work off of?

> **running_rabbit07 said:**
> Supposedly, Windows Vista and 7 have issues when their partitions get altered by outside sources.

Really? I used GParted with Vista and 7 before and I never had issues.  *shrug* I only used it once with 7 and two or three times with Vista, though...

---

### Post by Mahngiel on 2009-12-25
I don't think it's a good idea to have two roots.  Anyways, if you left it there, you couldn't extend the partition.

---

### Post by Mahngiel on 2009-12-25
let me knw how it turns out

---

### Post by Roasted on 2009-12-25
> **Mahngiel said:**
> I don't think it's a good idea to have two roots.  Anyways, if you left it there, you couldn't extend the partition.

Oh yeah, I completely understand that. And yeah, you CAN have two roots... For example, I run Vista/Ubuntu on my computer, but recently I was getting very interested in KDE so I wanted to have a native install of KDE separate from Ubuntu. So I downsized my home partition and put Kubuntu after, making it look like:

80gb NTFS Vista
1gb SWAP
20gb Ubuntu Root EXT4
360gb Home EXT4
20gb Kubuntu Root EXT4

Works fine. No issues. However because I *installed* Ubuntu and Kubuntu, Grub picked them both up. I would assume that copying partitions in GParted wouldn't prompt Grub to auto-detect them. But anyway, it was just a question I had based out of pure curiosity.

I'll certainly be utilizing Clonezilla LiveCD here. I'll make a full backup image of the entire disk before I screw around with it. Then if it backfires, I can fire the previous image back. That, plus the fact I'll be working on a completely different hard drive should mean I'm in the clear from potential data loss. But I'll post back whenever I give this a shot. I'm going to set up a mimic'd system on my spare computer to test it first. So we'll see how it goes. Thanks again!

---

### Post by Mahngiel on 2009-12-25
why do you make your OS partitions so large? you could easily share a data partition between all your OS's if you created a fat32 partition. *shrug* it's what i do.

And yes, no matter how you move around your partitions, Grub will know they're there. the .cfg file (if you're using grub2 - menu.lst if grub legacy) has it - though you _*may*_ have to edit if the partition name changes, i.e. sda2 to sda3? not sure about that.

G'luck.

---

### Post by running_rabbit07 on 2009-12-25
> **Roasted said:**
> Really? I used GParted with Vista and 7 before and I never had issues.  *shrug* I only used it once with 7 and two or three times with Vista, though...

That's why I said supposedly, I've never tried it.

---

### Post by raymondh on 2009-12-25
Let's try something ... still using gparted.

-  Click to highlight the extended partition
-  Drag the right border all the way to the right which will occupy the unallocated
-  Click to highlight sda6.  Click on the center of the box and move the whole box to the right ... up to the new right-side border of the EXTENDED partition.  That will move the unallocated to the left.
-  Click to highlight swap.  Move the whole box to the right ... up to the left-side border of sda6.  That will move the unallocated space left, again.
-  Click to highlight the EXTENDED partition.  Drag the left border to the right ... up to the left-side border of swap.  That will move the unallocated OUTSIDE the extended partition and beside the NTFS

If OK, use windows disk manager to enlarge existing windows and occupy the unallocated beside it.  If OK, let windows run its' checkdisk.

If you have already tried this, then I apologize for suggesting in the first place.  I just finished moving partitions around using gparted from a live gparted CD ... something similar to what you wish to accomplish.

Regards,

---

### Post by Roasted on 2009-12-25
> **Mahngiel said:**
> why do you make your OS partitions so large? you could easily share a data partition between all your OS's if you created a fat32 partition. *shrug* it's what i do.


I could do that, but with Windows and how many programs, games, etc my brothers use, there's no telling how much space they'll suck up. So I just allocated the most space for NTFS and the remainder for Linux if they wanted to mess around with it. Plus, Linux can read/write to NTFS, so I don't see why I'd limit myself to FAT32. *shrug*

---

### Post by Mahngiel on 2009-12-25
good point. Fat32 just seems safe to me, thumbdrives are all formatted as fat32, so i suppose there's some use to the scheme

---

### Post by Roasted on 2009-12-25
> **Mahngiel said:**
> good point. Fat32 just seems safe to me, thumbdrives are all formatted as fat32, so i suppose there's some use to the scheme

On my personal computer, FAT32 wouldn't fly, simply because I have image backups and whatnot that exceed 4gb in size. With my brothers, it may be do-able. But ehh, what's done is done. :P

---

### Post by Roasted on 2009-12-25
I'm glad I did a test on a different computer.

80gb drive.

20gb NTFS Windows
1gb Swap
19gb EXT4 Root
40gb Unallocated

I moved some stuff around, copied and pasted partitions, took about 15 minutes, then rebooted.

Error - no such partition
grub rescue>

---

### Post by SecretCode on 2009-12-27
> **running_rabbit07 said:**
> Supposedly, Windows Vista and 7 have issues when their partitions get altered by outside sources.

> **Roasted said:**
> Really? I used GParted with Vista and 7 before and I never had issues.  *shrug* I only used it once with 7 and two or three times with Vista, though...

If you change the start position of the partition - as a result of the 'round to cylinders' option - you can apparently mess up Windows.

Also, on some drives some versions of GParted change the heads-per-cylinder geometry. Linux isn't affected but Windows fails utterly - doesn't even begin to boot. There's been some discussion on the gparted forums about this problem.

---

### Post by SecretCode on 2009-12-27
> **Roasted said:**
> I'm glad I did a test on a different computer.

80gb drive.

20gb NTFS Windows
1gb Swap
19gb EXT4 Root
40gb Unallocated

I moved some stuff around, copied and pasted partitions, took about 15 minutes, then rebooted.

Error - no such partition
grub rescue>

What is your *fdisk -l* after moving? (And before if you saved it.)

It's pretty hard to advise without knowing which of these are logical partitions and how big the extended partition is.

Maybe grub is pointing to (hd0,3) and your ext4 is no longer partition 3?

---

### Post by Roasted on 2009-12-27
I can't figure that part out now. I already crashed the system and put Fedora 12 on it.

I was thinking though, instead of moving the unallocated space at the end of the drive behind the NTFS drive, would it be easier for me to just move the individual swap and ext4 partition to the back of the drive and then, in essence pushing the unallocated space right up behind NTFS anyway?

---

### Post by SecretCode on 2009-12-27
That sounds like the same thing to me :) ... gparted moves partitions not the unallocated space as such.

I think your difficulty comes with where the extended partition is. Is your main machine still partitioned as shown in your post #6? You should be able to **move** (not resize, and definitely not copy/paste) the extended partition sda2, either to the end of the drive or something like 40GB further on.  **You can't move a logical partition (sda5 or sda6) anywhere except within the extended partition - but you should be able to move the whole extended partition.**

Then you would have unallocated space adjacent to sda1, which you could then resize. But first, boot into windows and run a chkdsk (if it doesn't do it automatically). 

I'm not sure if you've tried this approach yet.

First of all, use clonezilla to back up your MBR and sda1 and sda6!

---

