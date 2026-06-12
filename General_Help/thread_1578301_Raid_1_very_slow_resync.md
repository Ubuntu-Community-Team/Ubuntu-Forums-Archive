---
title: "Raid 1 very slow resync"
date: 2010-09-20
forum: General Help
---

### Post by Dillius on 2010-09-20
I have a low power machine I use as an SFTP server.

It currently contains two raid 1 arrays, and I am working on adding a third. However, I'm having a bit more trouble with this array than I did the prior arrays.

My suspicion is that I have a bad drive, I am just not sure how to confirm it.

I have successfully formatted both drives with EXT3 and performed disk checks on both which did not indicate a problem.

I create my raid array...

```
sudo mdadm --create --verbose /dev/md2 --level=1 --raid-devices=2 /dev/sde1 /dev/sdf1
```

and it begins the initial resync. However, after a VERY short time the speed will drop to 0K/sec and the time indicates some millions of minutes.

I can see it progressing in the blocks count, but it's incredibly slow. In the course of 5 minutes it progressed from 1024/1953511936 to 1088/1953511936.

Checking top, not even 10% of my CPU is being used. Are there any other performance items I could check that could be affecting this?

Anyone else experienced something like this? Any help or advice would be greatly appreciated.

---

### Post by john newbuntu on 2010-09-20
Have you tried this:
[http://www.linuxhowtos.org/Tips%20and%20Tricks/raid1speedup.htm](http://www.linuxhowtos.org/Tips%20and%20Tricks/raid1speedup.htm)

---

### Post by Dillius on 2010-09-20
> **john newbuntu said:**
> Have you tried this:
[http://www.linuxhowtos.org/Tips%20and%20Tricks/raid1speedup.htm](http://www.linuxhowtos.org/Tips%20and%20Tricks/raid1speedup.htm)

I have min at 100000 and max at 200000. It did not make a difference in my attempts.

---

### Post by Aurawin on 2010-09-20
Have you looked at the smart data for the individual drives?

But yes when writing takes that long you certainly have a bad drive in there.  You an get a status of each device

I'll assume your using mdadm and the device is md127 but could be md0

mdadm --detail /dev/md127

If you use dmraid I would just refer the the individual components and look at the smart data in the Disk Utility.  If one is bad you will need to remove it.

You will need to sync but only if you have a backup.  There is a much faster way when you create the array like you did, use --assume-clean option.  

I have a 2TB mirror setup so I don't have day it would take to sync.  I copied the data to a separate disk.  using cp -Rfp /media/raid /media/backup.

Then I created the array using everything typical for my devices but included --assume-clean
Then I formatted the 2TB raid with ext4.
Then I copied the data back into the newly mount array.

I was up in running in under two hours.  Sure beats all that extra time synchronising.

---

### Post by Dillius on 2010-09-20
> **Aurawin said:**
> Have you looked at the smart data for the individual drives?

But yes when writing takes that long you certainly have a bad drive in there.  You an get a status of each device

I'll assume your using mdadm and the device is md127 but could be md0

mdadm --detail /dev/md127

If you use dmraid I would just refer the the individual components and look at the smart data in the Disk Utility.  If one is bad you will need to remove it.

You will need to sync but only if you have a backup.  There is a much faster way when you create the array like you did, use --assume-clean option.  

I have a 2TB mirror setup so I don't have day it would take to sync.  I copied the data to a separate disk.  using cp -Rfp /media/raid /media/backup.

Then I created the array using everything typical for my devices but included --assume-clean
Then I formatted the 2TB raid with ext4.
Then I copied the data back into the newly mount array.

I was up in running in under two hours.  Sure beats all that extra time synchronising.

Thanks for the information. I did not know about the assume-clean option, as it definitely was a clean pair.

I remoted in to check on it (as I'm at work) and it seems to have reached 2000 K/min, so perhaps it was just a problem getting started.

I will see what kind of progress it has made when I get home. Based on the amount of time it is taking it may still be best to start it over with assume clean.

---

### Post by john newbuntu on 2010-09-20
Did you manage to check the speeds of the individual drives "sudo hdparm -Tt /dev/sde1" prior to array creation? Same with sdf1. and a lame question: are the drives running in UDMA mode?

---

### Post by Dillius on 2010-09-20
> **john newbuntu said:**
> Did you manage to check the speeds of the individual drives "sudo hdparm -Tt /dev/sde1" prior to array creation? Same with sdf1. and a lame question: are the drives running in UDMA mode?

The hdparm command is what I was looking for, I was completely ignorant of the console method to checking that information.

I am also fairly ignorant of UDMA mode.

---

### Post by Dillius on 2010-09-20
Everything seems to be fine when I restarted the creation and told it to assume clean. 

I am going to put some data I have backed up else wear on the drives and see how they hold up.

The only strange thing is when I restarted the system it changes the device name from /dev/md2 to /dev/md_d2. 

Also if I check /dev I see:

/dev/md_d2p1
/dev/md_d2p2
/dev/md_d2p3
/dev/md_d2p4

I'm not sure what this is about?

---

