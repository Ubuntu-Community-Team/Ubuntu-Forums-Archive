---
title: "Partition Help"
date: 2010-05-14
forum: General Help
---

### Post by xSchizoid on 2010-05-14
Hello all.

I have a few partitions: One for Ubuntu that is only around 50GB, and another for Windows Vista that has about 400GB of space. I've transferred some of my files over to the Linux side, but my Windows partition has over 250GB of music currently. Is there any way I can edit the partitions (my plan is something along the lines of reversing the current sizes), and move the music to my Linux partition without buying an external hard drive or uploading to a server? My current solution is to have the windows partition automatically mount on start up for easy access, but would like something a bit more permanent.

Here's a screenshot too:
[http://i44.tinypic.com/330z04z.png](http://i44.tinypic.com/330z04z.png)

-S

---

### Post by ryan858 on 2010-05-14
You can use *GParted* to resize partitions (even if they have data on them).

You can install it using the *Ubuntu Software Center* (located at the very bottom of the **Applications** menu) and type in **GParted** in the search (located top right corner of Software Center window).

OR

You can use the command-line utility *apt-get* to install it automatically as well;
Open a Terminal and type in:

**$ sudo apt-get update && sudo apt-get install gparted**

(Do not type the **$**, it just represents a user shell prompt (as opposed to root), in case you didn't know)

Once installed, it will be in your **System** menu under **Administration**. Or you could type the command **sudo gparted**.


And also... Although it is generally pretty safe to use and shouldn't cause any harm to your partitions, or the data on them, **you should use extreme caution in making any changes using this program**, since it *does* modify partition tables after all! Just be very careful and pay close attention to what you're doing, and review all your changes thoroughly before saving. It should give you a quick review when you press save, but check over it before then too. You can't be too careful when it comes to things like this.

But like I said, if you use safe practices (kind of common sense I would think, but you never know...) it's pretty safe to use. I don't mean to scare you or anything!

---

### Post by ajgreeny on 2010-05-14
Depending on your current partition setup, the best way may be for you to shrink your windows partition to a more sensible size for the OS only, and in the free space make a new ntfs partition that will be mounted at boot time and only contain your data.  That partition will be readable and writable from both OSs.  The windows shrinking should be done from windows own disk management utility if in Vista or Win7, but you can use gparted if it's WinXP, but only to shrink it from the right end back.  I hope you understand what I mean by that; ask again if not.

Let's see your present partition layout from a screenshot of gparted on the live Ubuntu CD, or use ```
sudo fdisk -l
``` and report the output back here.

---

### Post by dandnsmith on 2010-05-14
As a matter of safe practice, with a single HDD partitioned in this fashion, it would be wiser to boot from a live CD to make the proposed changes.
There is a Gparted LiveCD available for download.
I hope that gparted is safe to use in this context - there seem to be a few postings relating to damaged partition tables for the latest versions of Windows systems, and more relating problems booting afterwards.

---

### Post by obscurant1st on 2010-05-14
As of now i think u hv 150 gb free space in windows partition.
Then just use gparted to reduce the windows partition size to around 300 GB then grow the linux partition to 150 Gb.
Now linux has got some free space, move aroung 80 Gb music to linux from windows.Now again windows will be having 80 Gb freespace. Like this do untill all the music is transfered to linux., whats the big deal..
i am sorry if this wasnt the actual problem.. :|

---

### Post by ryan858 on 2010-05-14
I think obscurant is right. All you have to do is shrink the Win partition as much as possible, then grow the linux partition as much as possible, transfer files, and repeat.

For safety concerns, you might want to manually specify sizes and leave a gig or two of free space on each partition during these operations... I think it would reduce the risk of problems coming up from gparted possibly overlapping things, or erasing data, or anything like that.

BTW, have a calculator handy, you might need it for size conversions.

---

### Post by ryan858 on 2010-05-14
Also, what you can do, besides resizing the partitions, is add the windows partition to *fstab* and symlink the music folders to your linux partition... This way you're Win partition will always be mounted when you boot into Ubuntu, and you will have convenient links on your linux partition that act as if they are actually folders on the filesystem.

For example:

[B]$ link "/media/Windoz/My Music" /music
$ cd /music && vlc whatever.mp3[/B]

or you can do it via gui, like with *Nautilus*... if you right click on a file/folder you can click **Make Link**, to create a symlink. It will make it in the current folder but you can open a new nautilus in / and drag 'n drop the link into /



Adding the partition to *fstab* is pretty easy. e.g. if your windows partition is /dev/sdb1  and you want to mount it in /media/Windoz then you would add the following to fstab:

*/dev/sdb1 /media/Windoz ext4 rw 0 0*

The format for a line in *fstab* is as follows:

*<Device> <Mount Point> <Filesystem Type>* [I]<Options> <Dump> <Pass>


[/I]

---

### Post by warfacegod on 2010-05-14
Frankly I'm surprised only ajgreeny has mention this; resizing a Vista or 7 partition from outside of Windows is incredibly risky.

Please read here: [http://ubuntuforums.org/showthread.php?t=1482025]("http://ubuntuforums.org/showthread.php?t=1482025")

You should defrag your HDD and then resize Windows with its own Disk Management tool. Doing anything else is begging for trouble.

---

### Post by ryan858 on 2010-05-14
I didn't know Windows could resize partitions. Cool.

---

### Post by warfacegod on 2010-05-14
> **ryan858 said:**
> I didn't know Windows could resize partitions. Cool.

Vista and 7 can. XP can't but resizing XP with, for instance Gparted, is generally allot safer. XP is allot more tolerant of such things. Its also allot more tolerant of other bootloaders being installed. Vista and 7 usually panic for that too.

---

