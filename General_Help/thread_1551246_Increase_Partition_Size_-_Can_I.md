---
title: "Increase Partition Size - Can I?"
date: 2010-08-12
forum: General Help
---

### Post by listerdl on 2010-08-12
Hi, I have a tricky situation here....

I have a 

20 gig partition to house Windows 7
20 gig partition to house Ubuntu 

and a shared storage of like 130 gig (by making linux read NTFS)

Now, I use windows a lot for office work and the problem is that it has outgrown its 20 gig....can I increase the windows partition by decreasing the shared D Drive storage or will I enter a world of pain?

Thanks!

---

### Post by kahlil88 on 2010-08-12
Resizing partitions is loads of fun -- can take hours when you resize "to the left" but it's doable. Just be sure your computer is plugged into a good surge protector before you start. You may need to perform a disk check on the NTFS partition, then boot the Ubuntu Live CD and run GParted....it's a pretty straightforward process.

---

### Post by Mark Phelps on 2010-08-12
> **listerdl said:**
> ...can I increase the windows partition by decreasing the shared D Drive storage or will I enter a world of pain?

It's going to be complicated because you're going to be changing three partitions -- using two different filesystem formats.

You should boot into Win7 and use the Disk Management utility to shrink the shared NTFS partition.  That could take some time.

Then, boot into a GParted LiveCD (which you can download and burn from distrowatch.com) and "move" the Ubuntu partition to the right.

Then, boot back into Win7 and use the Disk Management utility to resize the OS partition.  This will require a reboot but it will work and it may take some time.

---

### Post by listerdl on 2010-08-12
> **Mark Phelps said:**
> It's going to be complicated because you're going to be changing three partitions -- using two different filesystem formats.

You should boot into Win7 and use the Disk Management utility to shrink the shared NTFS partition.  That could take some time.

Then, boot into a GParted LiveCD (which you can download and burn from distrowatch.com) and "move" the Ubuntu partition to the right.

Then, boot back into Win7 and use the Disk Management utility to resize the OS partition.  This will require a reboot but it will work and it may take some time.

Thanks for your reply. I added a screenshot to clarify your advice - so basically would you still agree to your advice now that you have seen the screenshot? Thanks very much i appreciate your help.

---

### Post by Mark Phelps on 2010-08-12
Sorry, didn't realize there was a partition in the way.

Since you can't merge space with an intervening partition in the way, you will have no choice to to remove the space, move the Linux partition to the right into that unallocated space, and then use the Win7 Disk Management utility to expand the "C" drive to fill the new space to the left of the Linux partition.

---

### Post by The Bird Man of Alcatraz on 2010-08-13
I don't mean to steal the thread but I just had a large problem with increasing an extended partition's size to the left.  I increased the enclosing partition first (I don't know the technical term for it) and that went fine.  I came back in the morning to find the partition resize had failed, and the stuff on the 170 GB partition inaccessible.

On a side note, the now corrupt partition downsized to the size of all the files on it.

Is there any solution?  Thanks a bunch

---

### Post by listerdl on 2010-08-13
> **The Bird Man of Alcatraz said:**
> I don't mean to steal the thread but I just had a large problem with increasing an extended partition's size to the left.  I increased the enclosing partition first (I don't know the technical term for it) and that went fine.  I came back in the morning to find the partition resize had failed, and the stuff on the 170 GB partition inaccessible.

On a side note, the now corrupt partition downsized to the size of all the files on it.

Is there any solution?  Thanks a bunch

No worries with stealing the thread in fact you actually adressed something I am worried about. I have so much important data on my machine, (which i back up each week) that I am too worried to do this partition issue now that I have read about it. It just looks like things could go wrong.

I think the best thing for me and perhaps you is that we take an image of our drives, using clonezilla etc and wipe our machines then re-install.

Your lost data might hopefully still be recoverable though...not sure how though!

Thanks!

---

### Post by varunendra on 2010-08-13
While tools like GParted make it extremely easy to manipulate partitions the way you wish, there is no such tool available that guarantees a "SAFE" manipulation.

Partition manipulation always involves some level of risk of data-loss, and almost all the programs do 'warn' you before applying changes.

So to be safe, it is always recommended to backup your data on an external media (cd / dvd / USB hard disk, etc.) before applying any change to the partitions. The data may simply be copy-pasted to the external media. If the whole system is to be backed up, then using [clonezilla, partimage]("http://www.dedoimedo.com/computers/free_imaging_software.html") etc. is a good idea.

If you don't have any media to backup your data upon, and you have to take the (slight) risk, it is advised to completely "De-fragment" your drives first to make 'data-recovery' easier if anything goes wrong.

However, you shouldn't get too alarmed (you can't avoid using a car just for the fear of road accidents, right!!:))


@The Bird Man,
Trying TestDisk or a similar tool to recover data, then deleting-recreating partitions would be best option for you.

---

### Post by The Bird Man of Alcatraz on 2010-08-22
@ listerdl
It's funny; in retrospect, I should have just bought another hard drive.  I was trying to optimize the hard drive I had.  So much space is so cheap nowadays.
@ varunendra
Thanks; I'll try that program, and Photorec.

---

