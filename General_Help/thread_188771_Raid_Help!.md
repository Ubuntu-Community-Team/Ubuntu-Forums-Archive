---
title: "Raid Help!"
date: 2006-06-04
forum: General Help
---

### Post by malkaven on 2006-06-04
Hello all,

I have a brand new xeon server and im trying to get Ubuntu 6.06 installed.  During the setup I configure a raid 0, I have 2 250 gig drives.  The setup continues and formats and partitions the raid.  The setup will install all of the base files.

Once the setup gets to trying to install grub it fails.  I assume this is normal because grub does not know how to install on a raid.  I found this HowTo
 [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

But I really dont know where to start.  Alot of it doesnt look like it applies.  I can even tell the install to finish without the bootloader and it will.

---

### Post by malkaven on 2006-06-04
any suggestion?  I tried reinstalling using the essentials disk as well.  That did not give me any other options

---

### Post by cgjones on 2006-06-05
The server doesn't have hardware RAID?

---

### Post by JoWilly on 2006-06-05
So if you don't have a hardwareraid, do you have a fakeraid (I don't think so if it is a server) or are you trying to setup a linux raid with the installer ?

If it's a linux raid, you can have the root partition in raid 0, but you will need the boot partition to install grub and the kernel images.

Here is what I usually do if I have 2 drives:

HD1: 
partition1: 500Mb /boot (you need about min 100Mb, I put 500 to leave the same space for the raid part on each disk and I don't want less that 500MB swap)
Partition2: XXXXMb raid

HD2:
partition1: 500Mb swap
partition2: XXXXMb raid

(the 2 raid parts must be the same size).

Then, make the raid0 with the 2 raid partitions. Raid0 will be /.

This way, grub boots into /boot to start the kernel and then loads root on the raid0.

---

### Post by juicybananahead on 2006-06-06
I can't remember where I read this but I think that the only RAID device that can be booted from is of type RAID 1. As JoWilly suggests, keep your /boot partition separate (either mounted on a non-RAID or RAID 1 device) and mount your / partion on a RAID 0 device. Be warned about keeping your root filesystem on RAID 0 however, if one of your drives fails you lose everything!

// juicy

---

### Post by malkaven on 2006-06-06
No this is a "personal" server so its a fakeraid.  I'm using the raid controller on the motherboard.

JoWilly- Thanks ill try installing that way.  Are you using breezey or dapper?  If dapper what disc? Alt, server or workstation, did you use?

---

### Post by malkaven on 2006-06-06
Was thinking, since I formatted like at least like 20 times, GRUB is in my mbr,  If i make a seperate /boot partition it will overwrite that mbr correct? 

Last night I installed dapper and the same problem happened with grub.  For the heck of it I installed breezey and it installed perfectly using 1 single disk no raid.  But when the grub menu popped up it found dapper too and dapper started correctly when selected.  

Is it possible that grub is corrupt in my mbr and just not reading the /boot partition?  Or does the /boot partition just become the MBR?

---

### Post by juicybananahead on 2006-06-06
Sorry Malkaven, I assumed you were running software RAID (mdadm). I'm not sure how you'd move forward with fakeraid.

---

### Post by malkaven on 2006-06-07
Somewhat solved.  I partitioned the drives exactly like jowood said and it worked.  It did not work with dapper, grub just doesnt go in properly or something.  With breezey I had no issues.

After I had breezey running I upgraded to dapper.  Dapper doesnt like the /boot ext3 partition and dumps me to a shell but it lets me continue to load by pressing ctrl D.  Ill tackle that issue later tho im just glad to have an os installed finaly.

If anyone else comes accross this just follow the same partition scheme JoWilly posted in breezys setup. I did not have my raid setup in the BIOS.  

Thanks for the help all.=D>

---

### Post by Ocxic on 2006-06-07
[QUOTE=JoWilly]
Here is what I usually do if I have 2 drives:

HD1: 
partition1: 500Mb /boot (you need about min 100Mb, I put 500 to leave the same space for the raid part on each disk and I don't want less that 500MB swap)
Partition2: XXXXMb raid

HD2:
partition1: 500Mb swap
partition2: XXXXMb raid

(the 2 raid parts must be the same size).

Then, make the raid0 with the 2 raid partitions. Raid0 will be /.

This way, grub boots into /boot to start the kernel and then loads root on the raid0.[/QUOTE]

I've done exactly this with raid, and LVM. I find LVM better as you can name your partitions, and it's simpler then RAID.

---

