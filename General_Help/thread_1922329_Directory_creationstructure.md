---
title: "Directory creation/structure"
date: 2012-02-08
forum: General Help
---

### Post by dkolars on 2012-02-08
Trying to figure out the behavior of Linux...  my cell phone has an id #... format is:  9999-9999...  so, I created a sub-dir in /media named 9999-9999...  When I plug my phone in, Linux creates the directory 9999-9999_  for the phone (underscore after the number)...  IF I unplug the phone, that directory disappears.  If I create the directory 9999-9999_ and plug in the phone, Linux now creates a new directory, 9999-9999__  with 2 underscores...  WTH?

---

### Post by LewisTM on 2012-02-08
Ubuntu (not Linux per se) automatically creates a directory in /media for removable devices and mounts the filesystem in it. It uses the volume label or other ID from the fs for the new directory's name. This directory gets removed once the device is disconnected so as not to pollute your /media.

It's also playing nice with you and of course won't overwrite a personal directory that YOU created in /media and that might contain important files. So in that event it just creates a dir with an extra underscore.

Makes sense?

Cheers!

---

### Post by jamesisin on 2012-02-08
What LewisTM writes is correct.  There should be no reason to create that folder yourself.  What are you trying to accomplish and maybe we can help with that as well?

---

### Post by dkolars on 2012-02-08
Well, I was told via a message that I should create directories for all the media.  SOMETIMES, Ubuntu ~uses~ the directory I have created, sometimes not...  Right now I can see HD7 (that I created and that HAS been used by Ubuntu) but it is empty/not accessible/etc.  HD7 is mounted on HD7_  the Ubuntu-created directory.  There has never been any rhyme or reason that I can see why it does what it does... there's a 50-50 chance that ANY drive. other than the boot drive, will be mounted in an Ubuntu-created directory, named the same as the one referenced in the fstab file, only with an underscore added; i.e., HD2_, HD3_, etc.

In almost 3 yrs. of using Linux this has always been the case for me.  Drives me nuts!!  I have 2 internal HDD's and 5 external, USB HDD's...  plus Android, USB sticks, etc.  I'd just like it to be consistent for a change!!

---

### Post by LewisTM on 2012-02-09
I think unless you have very specific needs for them, you should let Ubuntu handle automounting of USB-connected drives and not have fstab entries for them. Those are for internal or at the least permanently attached drives. Expect more consistency that way.

Ubuntu likes to manage USB stuff. You could play around with udev rules but that is beyond my expertise.

---

### Post by dkolars on 2012-02-09
I don't like the way Ubuntu manages HDD's!!!  OK, I commented out ALL the HDD's in my fstab file ~except~ HD1 & HD2 (internal drives).

Re-boot...  HD2 not mounted by boot process...  must mount either via Terminal or Disk Utility.  Since I have a sub-directory in my /media directory, Ubuntu now calls HD2, HD2_

Delete the HD2 sub-dir in /media, re-boot, and now HD2 is found under HD2.  As it should be, you say?  Well, I think so as well...

NOW, I turn on HD6, external 1.5 TB drive.  It mounts at, no surprise, HD6_ -- since I have a sub-dir named HD6 in /media.  OK, what I expected.  

BUT, using Krusader (double-pane file mgr.) I can open HD6_ and see the contents, but instead of getting a message telling me that "only root can mount UUID blah-blah", I can see the contents of HD6 as well...  So, I now have TWO instances of HD6 in existence.  

Next step is to delete all sub-directories above HD2 in /media, and hope that this will "tidy things up"...

Also, when booting (a problem forever, for me), I will get many instances of "flush-9:9" running... this last boot-up was 27 instances... when I click on "Re-Start", they stop running, then I can cancel the re-boot and all seems to be ok... IF they do not stop, both processors are then running at 100% (or close to it), and the program bar does not show minimized programs, as it is full of little dots for all the instances of "flush"....  Pain in keester... sometimes 3 or 4 re-boots are required to get the system to run as it should.

Back to the grind...

---

### Post by dkolars on 2012-02-12
New system up and running...  HD1 & HD2, internal HDD's.

5 external drves, HD3 - HD7... .HD 5 is a brand new Seagate 1.5Tb drive.  

I eliminated all references to external drives in my fstab file, so Ubuntu mounts them on start-up...  All was going well, but today, HD5 started acting funky.  I formatted it to ext4, 1 large partition.  

Since 8 pm, 3 hrs. ago, Ubuntu has re-mounted that drive 11 times.  So, looking at my desktop, I have 12 icons for HD5.  Looking at the /media dir in Krusader, I have:

HD5
HD5_
HD5__
HD5___
HD5____
etc. thru
HD___________

It was originally mounted on HD5, and that opens, but shows empty drive.  HD5_ likewise opens, shows empty.  But, HD5__ (two underscores) can't be opened.  Likewise HD5____ (3 underscores).  HD5_____ (4 underscores) opens, says empty... etc. etc.  The last two open and show the contents of the drive.  

I did have all my externals mounting via fstab, but that caused a lot of grief when I tried to move everything to the new computer, so as per a suggestion, I commented out all but internal drives.  

I was gone last night, system on... got home today to find 22 instances of HD5 listed!

WTH????  Tonight I unplug the drive!!  Any clue why this is happening?  First Ubuntu won't mount drives, and now it's re-mounting one over and over... karma?  Does it keep count of how many times it missed mounting drives and is now making up for it?  Yin & Yang??  :D  Very strange...

---

### Post by Paqman on 2012-02-12
> **dkolars said:**
> Well, I was told via a message that I should create directories for all the media.

Sort of correct. Anything that you mount explicitly in fstab (such as internal drives or network shares) should have a mount point created for it, but USB devices will create their own mount point in /media as soon as they're plugged in.

Can you post up a copy of your fstab?

---

### Post by dkolars on 2012-02-12
Here's my fstab:

> proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=bb687805-94d4-46de-8bd8-8d4c772848d8 none swap sw 0 0
#/dev/sdb1 = HD2
UUID=72ac82d9-dcb8-4a9a-8f9b-29826c56634f /media/HD2 ext4 defaults,errors=remount-ro,noatime 0 1
# Entry for CD/DVD drive
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0


As I say, I USED to have my USB drives in the fstab, now it's only the 2 internal HDD's and the CD/DVD ROM that are listed.

Here's what happens when I unplug the drive, both power and USB, then go to terminal and attempt to remove the HD5  directories from the /media dir:

> dkolars@Desktop:/media$ sudo rm -r HD5_
rm: cannot remove `HD5_': Device or resource busy

I was able to delete the original HD5 and HD5_ _ , but NONE of the rest!!

Will be doing a reboot with the HD5 unplugged...

OK, re-booted.  Ubuntu did not mount any external HDD's?  The last 3-4 re-starts, it HAS mounted them on boot-up???   So, plugged in HD5.  Ubuntu mounted it immediately... twice:  HD5 & HD5_.  So, I unmounted 5_ via terminal, deleted it via root-mode Krusader...  now we wait and see if HD5 gets remounted again!!

---

### Post by jamesisin on 2012-02-12
Those automatically created directories (like HD5_) will delete themselves when the drive is fully unmounted.  Only those folders you manually create (using sudo) will remain in /media/.

None of the machines I looked at have an entry for the CD drive, in case that matters.

---

### Post by dkolars on 2012-02-12
> Those automatically created directories (like HD5_) will delete themselves when the drive is fully unmounted. Only those folders you manually create (using sudo) will remain in /media/.

We'll see...  of course, when I had them in fstab, they stayed.

After my last posting where I deleted the HD5_, it is now back, and I can access that drive from both HD5 & HD5_ directories.  I use Krusader (2-pane file manager).

I don't like this.  I'm sure that within a few minutes, another window will pop up notifying me of HD5 _ _ being created, and very likely a 2nd window with a message that says it can't be mounted.  Just a guess, mind you, but I just got a feelin'.

Oh, one other thing... the time stamp for the HD5_ is the same as the original HD5.

---

### Post by dkolars on 2012-02-12
Yep, now have 2 more HD5's... total of 4 now.  So, 2 new ones in 12 minutes...  very strange.

---

### Post by jamesisin on 2012-02-12
With these additional HD5's could you post the output from ls -al /media?

---

### Post by dkolars on 2012-02-12
Here's the output... there are 2 more since the last message!!  Up to 9 now...


> dkolars@Desktop:~$ ls -al /media
total 84
drwxr-xr-x 18 root    root  4096 2012-02-12 02:28 .
drwxr-xr-x 25 root    root  4096 2012-02-11 22:28 ..
drwxr-xr-x  2 root    root  4096 2009-06-30 09:39 cdrom0
-rw-r--r--  1 root    root  2169 2012-02-12 02:28 .hal-mtab
-rw-------  1 root    root     0 2012-02-12 00:01 .hal-mtab-lock
drwxr-xr-x  2 root    root  4096 2010-12-11 17:54 HD1
drwx------  8 dkolars root  4096 2012-02-10 14:19 HD2
drwx------  1 dkolars root  4096 2011-12-10 21:26 HD3
drwx------  1 dkolars root 12288 2012-02-10 07:41 HD4
drwx------  3 dkolars root  4096 2012-02-11 18:40 HD5
drwx------  2 root    root  4096 2012-02-12 00:28 HD5_
drwx------  3 dkolars root  4096 2012-02-11 18:40 HD5__
drwx------  2 root    root  4096 2012-02-12 00:58 HD5___
drwx------  2 root    root  4096 2012-02-12 01:28 HD5____
drwx------  3 dkolars root  4096 2012-02-11 18:40 HD5_____
drwx------  2 root    root  4096 2012-02-12 01:58 HD5______
drwx------  3 dkolars root  4096 2012-02-11 18:40 HD5_______
drwx------  3 dkolars root  4096 2012-02-11 18:40 HD5________
drwx------ 17 dkolars root  4096 2012-02-10 14:19 HD6
drwx------  5 dkolars root  4096 2012-02-10 01:09 HD7

---

### Post by jamesisin on 2012-02-12
I am a little confused by your permissions.  When I attach a USB drive to my system it shows up as me:me; when I connect a network drive (via fstab) it appears as root:root.  Yet your USB connected drives (not via fstab) are showing as dkolars:root while that renegade number-5-is-alive is showing as root:root.  I wonder if this is an interesting clue to the matter?

---

### Post by dkolars on 2012-02-12
Yes, I too noticed that... had to go into Chicago today, and when I came home tonight found only 18 HD5's listed!!  :D

So, unmounted the drive, deleted all the HD5 sub-dirs, and changed permissions to be read/write for everybody.  Now the output of ls -al /media shows;


> dkolars@Desktop:~$ ls -al /media
total 116
drwxr-xr-x 12 root    root  4096 2012-02-12 22:20 .
drwxr-xr-x 25 root    root  4096 2012-02-11 22:28 ..
drwxr-xr-x 44 dkolars root 32768 1969-12-31 18:00 6561-xxxx
drwxr-xr-x  2 root    root  4096 2009-06-30 09:39 cdrom0
-rw-r--r--  1 root    root  2397 2012-02-12 22:19 .hal-mtab
-rw-------  1 root    root     0 2012-02-12 10:56 .hal-mtab-lock
drwxr-xr-x  2 root    root  4096 2010-12-11 17:54 HD1
drwx------ 21 dkolars root  4096 2012-02-12 04:01 HD2
drwx------  1 dkolars root  4096 2011-12-10 21:26 HD3
drwx------  1 dkolars root 12288 2012-02-12 10:33 HD4
drwxrwxrwx  3 dkolars root  4096 2012-02-11 18:40 HD5
drwx------ 13 dkolars root  4096 2012-02-12 12:21 HD6
drwx------  5 dkolars root  4096 2012-02-10 01:09 HD7
drwxr-xr-x 44 dkolars root 32768 1969-12-31 18:00 ?PNG?


Looks much nicer!  6561-xxxx & ?PNG? are my cell phone.  Double entry for ?? reason, but I'm not too worried about that!!  We'll see if the permissions stick and the problem goes away...  thanks...  dk

---

### Post by dkolars on 2012-02-13
Well, no difference...  Seems as tho' after 30 mins. Ubuntu mounts HD5...  I noticed that time frame last night, and it just happened again.  I now have HD5 & HD5_

Can access both, but when the next one is created, HD5 will only show "..", I won't be able to access HD5_, and the HD5_ _ will have the 2 files I copied there to monitor the drive.  Then, when HD5 _ _ _ is created, I'll again be able to see the contents in the last 2 drives, and the HD5_ will show the ".."

Sumting not working right!!  Starting to be not funny... :x

---

### Post by efflandt on 2012-02-13
Does **dmesg** or **/var/log/syslog** give any clue about drive problems or why it gets mounted repeatedly?

It is still curious why external drives automount in your name instead of root root. Are you running some secondary automount other than, or in addition to, the one automatically on the system?

---

### Post by dkolars on 2012-02-13
Not sure about "other automount"...  I have the drives commented out in fstab... where else would they be mounted from?

I now, in 2 hrs., have 8 incarnations of HD5...

Here's the end part of the /var/log/syslog file --  "sdk1" is HD5... lots of ERROR & WARN...  "sdj1" does not exist in the Disk Utility list of connected drives...  Also, Ubuntu mounted the external drives as "sdc1", "sdd1", "sdf1", "sdg1", & "sdk1"... skipped e, h, i, j...  says "running e2fsck is recommended"... I Googled that, and am not going attempt that at 1:30 a.m.!!

I note that this occurs:  "forcibly attempting to lazy unmount /dev/sdk1 as enclosing drive was disconnected"...  Does that message mean what it says, that the drive was disconnected?  Is it possible that the drive is faulty?  Bad cable?  I have not disconnected or messed with any connections...  Will investigate further after some shuteye!!


> 
Feb 12 23:56:46 Desktop kernel: [48645.007562] scsi 41:0:0:0: Direct-Access     Seagate  FA GoFlex Desk   0157 PQ: 0 ANSI: 4
Feb 12 23:56:46 Desktop kernel: [48645.008596] sd 41:0:0:0: Attached scsi generic sg5 type 0
Feb 12 23:56:46 Desktop kernel: [48645.008722] sd 41:0:0:0: [sdk] 2930277167 512-byte logical blocks: (1.50 TB/1.36 TiB)
Feb 12 23:56:46 Desktop kernel: [48645.009124] sd 41:0:0:0: [sdk] Write Protect is off
Feb 12 23:56:46 Desktop kernel: [48645.009130] sd 41:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Feb 12 23:56:46 Desktop kernel: [48645.009135] sd 41:0:0:0: [sdk] Assuming drive cache: write through
Feb 12 23:56:46 Desktop kernel: [48645.016521] sd 41:0:0:0: [sdk] Assuming drive cache: write through
Feb 12 23:56:46 Desktop kernel: [48645.016532]  sdk: sdk1
Feb 12 23:56:46 Desktop kernel: [48645.040926] sd 41:0:0:0: [sdk] Assuming drive cache: write through
Feb 12 23:56:46 Desktop kernel: [48645.040935] sd 41:0:0:0: [sdk] Attached SCSI disk
Feb 12 23:56:46 Desktop kernel: [48645.299708] EXT4-fs error (device sdj1): ext4_find_entry: inode #2: (comm Thunar) reading directory lblock 0
Feb 12 23:56:46 Desktop kernel: [48645.299780] EXT4-fs error (device sdj1): ext4_find_entry: inode #2: (comm Thunar) reading directory lblock 0
Feb 12 23:56:46 Desktop kernel: [48645.299789] EXT4-fs (sdj1): previous I/O error to superblock detected
Feb 12 23:56:46 Desktop kernel: [48645.446418] EXT4-fs (sdk1): warning: maximal mount count reached, running e2fsck is recommended
Feb 12 23:56:47 Desktop kernel: [48645.572202] EXT4-fs (sdk1): recovery complete
Feb 12 23:56:47 Desktop kernel: [48645.572207] EXT4-fs (sdk1): mounted filesystem with ordered data mode. Opts: (null)
Feb 12 23:56:47 Desktop hald: mounted /dev/sdk1 on behalf of uid 1000
Feb 13 00:09:17 Desktop kernel: [49396.176989] usb 2-4.4: new high speed USB device using ehci_hcd and address 7
Feb 13 00:09:17 Desktop kernel: [49396.283525] scsi42 : usb-storage 2-4.4:1.0
Feb 13 00:09:18 Desktop kernel: [49397.284600] scsi 42:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
Feb 13 00:09:18 Desktop kernel: [49397.285582] sd 42:0:0:0: Attached scsi generic sg11 type 0
Feb 13 00:09:18 Desktop kernel: [49397.293439] sd 42:0:0:0: [sdl] Attached SCSI removable disk
Feb 13 00:09:24 Desktop kernel: [49402.888560] usb 2-4.4: USB disconnect, address 7
Feb 13 00:17:01 Desktop CRON[17009]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 13 00:26:36 Desktop kernel: [50434.650863] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:26:36 Desktop kernel: [50434.651897] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:26:36 Desktop kernel: [50434.668403] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:26:36 Desktop kernel: [50434.763485] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:26:36 Desktop kernel: [50434.799864] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:26:43 Desktop kernel: [50442.040769] usb 8-3.3: reset high speed USB device using xhci_hcd and address 6
Feb 13 00:26:43 Desktop kernel: [50442.040857] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:26:43 Desktop kernel: [50442.244187] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:26:43 Desktop kernel: [50442.448531] usb 8-3.3: device not accepting address 6, error -22
Feb 13 00:26:44 Desktop kernel: [50442.520417] usb 8-3.3: reset high speed USB device using xhci_hcd and address 6
Feb 13 00:26:44 Desktop kernel: [50442.520504] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:26:44 Desktop kernel: [50442.728172] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:26:44 Desktop kernel: [50442.928035] usb 8-3.3: device not accepting address 6, error -22
Feb 13 00:26:44 Desktop kernel: [50443.000440] usb 8-3.3: reset high speed USB device using xhci_hcd and address 6
Feb 13 00:26:44 Desktop kernel: [50443.000512] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:26:44 Desktop kernel: [50443.204185] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:26:44 Desktop kernel: [50443.408309] usb 8-3.3: device not accepting address 6, error -22
Feb 13 00:26:44 Desktop kernel: [50443.480988] usb 8-3.3: reset high speed USB device using xhci_hcd and address 6
Feb 13 00:26:44 Desktop kernel: [50443.481075] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:26:45 Desktop kernel: [50443.684262] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:26:45 Desktop kernel: [50443.888135] usb 8-3.3: device not accepting address 6, error -22
Feb 13 00:26:45 Desktop kernel: [50443.888708] sd 41:0:0:0: Device offlined - not ready after error recovery
Feb 13 00:26:45 Desktop kernel: [50443.889198] usb 8-3.3: USB disconnect, address 6
Feb 13 00:26:45 Desktop hald[2104]: forcibly attempting to lazy unmount /dev/sdk1 as enclosing drive was disconnected
Feb 13 00:26:45 Desktop hald: unmounted /dev/sdk1 from '/media/HD5_____' on behalf of uid 0
Feb 13 00:26:45 Desktop kernel: [50443.988398] usb 8-3.3: new high speed USB device using xhci_hcd and address 0
Feb 13 00:26:45 Desktop kernel: [50444.008867] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
Feb 13 00:26:45 Desktop kernel: [50444.009008] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
Feb 13 00:26:45 Desktop kernel: [50444.009103] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
Feb 13 00:26:45 Desktop kernel: [50444.009210] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
Feb 13 00:26:45 Desktop kernel: [50444.010572] scsi43 : usb-storage 8-3.3:1.0
Feb 13 00:26:46 Desktop kernel: [50445.010698] scsi 43:0:0:0: Direct-Access     Seagate  FA GoFlex Desk   0157 PQ: 0 ANSI: 4
Feb 13 00:26:46 Desktop kernel: [50445.011637] sd 43:0:0:0: Attached scsi generic sg5 type 0
Feb 13 00:26:46 Desktop kernel: [50445.012004] sd 43:0:0:0: [sdk] 2930277167 512-byte logical blocks: (1.50 TB/1.36 TiB)
Feb 13 00:26:46 Desktop kernel: [50445.012753] sd 43:0:0:0: [sdk] Write Protect is off
Feb 13 00:26:46 Desktop kernel: [50445.012762] sd 43:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Feb 13 00:26:46 Desktop kernel: [50445.012768] sd 43:0:0:0: [sdk] Assuming drive cache: write through
Feb 13 00:26:46 Desktop kernel: [50445.019279] sd 43:0:0:0: [sdk] Assuming drive cache: write through
Feb 13 00:26:46 Desktop kernel: [50445.019301]  sdk: sdk1
Feb 13 00:26:46 Desktop kernel: [50445.074311] sd 43:0:0:0: [sdk] Assuming drive cache: write through
Feb 13 00:26:46 Desktop kernel: [50445.074320] sd 43:0:0:0: [sdk] Attached SCSI disk
Feb 13 00:26:47 Desktop kernel: [50445.560740] EXT4-fs (sdk1): warning: maximal mount count reached, running e2fsck is recommended
Feb 13 00:26:47 Desktop kernel: [50445.684180] EXT4-fs (sdk1): recovery complete
Feb 13 00:26:47 Desktop kernel: [50445.684184] EXT4-fs (sdk1): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 00:26:47 Desktop hald: mounted /dev/sdk1 on behalf of uid 1000
Feb 13 00:47:57 Desktop kernel: [51715.941142] usb 2-4.4: new high speed USB device using ehci_hcd and address 8
Feb 13 00:47:57 Desktop kernel: [51716.046725] scsi44 : usb-storage 2-4.4:1.0
Feb 13 00:47:58 Desktop kernel: [51717.047449] scsi 44:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
Feb 13 00:47:58 Desktop kernel: [51717.048413] sd 44:0:0:0: Attached scsi generic sg11 type 0
Feb 13 00:47:58 Desktop kernel: [51717.055270] sd 44:0:0:0: [sdl] Attached SCSI removable disk
Feb 13 00:48:03 Desktop kernel: [51721.518306] sd 44:0:0:0: [sdl] 15523840 512-byte logical blocks: (7.94 GB/7.40 GiB)
Feb 13 00:48:03 Desktop kernel: [51721.520221] sd 44:0:0:0: [sdl] Assuming drive cache: write through
Feb 13 00:48:03 Desktop kernel: [51721.526354] sd 44:0:0:0: [sdl] Assuming drive cache: write through
Feb 13 00:48:03 Desktop kernel: [51721.526366]  sdl: sdl1
Feb 13 00:56:36 Desktop kernel: [52234.625186] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:56:36 Desktop kernel: [52234.626299] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:56:36 Desktop kernel: [52234.645542] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:56:36 Desktop kernel: [52234.740725] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:56:36 Desktop kernel: [52234.777031] xhci_hcd 0000:03:00.0: WARN: Stalled endpoint
Feb 13 00:56:43 Desktop kernel: [52242.056849] usb 8-3.3: reset high speed USB device using xhci_hcd and address 6
Feb 13 00:56:43 Desktop kernel: [52242.057004] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:56:43 Desktop kernel: [52242.260253] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:56:43 Desktop kernel: [52242.464015] usb 8-3.3: device not accepting address 6, error -22
Feb 13 00:56:44 Desktop kernel: [52242.537635] usb 8-3.3: reset high speed USB device using xhci_hcd and address 6
Feb 13 00:56:44 Desktop kernel: [52242.537702] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:56:44 Desktop kernel: [52242.740354] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:56:44 Desktop kernel: [52242.944021] usb 8-3.3: device not accepting address 6, error -22
Feb 13 00:56:44 Desktop kernel: [52243.020873] usb 8-3.3: reset high speed USB device using xhci_hcd and address 6
Feb 13 00:56:44 Desktop kernel: [52243.020953] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:56:44 Desktop kernel: [52243.224345] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:56:44 Desktop kernel: [52243.428344] usb 8-3.3: device not accepting address 6, error -22
Feb 13 00:56:44 Desktop kernel: [52243.500593] usb 8-3.3: reset high speed USB device using xhci_hcd and address 6
Feb 13 00:56:44 Desktop kernel: [52243.500678] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:56:45 Desktop kernel: [52243.704849] xhci_hcd 0000:03:00.0: Setup ERROR: address device command for slot 5.
Feb 13 00:56:45 Desktop kernel: [52243.908049] usb 8-3.3: device not accepting address 6, error -22
Feb 13 00:56:45 Desktop kernel: [52243.908594] sd 43:0:0:0: Device offlined - not ready after error recovery
Feb 13 00:56:45 Desktop kernel: [52243.909054] usb 8-3.3: USB disconnect, address 6
Feb 13 00:56:45 Desktop hald[2104]: forcibly attempting to lazy unmount /dev/sdk1 as enclosing drive was disconnected
Feb 13 00:56:45 Desktop hald: unmounted /dev/sdk1 from '/media/HD5______' on behalf of uid 0
Feb 13 00:56:45 Desktop kernel: [52244.013305] usb 8-3.3: new high speed USB device using xhci_hcd and address 0
Feb 13 00:56:45 Desktop kernel: [52244.032693] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
Feb 13 00:56:45 Desktop kernel: [52244.032829] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
Feb 13 00:56:45 Desktop kernel: [52244.032931] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
Feb 13 00:56:45 Desktop kernel: [52244.033064] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
Feb 13 00:56:45 Desktop kernel: [52244.034615] scsi45 : usb-storage 8-3.3:1.0
Feb 13 00:56:46 Desktop kernel: [52245.052601] scsi 45:0:0:0: Direct-Access     Seagate  FA GoFlex Desk   0157 PQ: 0 ANSI: 4
Feb 13 00:56:46 Desktop kernel: [52245.053160] sd 45:0:0:0: Attached scsi generic sg5 type 0
Feb 13 00:56:46 Desktop kernel: [52245.053543] sd 45:0:0:0: [sdk] 2930277167 512-byte logical blocks: (1.50 TB/1.36 TiB)
Feb 13 00:56:46 Desktop kernel: [52245.053934] sd 45:0:0:0: [sdk] Write Protect is off
Feb 13 00:56:46 Desktop kernel: [52245.053942] sd 45:0:0:0: [sdk] Mode Sense: 1c 00 00 00
Feb 13 00:56:46 Desktop kernel: [52245.053947] sd 45:0:0:0: [sdk] Assuming drive cache: write through
Feb 13 00:56:46 Desktop kernel: [52245.054971] sd 45:0:0:0: [sdk] Assuming drive cache: write through
Feb 13 00:56:46 Desktop kernel: [52245.054978]  sdk: sdk1
Feb 13 00:56:46 Desktop kernel: [52245.086871] sd 45:0:0:0: [sdk] Assuming drive cache: write through
Feb 13 00:56:46 Desktop kernel: [52245.086875] sd 45:0:0:0: [sdk] Attached SCSI disk
Feb 13 00:56:47 Desktop kernel: [52245.562112] EXT4-fs (sdk1): warning: maximal mount count reached, running e2fsck is recommended
Feb 13 00:56:47 Desktop hald: mounted /dev/sdk1 on behalf of uid 1000
Feb 13 00:56:47 Desktop kernel: [52245.691117] EXT4-fs (sdk1): recovery complete
Feb 13 00:56:47 Desktop kernel: [52245.691121] EXT4-fs (sdk1): mounted filesystem with ordered data mode. Opts: (null)
Feb 13 01:10:21 Desktop kernel: [53060.489078] EXT4-fs error (device sdj1): ext4_find_entry: inode #2: (comm krusader) reading directory lblock 0
Feb 13 01:10:21 Desktop kernel: [53060.489088] EXT4-fs (sdj1): previous I/O error to superblock detected


---

### Post by dkolars on 2012-02-13
OK, changed cable to HD5...  Re-started system... many message windows about drives not mounting, then they mounted, mounted 2 instances of them, etc.  SO...

Shut down system.  Turned off all USB drives.  Restarted system.  Internal drives mount just fine.

Turn on HD3.  Get window saying it won't mount.  Then get window showing contents of drive.  Look at my dirs in /media, and I have:

cdrom0          <DIR>
HD1              <DIR>
HD2              <DIR>
HD3              <DIR>

Cool.... so, turn on HD4.    Get window saying it won't mount.  Then get window showing contents of drive.  Then another window saying it's mounted.  Look at dirs again, and in addition to the above, I now have:

HD4              <DIR>
HD4_            <DIR>

Turn on HD5... same thing, same results:  HD5 ~and~  HD5_
Turn on HD 6... ditto...    HD7...  ditto.

Using Krusader, both drives are accessible, readable, & writable.

SO, I now have HD1, HD2, HD3, HD4, HD4_, HD5, HD5_, HD6, HD6_, HD7, HD7_

The Disk Utility shows the doubled up drives mounted at the location with the added underscore.  GParted shows the doubled up drives mounted in BOTH locations.

WTF?  I'm about ready to go back to Windows with all its grief... Gak.. wash my mouf out wif soap.... But, this is turning into too much hassle.  

Plus, _EVERY_ time I start up the system, I have dozens of instances of "flush: x-x" running, so my panel is filled with dozens of little vertical lines flickering about and running/minimized programs do not show because they are too small to show...  If I click on "Restart", I get the message that an unknown program is still running, and when I click "Cancel", the multitude of running flush processes stop running, and the panel again shows the running/minimized programs, but there is still an "Unknown program" running.  Then, of course we can't forget that the Nepomuk whatever crashes at least half the time, and I end up rebooting at least 2-3 times to get a clean running system.  Crap, I call it...

I'm running 10.10... are the 11.xx versions any better?

---

### Post by HiImTye on 2012-02-13
the log file you posted lists some errors with the drive, it could be a USB issue or an issue with the drive itself (or a combination). could also be a power issue if you are running a bunch of USB devices on the same USB interface at the same time

---

### Post by HiImTye on 2012-02-13
honestly, Id run an 11.10 live CD and see if you have the same issues when you have all the drives mounted. play around with it for a bit to make sure, that will give you an idea of whether its a hardware or driver/software issue

---

### Post by dkolars on 2012-02-14
Well, I ran 11.10...  Don't really care for Unity at 1st use/look...  but, I finally found the Disk Utility, mounted all the drives; at least it said they were all mounted.  Only drives HD1, HD3, & HD5 showed up in the left-hand panel...  found NO way to add the others and was not about to spend a lot of time messing with a new interface...  but, had it running for over 2 hrs., and NO re-mounting of any HDD's.  Now, back on 10.10, and after about the usual 30 mins., I now have an extra HD5.

I found a couple of links to getting rid of Unity and going back to the Gnome interface for 11.10... I've got 11.04 as well, but haven't tried it yet... I know that if it works, it's an upgrade to 10.10, and all my settings should migrate along with the new edition...  Not sure what would happen with 11.10.

But, it definitely appears to be software related...  I'm neglecting all my "to do's" messing with this... grrrr...  did get to spend a few hours in the shop today and actually got something productive done!!

---

### Post by dkolars on 2012-02-17
Well, it's ~kinda~ fixed... I updated from 10.10 to 11.04...  Now, every half hour, Ubuntu unmounts and remounts HD5.  So, at least no multiple instances of the drive showing up. 

 Now, the question is, what happens if I'm writing/reading something on that drive when it happens?  After 25+ years on the computer, I'm guessing (!) nothing good is gonna come of this!!

So, still futzing with it, but at least now it's behaving "mo bettah" than it was...  Plus 11.04 handles my new monitor MUCH better than 10.10... Graphics are actually scaled properly!!

---

### Post by cryptotheslow on 2012-02-17
Just a shot in the dark - do the external drives have some form of power saving function that could be doing something like powering down (even partially) the usb interface on the drive when idle? Leading to Ubuntu thinking it's been unplugged.

Likewise if you are using a PCI card for additional usb ports - that could be affected by power-saving modes as well.

As I say just a thought.

---

### Post by dkolars on 2012-02-17
That's a good point, actually... 3 of the external drives have power switches... one is USB powered.  This drive connects via USB, of course, and has external power, but NO power switch...  Could be the culprit?  Who knows, it's a computer!!!

---

### Post by dkolars on 2012-02-21
[Solved] ---  well, strange as it seems, the problem was that the HDD did not have an on/off switch... I got a new enclosure for the drive that had on/off switch, mounted drive in same, plugged it in, Ubuntu saw it immediately and has not unmounted/mounted it since.  There must have been something in the circuitry of the Seagate enclosure that was confusing Ubuntu.  Wanna buy enclosure, cheap?

---

### Post by jamesisin on 2012-02-24
Nice.

---

