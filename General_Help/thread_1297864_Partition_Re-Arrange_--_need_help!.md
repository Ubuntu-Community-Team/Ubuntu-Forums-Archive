---
title: "Partition Re-Arrange -- need help!"
date: 2009-10-22
forum: General Help
---

### Post by muito_fofinho on 2009-10-22
Hi ppl,

I'm stuck with the following:

I need more space on ubuntu distribution (I'm making it my main distribution :)) so I stole some free disk space from windows. (see annexed image).

That space is still "unallocated", but I wanted to be used for ubuntu (/dev/sda2).

**How can I do it?**

PS. The GParted says I can't have more than 4 primary partitions.

Thanks in advance!

---

### Post by ColdFFF on 2009-10-22
I take it you want to extend sda2 to also use the space preceeding it. Click  on /dev/sda2 and then click "Resize/Move", and enter 0 for the amount of space before the partition. Finally click apply and gparted will do the rest

Edit:

You will probably need to unmount sda2 before you can resize it. Its probably a better idea to run gparted from a livecd

---

### Post by psycho5 on 2009-10-22
I'm pretty sure you have to unmount your linux partition before you can extend or resize it. You can use the live cd of Ubuntu to do it or you can download the gparted live cd. 

Then when you click resize, just click and drag your ubuntu partition from the left end to cover the entire unallocated space.

And Yes you can't make more than 4 primary partitions. 

If you are going to have more than 4 partitions, then you need an extended partition and make further partitions in it.

---

### Post by M4rotku on 2009-10-22
I would move the partitions so that they are in the following order:

sda1 - windows
unallocated ~ 46 gb
sda2 - linux
unallocated ~ 6 gb
swap
ntfs

So pretty much just move the swap and the ntfs over to the far right and then absorb all of the unallocated space into sda2.

As said above, this is all from a live cd.

---

### Post by Giblet5 on 2009-10-22
Since you have a 37G / partition, and 45G unallocated, the best thing to do is to backup your changes and reinstall, using more "sensible" space allocation. Example backup:

```
sudo mount /dev/sda1 /mnt -tntfs
sudo tar czf /mnt/backup-home.tar.gz /home /etc
```

Save the installed packages: ```
aptitude -F '%?p %?V' search '~i' | awk '{ print $1 }' > ~/packages.txt
cd
sudo mv packages.txt /mnt
```

Example "sensible" space allocation:

Delete the existing / filesystem and partition.
Create an ext3 partition that's 8GB for /
Allocate the rest as ext3 for /home (around 74G).

Reinstall the packages: ```
sudo mount /dev/sda1 /mnt -tntfs
for i in `cat /mnt/packages.txt`
do
  apt-get install $i -fyq
done
```

This is a great time to update! ```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

Then you can restore your backup via; ```
cd /
sudo tar xzf /mnt/backup-home.tar.gz
sudo chown -R $LOGNAME:$LOGNAME $HOME
sudo reboot
```

And finally, remove the files we created under NT: ```
sudo mount /dev/sda1 /mnt
sudo rm /mnt/backup-home.tar.gz /mnt/packages.txt
sudo unmount /mnt
```

You'll be where you are now, but with better resource allocation.

---

### Post by muito_fofinho on 2009-10-22
Ok guys,

Thanks for all your quick answers!
I'm gonna try it using GParted live cd first and do like the 1st three posts: make '/sda2' absorve the unused space using the GParted.

If it doesn't works gonna try like you suggested Giblet5 (but it seems difficult :roll:)

either way, I have another question:

If I make /sda2 absorve the unused space, **will I have problems with grub configuration?**

Thanks once again ;)

---

### Post by Giblet5 on 2009-10-22
> **muito_fofinho said:**
> Ok guys,

Thanks for all your quick answers!
I'm gonna try it using GParted live cd first and do like the 1st three posts: make '/sda2' absorve the unused space using the GParted.

If it doesn't works gonna try like you suggested Giblet5 (but it seems difficult :roll:)

either way, I have another question:

If I make /sda2 absorve the unused space, **will I have problems with grub configuration?**

Thanks once again ;)

Yours is a complicated request, but that super easy route that performs no backup might work too. So, I guess you gotta ask yourself "Do I feel lucky?"  ;)

---

### Post by muito_fofinho on 2009-10-22
> **Giblet5 said:**
> Yours is a complicated request, but that super easy route that performs no backup might work too. So, I guess you gotta ask yourself "Do I feel lucky?"  ;)

I got your point ;)
Thank you!

---

### Post by muito_fofinho on 2009-10-22
Ok people, 
I'm all ready to execute those changes using GParted.

But before, I'de like to ask: **Has anyone made something like this?**

(Using GParted live cd (moving several partitions and including all free existing space into another one))

Thanks!

---

### Post by mechro on 2009-10-22
> **muito_fofinho said:**
> Ok people, 
I'm all ready to execute those changes using GParted.

But before, I'de like to ask: **Has anyone made something like this?**

(Using GParted live cd (moving several partitions and including all free existing space into another one))

Thanks!

Yes

---

### Post by Dullstar on 2009-10-22
I would put unallocated space in the back, so I can use it for new partitions.

---

### Post by ubun_two on 2009-10-22
> **muito_fofinho said:**
> Ok people, 
I'm all ready to execute those changes using GParted.

But before, I'de like to ask: **Has anyone made something like this?**

(Using GParted live cd (moving several partitions and including all free existing space into another one))

Thanks!
I have recently moved partition around on my drive to install Win7 in dual boot, if that's what you are asking.

I resized the extended portion of partition to create a primary partition where Windows would go to.  it took a lot of time resizing a partition that has a lot of data in it already (I left it over night), but it finished perfectly in the end.

---

### Post by muito_fofinho on 2009-10-22
> **mechro said:**
> Yes

And everything went well? 
no problems at all?

---

### Post by muito_fofinho on 2009-10-22
> **ubun_two said:**
> I have recently moved partition around on my drive to install Win7 in dual boot, if that's what you are asking.

I resized the extended portion of partition to create a primary partition where Windows would go to.  it took a lot of time resizing a partition that has a lot of data in it already (I left it over night), but it finished perfectly in the end.

Ok then :D

Gonna go through it... cross your fingers :p
Thank you all!

---

### Post by John Bean on 2009-10-22
> **muito_fofinho said:**
> Ok people, 
I'm all ready to execute those changes using GParted.

But before, I'de like to ask: **Has anyone made something like this?**

Sure; it (usually) works as expected :-)

Incidentally, GRUB normally uses UUIDs rather than partition position to identify the bits it needs so even if partition numbers change it shouldn't break anything. If it does you can easily reinstall GRUB from a live CD so it's not that important anyway.

Further, you don't have to stick to primary partitions; my Ubuntu installation is on sda5 and swap on sda6 which are in an extended partition. When I started  the laptop had Vista on sda1, a recovery partition on sda2, a BIOS tools whatsit on sda3, ... Well, you get the drift. At the time I installed Ubuntu I left the other stuff alone ("just in case") and shrunk the Vista partition before creating an extended partition (sda4) that contains the new partitions I needed. Worked fine without incident, still does. I'll clean it up a bit when I get a Round Tuit.

---

### Post by mechro on 2009-10-22
> **muito_fofinho said:**
> And everything went well? 
no problems at all?

Well, my system is now wholly Linux so I wouldn't hesitate in doing it.

I did once have a dual boot Windows/Ubuntu system with Ubuntu on an external drive that the BIOS wouldn't boot from, but that was sorted with a Grub boot floppy disc.

---

### Post by muito_fofinho on 2009-10-22
> **mechro said:**
> Well, my system is now wholly Linux so I wouldn't hesitate in doing it.

I did once have a dual boot Windows/Ubuntu system with Ubuntu on an external drive that the BIOS wouldn't boot from, but that was sorted with a Grub boot floppy disc.

For professional reason I can't leave dual boot... 
unless I use virtualization on ubuntu :) ...but that stays for another time.

---

### Post by muito_fofinho on 2009-11-03
Hi guys,

I finally made it. :D
I rearranged my entire disk, just as psycho5 told me to (thank you!). But having in mind what Giblet5 told, I made a backup of my disk, just in case.

All went well... except that:
**Now, I can't hibernate :( **

I wasn't expecting this, can anyone help?

Thank you once more!

**PS: output from 'free' command:**
             total       used       free     shared    buffers     cached
Mem:       2071692     756352    1315340          0      26812     308656
-/+ buffers/cache:     420884    1650808
Swap:      2875624          0    2875624

---

### Post by muito_fofinho on 2009-11-03
> **muito_fofinho said:**
> Hi guys,

I finally made it. :D
I rearranged my entire disk, just as psycho5 told me to (thank you!). But having in mind what Giblet5 told, I made a backup of my disk, just in case.

All went well... except that:
**Now, I can't hibernate :( **

I wasn't expecting this, can anyone help?

Thank you once more!

**PS: output from 'free' command:**
             total       used       free     shared    buffers     cached
Mem:       2071692     756352    1315340          0      26812     308656
-/+ buffers/cache:     420884    1650808
Swap:      2875624          0    2875624

I've tried to follow several threads in here like:
- [http://ubuntuforums.org/showthread.php?t=287962]("http://ubuntuforums.org/showthread.php?t=287962")

All seams correct:
- 'fstab' and 'resume' files have the same swap uuid;
- swap partition is correctly active after restart;

But when I do try to start ubuntu after hibernating, it simply starts ubuntu normally :(

Any ideas?
This happen just after moving the partition...

thanks

---

### Post by muito_fofinho on 2009-11-04
PARTITION REARRANGED - SOLVED! ;)
HIBERNATE PROBLEM - SOLVED! :D
 - for this last check [http://ubuntuforums.org/showthread.php?t=1314091]("http://ubuntuforums.org/showthread.php?t=1314091")

Thank you all guy's. ):P

---

