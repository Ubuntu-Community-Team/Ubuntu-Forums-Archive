---
title: "USB Hard Drive ... No Location?"
date: 2010-10-31
forum: General Help
---

### Post by Nomad55 on 2010-10-31
Hi Folks

     I guess I wouldn't be here if I didn't have a problem, but I do.  I'm a complete newbie to Ubuntu.  I installed 10.04, liked it, and upgraded to 10.10.

     My problem lies with an external 200 gig USB hard drive.  It initially worked with 10.04.  However, now when I plug it in it not only doesn't come up automatically, I can't mount it manually either.  When I look at it in Disk Utility, it doesn't show a location for it but I do get the manufacturer, serial number, etc.  It'll do a benchmark for it.  Fdisk shows all the specifics for it, other than a location.  Extended and swap volumes show 6.2 Gig each, with 194 shown as "unknown."
  
     I tried putting it on a Windows system, and it doesn't even recognize it's there, although that's where all the files on it came from.  I'm not using a dual boot system; each computer is independent.

     Obviously, something's wrong.  Anybody got an idea how to recover this?  If I lose it it's not the end of the world, but some of these files can't be duplicated.  I'd sure like somebody to show me the error of my ways before I gotta call this drive FUBAR and just write it off!

---

### Post by coffeecat on 2010-10-31
I don't understand this:

> **Nomad55 said:**
> Fdisk shows all the specifics for it, other than a location.

So let's get the specifics. Plug the drive in, switch it on and post the terminal output of:

```
sudo fdisk -lu
```And...

```
dmesg | tail
```It sounds as though it could be formatted NTFS, so a filesystem corruption is possible. If it is NTFS, one thing you could try is running ntfsfix from the terminal. Type 'man ntfsfix' to see how to run it. The output of fdisk will give you the device descriptor. Note that ntfsfix can only half repair a NTFS filesystem (see the comment in man ntfsfix), but it might fix it enough for it to be recognised  by Windows so that you can  run chkdsk from Windows.

---

### Post by Nomad55 on 2010-11-01
Thanks for trying to help

     Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cfcab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   378679295   189338624   83  Linux
/dev/sdc2       378681342   390721535     6020097    5  Extended
/dev/sdc5       378681344   390721535     6020096   82  Linux swap / Solaris


[ 1051.599046]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1051.599052]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1051.599058]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1051.599064]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1051.599069]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1053.457755] wlan0: authenticate with 00:60:b3:d8:35:1e (try 1)
[ 1053.459293] wlan0: authenticated
[ 1053.459344] wlan0: associate with 00:60:b3:d8:35:1e (try 1)
[ 1053.461266] wlan0: RX AssocResp from 00:60:b3:d8:35:1e (capab=0x461 status=0 aid=5)
[ 1053.461273] wlan0: associated
bill@bill-HP-Pavilion-dv9500-Notebook-PC:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003d050

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   224827391   112412672   83  Linux
/dev/sda2       224829438   234440703     4805633    5  Extended
/dev/sda5       224829440   234440703     4805632   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22a34bec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   234436544   117218241    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cfcab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   378679295   189338624   83  Linux
/dev/sdc2       378681342   390721535     6020097    5  Extended
/dev/sdc5       378681344   390721535     6020096   82  Linux swap / Solaris
bill@bill-HP-Pavilion-dv9500-Notebook-PC:~$ dmesg | tail
[ 1051.599046]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1051.599052]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1051.599058]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1051.599064]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1051.599069]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1053.457755] wlan0: authenticate with 00:60:b3:d8:35:1e (try 1)
[ 1053.459293] wlan0: authenticated
[ 1053.459344] wlan0: associate with 00:60:b3:d8:35:1e (try 1)
[ 1053.461266] wlan0: RX AssocResp from 00:60:b3:d8:35:1e (capab=0x461 status=0 aid=5)
[ 1053.461273] wlan0: associated


     I believe this is the info you asked for, CoffeeCat.  Hope this makes my problem a bit more clear to you, 'cause to me it still looks like mud.

---

### Post by coffeecat on 2010-11-01
There are a few things in your two posts that don't quite add up, so let's clarify those first.

> **Nomad55 said:**
> My problem lies with an external 200 gig USB hard drive.  It initially worked with 10.04.

I read that to mean that your 200GB worked as an external drive with 10.04. However, fdisk is showing your 200GB drive as sdc and partitioned up just as an internal drive would be for an Ubuntu system. Perhaps you could clarify.

> **Nomad55 said:**
> I tried putting it on a Windows system, and it doesn't even recognize  it's there, although that's where all the files on it came from.  

And I originally read that to mean that you copied the files onto the drive using Windows, hence my comment about NTFS, which you can now ignore. The 200GB drive has Linux filesystems which Windows can't use (unless you install a 3rd party driver), and that's why it doesn't recognise it.

> **Nomad55 said:**
> Extended and swap volumes show 6.2 Gig each, with 194 shown as "unknown."

That's more-or-less the figures I get working out your partition sizes of sdc from the fdisk output. sdc1 is a ~193-4GB partition with an ext2/3/4 filesystem. fdisk merely reports the contents of the partition table, not the state of the filesystem. That "unknown" message comes from Disk Utility? Am I correct?
  
Lastly, did you run 'dmesg | tail' immediately after plugging in the drive and running fdisk? Because there is no indication of the system seeing sdc at all from dmseg. Which is odd, since fdisk is seeing it. Perhaps you could clarify. It is important we establish exactly what dmesg sees **immediately after** plugging in and switching on the drive. If you need to repost the dmesg output, **please** enclose it in [noparse]```

```[/noparse] tags to make it readable. Please do that with any posted terminal output or configuration file contents to keep formatting. Your fdisk output was originally neatly columned but is now difficult to read.

Once we've sorted out what dmesg is telling us, it may be possible to tell whether this is likely to be a hardware problem in the drive or a filesystem corruption which might be repairable.

---

### Post by Nomad55 on 2010-11-01
First, CoffeeCat, I appreciate the help you're trying to give.  Now, to your questions.

I read that to mean that your 200GB worked as an external drive with  10.04. However, fdisk is showing your 200GB drive as sdc and partitioned  up just as an internal drive would be for an Ubuntu system. Perhaps you  could clarify.

     Love to, but I can't.  I've never intentionally written anything to this drive using Ubuntu.

That "unknown" message comes from Disk Utility? Am I correct?
Yes, that is correct.

Lastly, did you run 'dmesg | tail' immediately after plugging in the  drive and running fdisk? Because there is no indication of the system  seeing sdc at all from dmseg. Which is odd, since fdisk is seeing it.  Perhaps you could clarify. It is important we establish exactly what  dmesg sees **immediately after** plugging in and switching on the drive. If you need to repost the dmesg output, **please**  enclose it in ```

``` tags to make it readable. Please do that  with any posted terminal output or configuration file contents to keep  formatting. Your fdisk output was originally neatly columned but is now  difficult to read.

Once we've sorted out what dmesg is telling us, it may be possible to  tell whether this is likely to be a hardware problem in the drive or a  filesystem corruption which might be repairable.

     I'll follow that to the best of my ability, but I won't be able to do it tonight.  My days start very early and I'm running on empty right now.

---

### Post by coffeecat on 2010-11-01
> **Nomad55 said:**
> Love to, but I can't.  I've never intentionally written anything to this drive using Ubuntu.

I thought my question was clear, but that doesn't answer it. Did you or did you not use the 200GB drive as an external drive with 10.04? Did you or did you not use the 200GB drive as an internal drive for running 10.04?

And I find your posts very difficult to read. You are quoting me without using quote tags, just as you are posting code without code tags. Please help others to help you. Guide to BBCode:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by Nomad55 on 2010-11-02
CoffeeCat, I appreciate your help.  I've figured out the problem and recovered the files; they were actually FAT32.  Thanks for your assistance; there's a good chance I'll be asking for it again!

---

### Post by coffeecat on 2010-11-03
I'm glad it's sorted.

Good luck!

---

