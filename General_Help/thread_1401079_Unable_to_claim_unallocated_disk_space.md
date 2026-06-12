---
title: "Unable to claim unallocated disk space"
date: 2010-02-07
forum: General Help
---

### Post by nizdobs on 2010-02-07
I switched my laptop from a Windows only PC to a Windows-Linux dual boot. These 2 OS's use all 4 of my primary partitions:

On Windows I have a 4.4 GB restore partition which can be used to restore the PC to its initial shipping state.

I also have a 28 GB primary windows partition.

On Ubuntu I have a 1.8 GB swap drive and a 28 GB ext3 drive for everything else.

When I configured the dual boot I intentionally left 30GB dik space unclaimed figuring that if I liked Ubuntu I'd assign it to Ubuntu otherwise I could give it to Windows.

I now know that I love Ubuntu but I'm running out of storage on my disk. I can't delete the Windows partition because I need it for a few programs that don't run on Linux. I'd like to just expand the ext3 partition to take the 30GB that are currently unclaimed. However, I don't see an easy way to do this. When I go to create a partition GParted tells me that I can't have more than 4 primary partitions on a drive, that I need an extended partition. Unfortunately, an extended partition is also a primary partition so I have to delete an existing partition to get this to work. 

So my question is: Isn't there some way that I can just extend the Ubuntu partition to take advantage of the 30GB unallocated space? The existing partition is adjacent to the unclaimed space and to the left of it (if that info is helpful).

What's the least painful way I can get my hands on that extra space?

Thanks,

- Niz

---

### Post by electricFan on 2010-02-07
Use a Gparted Live CD or Ubuntu Live CD to accomplish this.

---

### Post by drs305 on 2010-02-07
As was mentioned, you can do this via Gparted. I wrote a guide on expanding the Ubuntu / system partition.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
How to move things around and some tips about the process begin about half way through the first post.

Before you begin, back up any important data. Secondly, if you plan on adjusting the Windows partition in any way, defrag it using Windows software at least twice.

Now, as for suggestions. Without having your current layout (if you have more questions a Gparted screenshot would be helpful), you could delete the swap partition, make an extended partition out of that space, and then move things around within the new extended partition. Depending on where the unallocated space is, this could take a while - possibly longer than a clean install of Ubuntu. But it is a way to create an extended partition. You would need to boot the LiveCD (or via Windows), turn off swap (select the swap partition, right click, Swapoff), and then delete it.

---

### Post by nizdobs on 2010-02-07
Thanks for your reply. I'll take a look at the link you suggested and see if that helps. In the meantime, here's a GParted screenshot. I'm trying to attach the 31 GB of unallocated space to the /dev/sda3 partition.

Does the screen shot mean anything?

Thanks,

- Niz

---

### Post by 2hot6ft2 on 2010-02-07
Looks simple enough.
Boot the livecd.
Start GParted and left click on sda3.
Select Resize/Move and drag the right hand side slider of sda3 to fill the space. Or use the dialers to set the free space before and after to 0 MB
Click Apply and wait for it to finish.
Close GParted
Reboot removing the livecd in the process.
All done

---

### Post by jfl on 2010-02-07
I strongly recommend that once you have created your extended partition, you create a separate "/home" partition (ext3).
If you have to do a new install, like when an upgrade goes wrong, you'll be glad to have all your stuff intact.

In the past, I had problems after resizing widoze NTFS partitions with Gparted and also resizing ext3 with "Partition Magic".
As previously said: BACKUP everything you cannot afford to loose.

---

### Post by 2hot6ft2 on 2010-02-07
You're not creating a NEW partition just expanding an existing partition to use the free space that is unclaimed right next to it from what I read.

Yeah I went back and re-read it and that's what you want to do so no problem just follow the instructions in my post above and you'll be set in about 1/2 hour including reboots.

---

### Post by drs305 on 2010-02-07
You could also tidy up the extended partition a bit. To really clean it up, you could delete Swap and the extended partition, move the fat partition adjacent to sda3, and then recreate the extended partition and within it swap partition.

If you don't want to move the fat partition, you could at least expand the extended partition to the right to incorporate the bit of free space on the right. Since you already have 3 primary partitions, you can't do anything with the bit of unallocated space on the right anyway unless you add it to sda2.

Backup important data before doing any of this.

---

### Post by nizdobs on 2010-02-07
Thank you all so much for the responses. I'm glad that this should be straightforward. 

I hope this isn't a stupid question. When I installed Ubuntu I installed 8.10 so that's the install/Live CD I have. Since then I've upgraded to 9.04 and then to 9.10. Do I need to burn a 9.10 Live CD or can I use the Live CD from 8.10?

Thanks again,

- Niz

---

### Post by electricFan on 2010-02-08
> **nizdobs said:**
> Thank you all so much for the responses. I'm glad that this should be straightforward. 

I hope this isn't a stupid question. When I installed Ubuntu I installed 8.10 so that's the install/Live CD I have. Since then I've upgraded to 9.04 and then to 9.10. Do I need to burn a 9.10 Live CD or can I use the Live CD from 8.10?

Thanks again,

- Niz

You should be able to use the 8.10 cd Niz, keep us posted on the results.

---

### Post by dcstar on 2010-02-08
> **electricFan said:**
> You should be able to use the 8.10 cd Niz, keep us posted on the results.

Some older versions of gparted had annoying bugs, I would use a 9.04 or 9.10 CD myself.

---

### Post by nizdobs on 2010-02-08
Thank you all for your suggestions. I followed the simple instructions you suggested and everything looks good.

Thanks again. I'm so glad that was painless.

- Niz

---

