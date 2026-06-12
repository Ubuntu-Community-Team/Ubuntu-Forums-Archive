---
title: "Unable To Boot After Update"
date: 2011-03-03
forum: General Help
---

### Post by Jamesbug92 on 2011-03-03
Hi All Im New To The Forum And Running Ubuntu 10.10
 
I Had The Update Box Come Up Last Night I Installed The Updates.
 
I Re-Booted The System And Now It Is Unable To Boot.
 
I Have Tryed The CTRL+ALT+F4 But That Didn't Work 
 
I Have Also Tried Backing Up The Data Using Puppy Linux But It Couldn't Mount The Partition.
 
When Booted It Comes Up With:
 
Mount:mounting/devon/root/dev failed: no such file or directory 
Mount:mounting/sys on/root/sys failed: no such file or directory 
Mount:mounting/Proc on/root/proc failed: no such file or directory
Target system doesn'y have requested/sbin/init 
no init found. Try passing init=bootarg
 
Any Ideas To Fix This 
Thanks
James

---

### Post by sikander3786 on 2011-03-03
Welcome to the forums :-)

We need you to boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us see what is going wrong with your boot and thus we might be able to help you.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes as this will be a long output.

---

### Post by Jamesbug92 on 2011-03-03
```

```    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,399,998   104,398,847     1,998,850   5 Extended
/dev/sda5         102,400,000   104,398,847     1,998,848  82 Linux swap / Solaris
/dev/sda3         104,398,848   976,771,071   872,372,224  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8A0C32F00C32D743                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        dbc2535d-83a7-4a8d-9472-92c0f80a381f   ext4                                     
/dev/sda5        2bc6997b-bf32-4f4c-aea7-caa8888c0b6c   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff 
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by sikander3786 on 2011-03-03
This doesn't sound good at all.

> sda3: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
[COLOR="Red"]Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
missing codepage or helper program, or other error[/COLOR]
In some cases useful info is found in syslog - try
dmesg | tail or so

That is why you are getting that error. I have requested some experienced members to take a look at your problem so please hang in there for a while.

I hope your problems will be solved soon.

---

### Post by Jamesbug92 on 2011-03-03
Thats What I was thinking when i saw it
 
Cheers For The Help


James

---

### Post by Veld on 2011-03-03
I have a similar problem, except I don't see an error message.

[http://ubuntuforums.org/showthread.php?t=1698139]("http://ubuntuforums.org/showthread.php?t=1698139")

---

### Post by sikander3786 on 2011-03-04
@ Jamesbug92:

As there haven't been replies so far from other member, I would recommend to run fsck from a Live CD in the mean time.

Boot an Ubuntu Live CD/USB and while the partitions are not mounted, run this command from Terminal.

```
sudo fsck -f /dev/sda3
```

Fix the errors if any and reboot and see if there is any improvement.

---

### Post by colmeweb on 2011-03-04
If you are using a wubi install you might find a solution here:

[http://ubuntuforums.org/showthread.php?t=1628560](http://ubuntuforums.org/showthread.php?t=1628560)

Warning: you will have to apply this fix after ever update.

---

### Post by Rubi1200 on 2011-03-04
As sikander3786 suggested, you can try and run a file-system check on the unmounted partition.

If that does not work or you have difficulties running the Ubuntu LiveCD, then download and burn to CD another Linux distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Use it to boot the computer and then, if it works, report back here so we can advise you further.

@colmeweb: you are giving out outdated information. There is now a permanent solution to the Wubi breakages you refer to.

See here for more:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Jamesbug92 on 2011-03-04
sikander3786

```

```Error reading block 54034557 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>?```

```

That Is What It Came Up With In Terminal 

Rubi1200

I Will Try That Now 

Cheers James

---

### Post by Jamesbug92 on 2011-03-04
Rubi1200


Slax Boots Up Fine But It Still Can Not Mount The HDD With An Error Message

```

```
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

---

### Post by Rubi1200 on 2011-03-04
Hi Jamesbug92,
make sure the partition is unmounted and then try the following command:

```
e2fsck -C0 -p -f -v /dev/sda3
```
If this reports errors (most likely), then run this command next:

```
e2fsck -f -y -v /dev/sda3
```
If this works and no errors are reported along the way, then you should hopefully be able to reboot and get back in.

If this does not work, please try and copy the exact error messages to post back here.

Thanks.

---

### Post by Jamesbug92 on 2011-03-04
Worked, Booted Up First Time

Thanks For The Help, I Fought I Was Going To Have To Re-install And Loose Everything.

Chears 

James 
:P

---

### Post by Rubi1200 on 2011-03-04
> **Jamesbug92 said:**
> Worked, Booted Up First Time

Thanks For The Help, I Fought I Was Going To Have To Re-install And Loose Everything.

Chears 

James 
:P
No problem, you are more than welcome :-)

Glad you got things sorted out.

---

### Post by Jamesbug92 on 2011-03-17
Hi Again 

I Have Had The Same Problem Again (solved) But I Was Wondering What Creates This Problem? Is It A Hardware Problem?

Thanks
James

---

### Post by Rubi1200 on 2011-03-17
> **Jamesbug92 said:**
> Hi Again 

I Have Had The Same Problem Again (solved) But I Was Wondering What Creates This Problem? Is It A Hardware Problem?

Thanks
James
Are you hard resetting, using hibernate, overclocking; anything like that?

On the LiveCD or in Ubuntu go to System > Administration > Disk Utility and check the health of the hard-drive via SMART data.

You want to see green ;)

Check particularly these sections:

Reallocated Sector Count
Reallocation Count
Current Pending Sector Count
Uncorrectable Sector Count

---

### Post by Jamesbug92 on 2011-03-17
Reallocated Sector Count - Good 
Reallocation Count - Didn't Come Up
Current Pending Sector Count - Warning 
Uncorrectable Sector Count - N/A

Don't Think That Sounds Good :(
Its A Month Old HDD

Thanks 

James

---

### Post by Rubi1200 on 2011-03-18
Hi,
If > Reallocated Sector Count - Good  then you may have some time still. I recommend you make full backups in any event and be prepared for the possibility that there might be a hardware failure.

The other thing I can think of that might be worth investigating is whether this was caused by faulty RAM.

You can run memtest from the LiveCD; leave it for a few hours and see what it comes up with.

---

### Post by Jamesbug92 on 2011-03-18
Memory Test Came Up Clean. 

Might Be Time To Bite The Bullet and Build a New Computer 

Thanks For The Help 

James

---

