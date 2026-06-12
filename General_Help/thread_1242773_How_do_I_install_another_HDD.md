---
title: "How do I install another HDD?"
date: 2009-08-17
forum: General Help
---

### Post by adrian-g on 2009-08-17
I have an old IBM Aptiva that I am using as a server, and I just got a few used IDE HDD's.

I'd like to know how I can install another one. Please share any formatting instructions, etc.

---

### Post by cariboo on 2009-08-17
If you are going to format the drive as ext3, you first have to partition the drive using fdisk:

```
sudo fdisk /dev/hdb
```

substitute your hard drive label for the one above. Once at the fdisk screen press **m** to show the menu. Set up your partitions the way you want, the press **w** to write the changes to the disk. You may have to reboot in order for the changes to take affect.

Next format the drive:

```
sudo mkfs -t ext3 /dev/hdbX
```

again substitute tour drive for the example above. The mount the drive. create a directory in /media:

```
sudo mkdir /media/data
```

then mount the drive:

```
sudo mount /dev/hdb1 /media/data
```

If you want to mount the drive automatically edit /etc/fstab

/dev/hdb1 /media/data ext3 relatime  0  0

For more info on options read the respective man pages.

---

### Post by egalvan on 2009-08-17
> **cariboo907 said:**
> If you are going to format the drive as ext3, you first have to partition the drive using fdisk:


Great condensed version...

It's going into my "saved" file!

Thanks!

---

### Post by adrian-g on 2009-08-17
Thank you, cariboo907!

But first, what is the command to see all of the HDD's attached? I don't know how to see the labels.

---

### Post by SuperSonic4 on 2009-08-17
```
sudo fdisk -l
```

or you can use gparted/another partition manager (better for non-partitioned drives)

---

to answer the title bluntly: you stick it in the mount, connect it to the PSU, connect it to the motherboard and away you go ;)

---

### Post by adrian-g on 2009-08-17
OK, this is what I think I should do (please correct me if I'm wrong!);

[LIST]
[*]Connect the new IDE drive to the IDE cable of the existing drive (there is a connection at around the halfway point of the ribbon cable)
[*]Connect it to the PSU
[*]Boot up the PC
[*]sudo fdisk -l to get the label
[*]sudo fdisk /dev/hdb (with the appropriate label)
[*]go through the partition process
[*]sudo mkfs -t ext3 /dev/hdbX (partition it, with the appropriate label)
[*]sudo mkdir /media/data (does it have to be called "data"?)
[*]sudo mount /dev/hdb1 /media/data (mount it)
[*]and finally, edit fstab
[*]/dev/hdb1 /media/data ext3 relatime 0 0 (**did you mean "realtime"?)**
[/LIST]

Edit: I SSH'ed into the server and ran fdisk -l. There are no /dev/hd__, only /dev/sda_. Is this normal? Will the new drive show up as /dev/hd__?

---

### Post by egalvan on 2009-08-17
> **adrian-g said:**
> OK, this is what I think I should do (please correct me if I'm wrong!);

[*]Connect the new IDE drive to the IDE cable of the existing drive (there is a connection at around the halfway point of the ribbon cable)
[/LIST]

**BEFORE** you install the drive, 
you should check on the **Master/Slave** jumpers...

Being an older machine, it may not have Cable Select...

Set the original drive to **MASTER**

Set the second (add-on) drive to **SLAVE**.

You can also connect the drive to the **secondary controller**, setting it up as **Master**, and the optical (if any) as Slave.

---

### Post by egalvan on 2009-08-17
> **adrian-g said:**
> 

Edit: I SSH'ed into the server and ran fdisk -l. There are no /dev/hd__, only **/dev/sda**_. Is this normal? Will the new drive show up as /dev/hd__?

No, as the second hard drive should show up as sd**b**.
Or hd**b** at the least... depending on what exact driver is accessing...

If no "b" is showing, then the secon drive is not being recognized.

First hard drive should be hda or sda
second hard drive should be hdb or sdb

Does the BIOS see the second drive?

---

### Post by adrian-g on 2009-08-17
Sorry, I might have come off wrong. I hadn't connected the second drive when I SSH'ed into it. I'm doing that right now. I just wanted to know if SDA was normal.

These jumper settings are giving me problems. I have a Maxtor (Model 90680D4) and the pins look like this:

: : : . : 

I can't figure out how to set the jumpers as Slave. Every link I find to the documentation is dead.

---

### Post by egalvan on 2009-08-17
I found this....
(Google is your friend!)

[http://stason.org/TULARC/pc/hard-drives-hdd/maxtor/90680D4-DMAX3400-6800MB-3-5-SL-ATA4.html](http://stason.org/TULARC/pc/hard-drives-hdd/maxtor/90680D4-DMAX3400-6800MB-3-5-SL-ATA4.html)


It's gonna depend on it being by itself on the cable, or with another hard drive....



```
Jumpers
MAXTOR DIAMOND MAX INSTALLATION SHEET
Jumper Setting
==============
Jumpers

                                        +---+---+---+---+---+
                                        |J50|J48|J46|J44|J42|
  +-------------------------------------+---+---+---+---+---+
  | Master/Slave                        |   |   |   |   |   |
  |  [COLOR="Red"]Only Drive in single drive system*[/COLOR] | J |   |   |   |   |
  +-------------------------------------+---+---+---+---+---+
  |  [COLOR="Red"]Master in a dual drive system* [/COLOR]    | J |   |   |   |   |
  +-------------------------------------+---+---+---+---+---+
  |  [COLOR="Red"]Slave in a dual drive system[/COLOR]       | O |   |   |   |   |
  +-------------------------------------+---+---+---+---+---+
  | Cable Select                        |   |   |   |   |   |
  |  Disabled*                          |   | O |   |   |   |
  +-------------------------------------+---+---+---+---+---+
  |  Enabled                            |   | J |   |   |   |
  +-------------------------------------+---+---+---+---+---+
    J=Jumpered O=Open *=Default

```

---

### Post by adrian-g on 2009-08-17
Thanks everyone, it ended up being no jumpers=slave.

I connected all of the cables, started it up, SSH'ed into the box, installed gparted (I am familiar with it, as opposed to fdisk), formatted the drive to ext3 (and removed boot+lba flags), and now it's humming nicely!

---

