---
title: "Getting rid of Linux?"
date: 2011-07-31
forum: General Help
---

### Post by ILEetz on 2011-07-31
Hey guy how can I format Linux off my Laptop without damaging it as I did not dual boot how can i format, I tried to format though vista reinstall but it gave me a error saying I can't any ideas?

---

### Post by 23dornot23d on 2011-07-31
Use a Ubuntu Livecd and have a look first using Gparted to see what the disk
is setup like first .....

Post a screen shot afterwards ..... if you would - it may give us more idea of what the disk layout is like now .....

There is also a [_***bootscript on sourceforge***_]("http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.60/") you could run to get more information .......

 ..... but if you are just going to format it maybe gparted will show enough information .......

---

### Post by ILEetz on 2011-07-31
[http://i55.tinypic.com/2ptrldw.png](http://i55.tinypic.com/2ptrldw.png)

---

### Post by WorMzy on 2011-07-31
Delete both of those partitions, and the extended partition (after unmounting the swap partition), and then reboot into the Windows installer.

Assuming, of course, you have no data you need to keep on the ext4 partition.

Oh yeah, I better quote 23dornot23d, seeing as how you ignored him the first time.

> **23dornot23d said:**
> Use a Ubuntu Livecd

> **23dornot23d said:**
> Use a Ubuntu Livecd

> **23dornot23d said:**
> [SIZE="4"]Use a Ubuntu Livecd[/SIZE]

---

### Post by ILEetz on 2011-07-31
What is the difference?

---

### Post by WorMzy on 2011-07-31
You can't delete partitions that are mounted, and you can't unmount the partition you're booted into.

---

### Post by 23dornot23d on 2011-07-31
update as -above - we both replied together

The difference is while you are running from that drive the partitions you need
to delete are in use ...

Using the Livecd means you can work on the disk and alter it .....

Removeing partitions ..... needs the partitions to be unmounted and not in use ....

as said remove any data you need off it first .....

---

### Post by ILEetz on 2011-08-01
Ok, I downloaded gParted and how do I ISO it to a USB?
And what do I do after that?

---

### Post by ILEetz on 2011-08-01
Can anyone help I need windows asap.

---

### Post by Jouke S on 2011-08-01
You should be able to run Windows alongside of Ubuntu, a so called dual boot.
What exactly is the problem? 
Removing your ubuntu install won't magically recover your vista install.

I recommend you make a thread carefully explaining the issues you encounter in the Installation & Upgrades forum

---

### Post by Sylos on 2011-08-01
As far as I am aware you cannot just burn Gparted to a CD as it is an application and requires and OS environment in which to operate. This is why everyone is saying to use a live CD as it will allow you to boot into a linux OS and then use Gparted (which comes on the live CD as standard) to rearrange the drives.

I assume you installed Ubuntu from a disk onto your laptop - Yes?

You should be able to just use that install disk but instead of choosing to install at the boot screen - choose to try it first. This will open a live session and allow you to use Gparted.

All the best.

---

### Post by .... on 2011-08-01
You use a program called Unetbootin to create a LiveUSB. Note that you need a whole Linux ISO. I recommend PartedMagic, as it's made for that purpose. [http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

---

### Post by kaldor on 2011-08-01
**_Step 1: Download the gParted CD Image_**

[LIST]
[*][_Click here to download this._]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.9.0-7/gparted-live-0.9.0-7.iso/download")
[/LIST]

**_Step 2: Burn the gParted CD Image to a CD or DVD_**

[LIST]
[*]Get a blank CD or DVD and insert it into the CD tray.

[*]Open the **Brasero Disc Burner** application.

[*]When Brasero is up, click "Burn Image" button on the list.

[*]When a dialog box opens up, select "*Click here to select a disc image* and find the gParted.iso image you downloaded.

[*]Select the blank CD in the "Select a disc to write to" field.

[*]Press "Create Image"
[/LIST]

**_Step 3: Using the CD_**

[LIST]
[*]Once the CD is finished burning and claims to be successful, you need to reboot with the CD in the drive.

[*]When the CD is finished loading, you will be presented with a partition editor. You will then have full run of the system. **Make backups beforehand if you need to**.
[/LIST]



Any questions, etc, feel free to ask.

---

### Post by Mark Phelps on 2011-08-01
> **Sylos said:**
> As far as I am aware you cannot just burn Gparted to a CD as it is an application and requires and OS environment in which to operate. This is why everyone is saying to use a live CD as it will allow you to boot into a linux OS and then use Gparted (which comes on the live CD as standard) to rearrange the drives.
FYI ... Gparted LiveCD is just that -- an ISO image you burn to a CD that then creates a BOOTABLE CD.

> You should be able to just use that install disk but instead of choosing to install at the boot screen - choose to try it first. This will open a live session and allow you to use Gparted.

It's generally easier for new folks to do partitioning using the GParted LiveCD because, unlike the Ubuntu LiveCD, it does NOT mount any partitions.

---

### Post by Sylos on 2011-08-02
> **Mark Phelps said:**
> FYI ... Gparted LiveCD is just that -- an ISO image you burn to a CD that then creates a BOOTABLE CD.



It's generally easier for new folks to do partitioning using the GParted LiveCD because, unlike the Ubuntu LiveCD, it does NOT mount any partitions.

Very true about GParted Live but the OP said he had downloaded Gparted and wanted to know how to burn it to as an ISO to a CD or USB - hence my post. Probably should have mentioned the Live version as an option - My bad on that front. Suppose I just thought it was easier to work with what he already had.

Hey Ho...

---

### Post by dingsheng on 2011-08-02
[http://www.linux.com/archive/forums/topic/3831](http://www.linux.com/archive/forums/topic/3831)
If you want to kone more about me,please visit my "[http://www.top-crusher.com](http://www.top-crusher.com)" ore crusher website or "[http://www.wcrusher.com](http://www.wcrusher.com)" stone crusher website.

---

### Post by CryptElectric on 2011-08-02
It is very simple follow these steps;

Put your reformatting CD in your CD/DVD drive.

Boot from CD

Follow the steps

Update your OS through the Microsoft site.

If I may, I would recommend downgrading to Windows XP and then dual booting with Ubuntu. Ubuntu is great for school work, and writing/working. 

XP is better than Vista in general, and is good for gaming, and video/picture making/editing.

---

### Post by pieroxy on 2011-08-02
Why does he needs a LiveCD at all? Just put the Vista CD in there and install. On the partitionning stage, just remove all existing partitions.

Of course, that'll remove all the data as well...

---

