---
title: "I am a beginner and need some major help."
date: 2009-10-22
forum: General Help
---

### Post by watchman323 on 2009-10-22
I just got a cheap notebook.  I want to use dual boot (window 7 and Ubuntu).  I read that there is a tool that you can use to repartition my harddrive.  I went ahead and took 70GB off of my c drive.  there are also other drive that have already partitioned by the manufacturer.  I was going to use that 70 GB for Ubuntu.  When I tried to do a format on that drive (f:), storage management said that it will change it to dynamic disk.  I went ahead and click ok.  that made my every drive a dynamic drive.  I put in Ubuntu cd into my drive and it went all the way to partition part without problem.  But it didn't recognize my f:.  it only have the option of convert everything to ubuntu or manually doing it.  I am at lost here.  I want both ubuntu and window 7.  I have more restrictions.
my computer doesn't have a window cd.  Compaq is cheap.  I created recover and the boot disk after I did the dynamic conversion.  I read on the net that there is not much I can do in reversing dynamic to basic partition.  I would lose all my data.  I have no problem losing my data but I don't have window 7.  I have an image disk of what is on my harddrive.I formatted my harddrive and did the recovering.  i still have the dynamic partition.  I went to the Microsoft knowledge center.  It said to delete the volumes and then convert.  I was able to delete everything but system drive and c:.  
I don't know what to do now.  I may need a step by step instruction on this.  :frown:

---

### Post by lrcaballero on 2009-10-22
Try this and see if it helps ok! boot up into windows, download and install Partition Wizard, it is very friendly, here's the link [http://www.partitionwizard.com/](http://www.partitionwizard.com/). As soon as you open it, you will see your c drive, f drive, etc.......from here you can manage, resize and delete whatever you need!!!! as you delete stuff it will automatically send it to your c drive..at least in my case that is what happened!!!! I was very successful and deleted 2 OS's and gain all my memory on my C drive. Once you are finish re-install Ubuntu.

Good luck,

Luis

---

### Post by sgosnell on 2009-10-22
The easy way to do all this is to just let the Ubuntu installer take care of the partitioning.  If you can put everything back the way it was, that would be the best, I think, but I'm not familiar with 'dynamic drive'.  The installer will do whatever partitioning is required and give you a dual boot with little management.

---

### Post by lrcaballero on 2009-10-22
Once you install Ubuntu, do the partition when installing Ubuntu, when Ubuntu gets to the partition part, select side by side and go all the way to the bottom and resize the bar to what-ever memory you want to give to ubuntu and Windows.

I hope this was clear, if NOT,  send me a private message in my profile.


Luis

---

### Post by undecim on 2009-10-22
I think the dynamic drive setup fouled it up.

[http://www.petri.co.il/difference_between_basic_and_dynamic_disks_in_windows_xp_2000_2003.htm#](http://www.petri.co.il/difference_between_basic_and_dynamic_disks_in_windows_xp_2000_2003.htm#)
[quote=http://www.petri.co.il/difference_between_basic_and_dynamic_disks_in_windows_xp_2000_2003.htm#]**Warning:** After you convert a basic disk to a dynamic disk, local access to the dynamic disk is limited to Windows XP Professional, Windows 2000 and Windows Server 2003. Additionally, after you convert a basic disk to a dynamic disk, the dynamic volumes cannot be changed back to partitions. You must first delete all dynamic volumes on the disk and then convert the dynamic disk back to a basic disk. If you want to keep your data, you must first back up the data or move it to another volume.[/quote]

Looks like the only thing you can do is backup your files and reinstall both OSs

---

### Post by undecim on 2009-10-22
hmmm... just found this... at the bottom of the page are instructions to convert dynamic disks back to basic (with loss of data, but not OS)

[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

This is for XP though, so it may be different than with 7

---

### Post by watchman323 on 2009-10-23
I am very glade that this forum is so active and supportive.  
I have already looked at the MS's solution.  Problems with that is I don't have a window 7 cd.  I only have a recover cd and an image of the whole harddrive.  I can delete all volumes but not C: because that is where window7 is at.  Window won't let me do that.  I won't be able to convert from dynamic partition to basic until the whole physical drive's volumes are deleted.  If I can do that, which I can with recovery disc.  I can't install window 7 back where I can just have the OS.  I tried formatting and recovering with an image disk, this method put everything back as is, even with the partitions.  I think MS is trying to make window idiot proof, but in this process, they made what we want a little bit harder.  I wish that I could simply pick what I want to recover from my storage image.
When I put in Ubuntu disc, I did came across the partition part.  There were two options.  The top one is to use Ubuntu exclusively.  The bottom part is where you can manually do partition (please correct me, if I am wrong).  I didn't go any further.  Should I have gone further?  If so, which one should I have picked?  I didn't see the option of running side by side at this point.  I want to put Ubuntu on f: so that I can uninstall and install cleanly in the future.
When I get home, I am going to try the following.  Use partition wizard, like suggested, then see if I can put back all partitions that came with the computer without destroying my OS.  Then I will use the Ubuntu disc to do the partition. Did I simply didn't go further enough on Ubuntu's partition?
I am still wanting more suggestions, especially changing my dynamic partition to a basic one, without reinstall window 7 because all I have is an image.  Then install Ubuntu.  
Or whatever that would work.

Thanks guys

---

### Post by watchman323 on 2009-10-23
Another question
If I let or use Ubuntu to partition my harddrive, wouldn't Ubuntu partition mess up window 7's data? Wouldn't I have to reformat the drive that Window is on?  Or am I still too old fashioned and still stuck in window 98 era.

---

### Post by ColdFFF on 2009-10-23
The partitioner in Ubuntu is actually quite smart. It can handle resizing a Windows partition without breaking the data inside it, provided of course that the partition has enough free space.
It may be a good idea to defragment your Windows drive prior to resizing.


Reading through the earlier posts in this thread, I feel the need to ask a bit of a stupid question. Are you trying to install Ubuntu by booting from the LiveCD, or are you using the installer from within Windows?

---

### Post by watchman323 on 2009-10-23
I boot to the Ubuntu cd.  It is something I omitted.  This is not a stupid question especially you are helping me.

Thank you

---

### Post by P4man on 2009-10-23
I may not understand the problem entirely, but if you already have windows 7 installed, then use its diskmanager to resize its own partition. It can do that (and much faster than ubuntu's installer).

Then leave whatever space you want to install ubuntu upon unpartitioned. Ubuntu installer will make partitions in the unpartitioned space if you tell it to, and automatically setup things like extended partitions and swap partitions so you dont have to worry about it.

---

### Post by watchman323 on 2009-10-23
One problem is that window 7 converted the resized partition to dynamic partition, which Ubuntu doesn't like and I can convert it to basic partition.  The solution MS has is basically delete all partitions then convert back, but that requires me to lose window 7.  My computer came window 7 preinstalled. I can only create an image and a recovery cd.   
One difference between dynamic and basic partition is dynamic is used mainly in MS servers and not basic.  Another is basic partition is simply more primitive to deal with . It has less things to worry about.  
I am sorry for all the typos.  I am using my blackberry.

Thank you.

I still need options.  So anything helps.

Eddy

---

### Post by watchman323 on 2009-10-23
I got my basic partitions back.  I emailed Partition Wizard.  I told them about my dynamic partition problem and what I want to do.  They emailed me back with a site of Partition Wizard 4.2.  He said just click and let it restart.  I misunderstood the first time.  But I was successful the second time.  
I want to say thank you to the people on this forum that helped me and the people at Partition Wizard.  Thanks.  I will have more questions when I install Ubuntu in a day or so.  Thank you.

Eddy

---

