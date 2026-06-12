---
title: "Formatting 1.5 GB hard drive"
date: 2009-07-29
forum: General Help
---

### Post by bla4free on 2009-07-29
I'm trying to format a 1.5 TB SATA hard drive. When I used gparted, I get this error:

Could not add this operation to the list.
A partition cannot have a length of -1 sectors.

I'm using a fresh install of 8.04. Thanks!

---

### Post by michy99 on 2009-07-29
Apparently you are not giving it a proper size for the partition. Can you post a screenshot from gparted?

---

### Post by benj1 on 2009-07-29
i would be very suprised if its a 1.5gb sata drive.
it would either be 1.5tb or an ata drive

---

### Post by bla4free on 2009-07-29
> **michy99 said:**
> Apparently you are not giving it a proper size for the partition. Can you post a screenshot from gparted?

[img]http://img.thoughtreactor.com/gparted.png[/img]

I get this error on both ext2 and ext3.

---

### Post by credobyte on 2009-07-29
Click **New**, fill all the fields and post a screenshot ( your previous one does not help at all ).

---

### Post by bla4free on 2009-07-29
> **credobyte said:**
> Click **New**, fill all the fields and post a screenshot ( your previous one does not help at all ).
I've updated the screenshot.

---

### Post by bla4free on 2009-07-30
Gparted says I'm using 0.3.5; but, the Gparted website says 0.4.5 is the latest. Is there not a way to download the latest release with apt-get? It only installs the 0.3.5 version.

---

### Post by credobyte on 2009-07-30
Mine says "GParted 0.4.3", so .. upgrading might help:
```
sudo apt-get update && sudo apt-get upgrade gparted
```

---

### Post by bla4free on 2009-07-30
> **credobyte said:**
> Mine says "GParted 0.4.3", so .. upgrading might help:
```
sudo apt-get update && sudo apt-get upgrade gparted
```

When I do that, it says there's nothing to be upgraded. Does that have anything to do with 8.04?

Also, I found out that I can create a 900 GB partition on there--just nothing over 1 TB.

---

### Post by realzippy on 2009-07-30
"When I do that, it says there's nothing to be upgraded. Does that have anything to do with 8.04?"

Yes.
There is a known bug in older gparted versions:

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/322772](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/322772)

You should use a newer version.
There are also gparted-liveCD-ISOs out:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by credobyte on 2009-07-30
> **bla4free said:**
> When I do that, it says there's nothing to be upgraded. Does that have anything to do with 8.04?

Also, I found out that I can create a 900 GB partition on there--just nothing over 1 TB.

Umh, yeah - most likely it's not updated yet ( I'm running 9.04 ) :roll:
If you create a 900GB partition, can you create another, smaller one ( after formating 900GB ) ?

---

### Post by Slim Odds on 2009-07-30
And really, why would you want a 1.5TB partition in the first place?

---

### Post by bla4free on 2009-07-30
> **Slim Odds said:**
> And really, why would you want a 1.5TB partition in the first place?
We are using a backup device made by High-Rely and we have 4 1.5 TB hdds in there--I want the entire size of the hdd just to make configuring the backups easier.

---

### Post by bla4free on 2009-07-30
> **realzippy said:**
> "When I do that, it says there's nothing to be upgraded. Does that have anything to do with 8.04?"

Yes.
There is a known bug in older gparted versions:

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/322772](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/322772)

You should use a newer version.
There are also gparted-liveCD-ISOs out:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

I tried the Live CD but it displayed a ton of errors when loading--it may have had something to do with the RAID hardware.

---

### Post by bla4free on 2009-07-30
Okay. I got the drives formatted. I ended up downloading the test build (0.4.5.5) of gparted and it was able to format the hard drives. Thanks all for your help!

---

### Post by kcox5342 on 2009-10-12
Trying to install a 1.5TB SATA drive on my mythtv box running 8.04 64-bit and format it as one large partition.  Gparted gave me the -1 error, so I tried a couple live CDs.  Parted Magic 4.5 loaded and looked like it was doing good, but froze partway through.  GParted Live 0.4.6-1, however, worked flawlessly.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by Kjella on 2010-02-02
On Kubuntu 9.10 here, had same problem so just formatted it in parted as it's apparently a GUI problem and nothing to do with the msdos partition table. I selected my disk and did "mkpart primary 0 -1" = make a primary partition from sector 0 to last sector. Worked just fine and I had my 1.5TB partition.

---

