---
title: "I can not autostart and automount software RAID"
date: 2009-11-03
forum: General Help
---

### Post by Rune Hagen on 2009-11-03
On Karmic Koala (0910) 64bit.

I have put together a media server for my home and have made a 4 disk raid 5 with mdadm (Disk utility).

I have gotten samba to start at boot, but...
How can I get the raid to assemble/start and mount at boot?
It works fine once I am logged into terminal using:
sudo mdadm -A /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
It asks for my password and then starts up fine.
And I must also mount it manually, and once again it asks for my password.

It would be great if everything would start at boot without the manual fooling around :)

Anyone have any idea?

---

### Post by sux2bu101 on 2009-11-03
I am also am looking for a similar solution....

---

### Post by Micha0365 on 2009-12-13
I had the same problem after updating from 8.1 to 9.04 (and then to 9.1)

For some (stupid ?) reason Ubuntu Server only starts those arrays automaticly, that are listet in the /etc/mdadm/mdadm.conf

If your array is already properly configured, the easiest way to get it started automaticly is the following:

# Let exisiting arrays be detected and started
sudo mdadm --auto-detect

# Find out the UUID of the array(s) you want to be started automaticly
sudo mdadm --detail --scan

The output will look something like this (depending on your arrays):
[I]mdadm: md device /dev/md/d0 does not appear to be active.
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=02a3fb05:e090a494:1b1a320b:21b9bdd9
[/I]
Now mark and copy (or write down) the "UUID= ..." of the array(s) you want to start

Edit your /etc/mdadm/mdadm.conf  and add the following line(s):

# definitions of existing MD arrays (put the UUID of YOUR array here...)
ARRAY /dev/md0 UUID=02a3fb05:e090a494:1b1a320b:21b9bdd9

Save the file.
Reboot.
-> The raid array(s) should be up and running
-> If it is included in the /etc/fstab it should also be mounted

Regards,

Michael

---

### Post by Rune Hagen on 2009-12-14
Thanks Michael
That would explain my troubles :D
I did put it in the /etc/fstab, but the array did not start, so it didn't mount either :(

I have solved it though by reinstalling and configuring the raid during the install, not something you would want for an upgrade though :|

---

### Post by samcoinc on 2009-12-16
Don't forget to make the /media/data directory also

sudo mkdir /media/data

sam

(that bit me this morning.) This thread got be 'almost' there. :)

---

### Post by MarylandTechs on 2009-12-27
this thread saved me, thank you
 
I don't understand why this is not automated especially when you use a gui to create the raid

---

### Post by JohnYYC on 2010-01-27
> **Micha0365 said:**
> I had the same problem after updating from 8.1 to 9.04 (and then to 9.1)

For some (stupid ?) reason Ubuntu Server only starts those arrays automaticly, that are listet in the /etc/mdadm/mdadm.conf

If your array is already properly configured, the easiest way to get it started automaticly is the following:

# Let exisiting arrays be detected and started
sudo mdadm --auto-detect

# Find out the UUID of the array(s) you want to be started automaticly
sudo mdadm --detail --scan

The output will look something like this (depending on your arrays):
[I]mdadm: md device /dev/md/d0 does not appear to be active.
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=02a3fb05:e090a494:1b1a320b:21b9bdd9
[/I]
Now mark and copy (or write down) the "UUID= ..." of the array(s) you want to start

Edit your /etc/mdadm/mdadm.conf  and add the following line(s):

# definitions of existing MD arrays (put the UUID of YOUR array here...)
ARRAY /dev/md0 UUID=02a3fb05:e090a494:1b1a320b:21b9bdd9

Save the file.
Reboot.
-> The raid array(s) should be up and running
-> If it is included in the /etc/fstab it should also be mounted

Regards,

Michael



Would these commands also work in Ubuntu 9.10 Desktop? I just don't want to screw up my system if I can help it.

Cheers,

John

---

### Post by Rune Hagen on 2010-01-28
I was using the desktop "edition" for this, and it worked for me (after all the good tips here).
I also tried Fedora 12, and it's the exact same problem there, and I guess the same fix.

---

### Post by JohnYYC on 2010-01-28
> **Rune Hagen said:**
> I was using the desktop "edition" for this, and it worked for me (after all the good tips here).
I also tried Fedora 12, and it's the exact same problem there, and I guess the same fix.

Thank you for the confirmation! My RAIDs now auto start and auto mont.

Cheers,

John

---

