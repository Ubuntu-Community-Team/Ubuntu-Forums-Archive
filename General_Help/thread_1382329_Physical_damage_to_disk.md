---
title: "Physical damage to disk"
date: 2010-01-15
forum: General Help
---

### Post by Feelin_froggy8877 on 2010-01-15
I apparently have a damaged hdd. Windows was installed and I used a gparted live disk to check things out. It right away reported the the disk has been damaged. Can I check and mark the bad sectors (fix) from within Linux? Or should I use a configuration diskette specifically for my hdd?

---

### Post by warfacegod on 2010-01-15
Your best option may be to replace the drive.

---

### Post by RedRat on 2010-01-15
> **Feelin_froggy8877 said:**
> I apparently have a damaged hdd. Windows was installed and I used a gparted live disk to check things out. It right away reported the the disk has been damaged. Can I check and mark the bad sectors (fix) from within Linux? Or should I use a configuration diskette specifically for my hdd?

well if you indeed have a damaged HD run, do not walk, to your local geek store and get a new disk! You can marke defects all right, but what caused the damage in the first place? If your drive is faulty and causing lost sectors it now becomes recovery time, your damaged disk might well be unreliable. I would buy a new HD, install Ubuntu or Windows on it and try to recover whatever you can from the old HD.

---

### Post by Feelin_froggy8877 on 2010-01-16
Well, The person I got the lappy from dropped it. I believe the bad sectors can just be marked as bad. But I'm having trouble running a fsck...
```
untu@ubuntu:~$ sudo fsck -pcfv /dev/sda
fsck from util-linux-ng 2.16
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda
/dev/sda: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>






```
And when I run  e2fsck -b 8193 /dev/sda I get the same error.

---

### Post by warfacegod on 2010-01-16
> **Feelin_froggy8877 said:**
> Well, The person I got the lappy from dropped it. I believe the bad sectors can just be marked as bad. But I'm having trouble running a fsck...

Trust me on this! Backup your important files ASAP. You will need to buy a new drive. There is no question on this it just a matter of time.

---

### Post by baddog144 on 2010-01-16
Methinks it's time to buy yourself a snazzy new disk, after salvaging what you can off that one :|

---

### Post by jamesisin on 2010-01-16
New drives are cheap.  Value your time and your data more.  Get a new drive and get everything you can off this one.

---

### Post by Feelin_froggy8877 on 2010-01-16
Guess I'll get myself a new hdd. Thanx for the input.

---

### Post by efflandt on 2010-01-16
Normally a drive reserves space to automatically exchange bad sectors with good ones transparently.  If you actually start seeing bad sectors, it is wise to replace the drive.  If BIOS during boot says "drive failure imminent" believe it.

Don't be surprised if you pick up a laptop drive box in the store and it feels empty (they seem light for the box size).  The only question is pata or sata.

My boss' grandson had an old Dell laptop that he apparently did not treat properly.  WinXP would not even boot into safe mode, to protect what data was left.  Gparted live CD refused touch it until Windows fixed it.  I was able to mount the drive, but trying to copy the user's home directory to USB hd from Linux CD choked to a halt before it even got to My Documents.  A new drive was quieter, faster (and bigger).

---

### Post by JoelOl75 on 2010-01-16
You can verify your hdd dying possible by installing smartmontools

sudo apt-get install smartmontools

then:

sudo smartctl -a /dev/sda

Will list its SMART data (errors, temp...)

Of course these can be taken with a grain of salt, but they can be helpful (Like non-corrected ecc errors)

If the drive is jacked up really bad, you can try Steve Gibsond Spinrite [http://grc.com](http://grc.com) to try to recover data.  Otherwise just backup and get a new drive.  I wouldn't trust it at this point.

---

