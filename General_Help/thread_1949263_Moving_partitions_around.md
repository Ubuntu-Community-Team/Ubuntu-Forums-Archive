---
title: "Moving partitions around"
date: 2012-03-29
forum: General Help
---

### Post by bobman321123 on 2012-03-29
So, I have a 500 gb hard-drive, all divided up into pieces, since I'm triple booting Ubuntu 12.04, Ubuntu 11.10, and Windows XP.

It looks like the image attached to this post.
/dev/sda1 is windows XP, it's a primary partition. 
/dev/sda7 is Ubuntu 11.10.
/dev/sda9 is Ubuntu 12.04.

So, what I'd like to do is to move sda9 to the place of windows XP and delete Windows XP entirely (or perhaps shrink it way down and keep it just in case I need it for something). I'd also like to keep Ubuntu 11.10 pretty much where it is for now, as a back up till the stable release of Ubuntu 12.04 comes out. 

While I could probably do this on my own, I'd rather not mess this up, and I don't really know what I'm doing, moving partitions between primary and logical and whatnot. 

So, could anyone walk me through this?

---

### Post by Bucky Ball on 2012-03-29
Your best bet is to shrink XP to about 20Gb (use Windows software, NOT Gparted), or delete it, then expand the extended partition into the free space, then extend sda7 into the free space inside the extended partition. Hope that makes sense. 

Moving the whole install from sda9? Not sure if that's possible. Why exactly do you want to do that?

Incidentally, expanding/shrinking the Ubuntu partitions must be done using the LiveCD, Try Ubuntu, open Gparted as the OS partition needs to be unmounted (and it is not if you're running from the hard drive).

---

### Post by UltimateCat on 2012-03-29
Just chiming in as I just learned that I would have to shrink my Windows XP partition if I wanted to add Fedora along with Ubuntu that I already have....

Bobman:
   I feel the same as you, I could probably do it on my own...but don't want to mess this up-
I thought about going online and watching tutorials on installing Fedora but then realized what would be the point in that as I do not have the Live Cd for Ubuntu...nor do I have Windows software as Bucky Ball advises-

Think my hands are tied because I don't have other knowledge to do this any other way; and don't want to ruin the 2 OSs that I do have.

I did find that you can put an OS on a USB but even that has to be properly formatted as well-

If I find a way I will post it

---

### Post by oldfred on 2012-03-30
You have larger / (root) partitions. I find when I am booting multiple copies of Ubuntu (or others that use UID of 1000) that a separate data partition saves on duplicate data. The only duplication I have is the user settings in /home which is tiny and my .wine which I understand is difficult to move. My total root with /home is about 7GB, but I have 100MB data partition that is ext3 and another that is NTFS for sharing with my old XP which I use very little now.

I still have unallocated space on my 640GB drive as I keep adding 25GB / partitions for each new install. But now I have an SSD so my new install is now there.

You should have a current version liveCD or Windows repairCD for every system you have installed just so you can make repairs. I have several flash drives with ISOs including other repair ISO like gparted, knoppix, siltaz.

---

### Post by bobman321123 on 2012-03-30
I don't actually have any windows repair software or cds, so could I just delete it entirely? 

Do harddrives have a problem supporting a drive with no primary partitions?

Proposed solution (from answers):
Delete sda1, 
extend extended partition system to fill up the space
Move Ubuntu's around in the extended partition from there.
Sound good?

---

### Post by bobman321123 on 2012-03-30
Scratch my previous post, I had a new plan/idea/thingy (which oldfred suggested) :P

How would I make a 350-400gb raw data partition, with a seperate, smaller partition for each install of an operating system?

Oldfred, how do you do it?

---

### Post by oldfred on 2012-03-30
I normally suggest at least one primary partition. There are some BIOS (Intel motherboards?) that will not even let you start to boot unless you have a primary partition with a boot flag. That is a Windows requirement, grub does not need it. You can have all logical if your BIOS is like most.

Separate Data partitions:
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by bobman321123 on 2012-03-30
> **oldfred said:**
> I normally suggest at least one primary partition. There are some BIOS (Intel motherboards?) that will not even let you start to boot unless you have a primary partition with a boot flag. That is a Windows requirement, grub does not need it. You can have all logical if your BIOS is like most.

Separate Data partitions:
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

So, I've formatted my sda1 to ext4, how do I make it my /data folder or partition( or whatever else it could be)?

---

### Post by bobman321123 on 2012-03-30
I read some of the other postings, messed around messed up, fixed my messing up, and kindasorta got it working. /mnt/data now links to the other partition, is there a way to make the "Data" folder show up in the sidebar?

---

### Post by oldfred on 2012-03-30
If you just want /data in the side bar you should mount it in /media or directly in /home. I purposely mount it in /mnt so it is not in the side bar but then link all the folders in /mnt/data into my /home replacing some of the default like Music, Documents etc (once I am sure the defaults are empty or copied into /data).

I have many folders in /mnt/data and originally I was doing the linking one by one. Then I found a nice little script that does it all at once. The one's that are the same name have to have been renamed or deleted from /home first.

sudo mkdir /mnt/data
sudo chown $USER:$USER /mnt/data
#sudo chmod 766 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data

sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

#Edit fstab with your UUID:
```
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext4         auto,users,rw,relatime               0  2 

```
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by bobman321123 on 2012-03-30
Ok thanks! :D
That worked great! 
Thanks for all your help.
Marked as solved.

---

