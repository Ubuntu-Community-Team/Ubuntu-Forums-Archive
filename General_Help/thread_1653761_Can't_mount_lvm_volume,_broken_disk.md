---
title: "Can't mount lvm volume, broken disk?"
date: 2010-12-27
forum: General Help
---

### Post by jake_swe on 2010-12-27
Hi! I suspect that one of the disks is broken in my lvm setup. I need help verifying this. The only trouble is that everything looks okay in my eyes.

When i try to mount the logical partition. The system hangs. 
"mount /dev/fileserver/media /var/media"

I have tried locating the problem without success. The same with a live cd.

Here are some of the commands i have run:
[http://pastebin.com/gYyJtUvQ]("http://pastebin.com/gYyJtUvQ")


I need help with understanding what is wrong and hopefully save some of the data if possible.

/Jake

---

### Post by psusi on 2010-12-27
Open the disk utility and look at the SMART values for the drive.  Also could you translate what the output of fsck was?

---

### Post by jake_swe on 2010-12-27
Here is a translation of fsck.

Unit or resourse is busy when trying to open
/dev/fileserver/media
Is filesystem mounted or used exclusivly by an other program?

Here is what smart gives me while running from live cd:[http://pastebin.com/nLeXnaFb]("http://pastebin.com/nLeXnaFb")
logged in this order: sda sdb sdc sdd sde sdf sdg sdh

---

### Post by psusi on 2010-12-27
Looks like there isn't anything wrong with the disks.  Are you getting any errors in your kernel log?

---

### Post by jake_swe on 2010-12-27
I find a few of these when i do "cat kern.log | grep error":

Dec 27 23:29:14 ubuntuServer kernel: [   10.988947] EXT4-fs warning (device dm-0): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure

And some looks like this:

Dec 27 23:29:25 ubuntuServer kernel: [   45.345837] tda18271_powerscan: [0-00c0|M] error -1 on line 507
Dec 27 23:29:25 ubuntuServer kernel: [   45.345842] tda18271_rf_tracking_filters_init: [0-00c0|M] error -1 on line 602
Dec 27 23:29:25 ubuntuServer kernel: [   45.345846] tda18271_calc_rf_filter_curve: [0-00c0|M] error -1 on line 662
Dec 27 23:29:25 ubuntuServer kernel: [   45.345851] tda18271c2_rf_cal_init: [0-00c0|M] error -1 on line 687

---

### Post by psusi on 2010-12-27
You need to unmount the fs and fsck it.

---

### Post by jake_swe on 2010-12-28
The problem is that the fsck output was while i used a live cd and the fs was not mounted. :S

---

### Post by psusi on 2010-12-28
Did you install the lvm2 package and activate the volume?

---

### Post by jake_swe on 2010-12-28
Yes. What do you think, is the ext4 corrupted in some way?

Edit!

I successfully checked the file system. I turned out that trying to mount the disk made it unable to check it. An thus making fsck fail. So the procedure was merly:

boot live cd
terminal:
sudo -s
apt-get install lvm2
fsck.ext4 /dev/fileserver/media


The check is currently running. Seams like everything will turn out fine.
Thank you psusi!

---

