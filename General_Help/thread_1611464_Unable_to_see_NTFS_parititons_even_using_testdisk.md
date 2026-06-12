---
title: "Unable to see NTFS parititons even using testdisk"
date: 2010-11-01
forum: General Help
---

### Post by flitbee on 2010-11-01
I was running Windows XP SP3 when one of my drives (or partitions) suddenly wasn't accessible. I booted into an old ubuntu Live CD I had (version 8.X) and tried mounting it. I could see the other partitions at this time. I rebooted the machine a couple of times (for normal reasons) and after a particular reboot none of my partitions were present! All seemed to have gone! I didn't do anything except mount the partition from Ubuntu Live CD. Made no write operations (at least explicitly).

**fdisk -l** gives me this:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08517fe2

   Device Boot      Start         End      Blocks   Id  System
```There are no partitions, just one device (my HDD of 500GB). I scanned the drive using [Sprinrite]("http://www.grc.com/spinrite.htm") (to make sure it wasn't a physical drive problem) and it results were clean. I had no bad sectors. I then tried using [testdisk]("http://www.cgsecurity.org/wiki/Running_TestDisk").

```

Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 500 GB / 465 GiB - ATA Hitachi HDP72505


[Proceed ]  [  Quit  ]

```I tried searching for my partition selecting [Intel] but nothing showed up when it was done 45 mins later. None of the topics (at least from what I can see) have a situation where partitions have disappeared and testdisk doesn't recover them. Mine seems to be such a case. I then tried the option "Non partitioned media" > "Analyse". I then got something:

```
 
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

The harddisk (500 GB / 465 GiB) seems too small! (< 16049941 TB / 14597336 TiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  HFS+                 13522  93 45 2787130488 125 38          0
  HFS+                 13891  26 44 3535040661 206 13 2147483648
  HFS+                 14087 126 35 2020299169  28 38 3106947584
  HFSX                 14450 174  3 1207906469  62 31  123034880
  HFS+                 14505  63  7 2938783755  22 27 1047481056
  HFSX                 15365 117 21 3784811885  14 26 3199045141
  HFS+                 15616  56 55 204804173 109 30 4278190080
  HFSX                 18278 236 12 2772090252 187 32 3115334316
  HFS+                 19835 164 55 1393933834 106 42 3563876221
  HFSX                 20236 166 11 1379107766 253 13 1599862166

[ Continue ]

```I have lots of questions, not sure where to start: What does the above mean? How to I interpret "Size in sectors". What is an "HFS+" partition? Does it mean I've lost my MBR? 

I clicked "Continue" and this is what I get:

[IMG]http://img526.imageshack.us/img526/7217/screen1o.gif[/IMG]

I selected the rows

```

P NTFS                  8413 208 51 10453 135 49   32768000
P NTFS                 21162  39 61 33910  93 38  204800000
P NTFS                 33910 126  8 46658 179 48  204800000
P NTFS                 46658 212 18 59407  10 58  204800000


```to list the files and I get:

```
Can't open filesystem. Filesystem seems damaged.
```Does that mean it's truly damaged? No way to recover it? Also why is Sprinrite still there?

I originally had 6 partitions (including my primary). What do I make of the above screen and how do I proceed? Mot of testdisk documentation says "Choose the paritions to recover..." but I do not have a partition. 

What do I do to recover my data? I don't mind reformatting my entire HDD, but I need to get some jpegs and movie files off it first. 

Anybody?

---

### Post by Bitrate on 2010-11-01
Try booting your XP system disk, go into console mode, and then run a CHKDSK /r x: (your drive letter).

BTW, HFS+ is a Macintosh file system.

---

### Post by flitbee on 2010-11-01
> **Bitrate said:**
> Try booting your XP system disk, go into console mode, and then run a CHKDSK /r x: (your drive letter).

BTW, HFS+ is a Macintosh file system.

I do not have the XP system disk at present, but shall try to get that. And how did HFS+ appear on my system at all :confused:. I don't have any Apply hardware.

---

### Post by Bitrate on 2010-11-01
> **flitbee said:**
> I do not have the XP system disk at present, but shall try to get that. And how did HFS+ appear on my system at all :confused:. I don't have any Apply hardware.

You could try a live system CD (eg. BartPE - [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)) instead if you can't find your XP system disk. 

As for the HFS+ partitions detected by Testdisk - it's probably just a best guess that Testdisk makes from analyzing the partition structure.

I hope you fix you NTFS partition. I had the same problem when running openSUSE 11.3. It would occasionally corrupt my NTFS partitions and I had no way of repairing them from within Linux. I ended up formatting them to ext4 and doing away with having a Windows OS sharing a partition with Linux.

---

### Post by wilee-nilee on 2010-11-01
Here is a XP ISO link.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

Will work fine for a chkdsk it is a slipstreamed Sp3 full install no key iso.

---

### Post by flitbee on 2010-11-02
I tried booting into a Win XP SP3 disk but since there are no partitions available (or are missing), I couldn't run a chkdsk or any other tool. So it rules out the Win XP option too :(

---

### Post by flitbee on 2010-11-02
Thought I'd update this thread as I work in case someone's got a similar scenario - I rebooted (am using a non-persistent USB Ubuntu distro) and ran TestDisk again (with the *Intel* option). THIS time I see - 

```
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0  32 33    12 223 19     204800 [System Reserved]
P HPFS - NTFS             12 223 20  6374  84 14  102196768 [OS]
P HPFS - NTFS           8413 241 21 21162  39 61  204800000 [Personal]
L HPFS - NTFS          21162  72 31 33910 126  8  204800000 [Movies]
L HPFS - NTFS          33910 158 41 46658 212 18  204800000 [VHD]
L HPFS - NTFS          46658 244 51 60801  47 46  227194880 [DUMP]

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue


```For some reason it shows up now (moral: try again). I think it does because THIS time I answered "Y" to

```
Should TestDisk search for partition created under Vista ? [Y/N] (answer Yes if unsure)
```I had answered N the last time (since my OS was Win XP and not Vista). Well anyway THIS time I could see my partitions (except 1).

It gives me the option to copy and so I did to a portable HDD. I couldn't yet find a way to copy the entire partition. TestDrive doesn't give such an option. Also one partition is missing (the one I tried to recover initially and that led to my whole HDD being non-bootable); I've yet to see that show up anywhere.

---

### Post by flitbee on 2010-11-02
After the scan came showed all my drives (bar one) in my post [above]("http://ubuntuforums.org/showpost.php?p=10060315&postcount=7"), I  pressed "Enter to Continue" and  Selected "Write" 

```
[  Quit  ]  [Deeper Search]  [ Write  ]
                          Try to find more partitions

```

I was asked to reboot the machine (into Ubuntu) and voila! all my partitions appeared (except the missing one). I still haven't got the missing partition (the 6th one) that started this whole thing.

PS - I also  found a way to copy an entire partition using testdisk. 

[IMG]http://img192.imageshack.us/img192/5467/screenshot1jy.png[/IMG]

Instead of selecting individual files, I only need to select the . (current directory) as shown above and press "c" (for copy). This will copy the entire contents.

---

### Post by flitbee on 2010-11-03
Good news - On doing a "Deeper Search", I got the missing drive! The one labelled "Installs". It's marked as "D" i.e. deleted, though I did not delete it. I can now copy my files off of it. :)

[IMG]http://img135.imageshack.us/img135/8084/screenshotyg.png[/IMG]

I don't know what to do to recover my drive to be bootable in Windows. I can copy off the data, but I'm not sure how to rebuild my partition tables or MBR

---

