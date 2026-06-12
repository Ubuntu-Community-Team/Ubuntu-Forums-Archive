---
title: "Partition removed by windows recovery partition"
date: 2011-01-28
forum: General Help
---

### Post by samskiter on 2011-01-28
Hey, I would really appreciate some help with this, heres the story


[LIST]
[*]My set up is a dual boot between windows 7 and ubuntu 10.04. This laptop used to have vista on it. See image below for my partition set up. pretty obvious where ubuntu should be.
[*]I accidentally selected the wrong entry in grub and booted into an acer windows recovery partition. despite exiting as soon as it loaded, the long story short is that it has goodbyed linux.
[*]On booting i now just get a grub rescue prompt.
[*]I have eventually managed to boot into a liveUSB (cd drive is botched too :( )
[*]As you can see from the screenpic, testdisk shows linux is still there but there are quite a few entries from the upgrades.
[/LIST]
So, if i can restore the partition around this linux partition will grub come back with it and will all be merry?

I havent mounted any volumes on the drive yet, but i think i need to back up my data before messing with the partition table. is it cool to mount them to pull some data off?

general advice for how to proceed would be great.

Im not too hung up on keeping the linux install itself. whats gunna be easier? install into that 16gb space and then re add windows to grub, or try and recover this partition?

and yes, im gunnna blitz those recovery partitions when im done! :mad:

thhanks for any help,

sam

forgot the pic!

[http://img207.imageshack.us/img207/2397/screenshothm.png](http://img207.imageshack.us/img207/2397/screenshothm.png)

---

### Post by samskiter on 2011-01-28
is there another part of the forum that would be better to place this?

---

### Post by lisati on 2011-01-28
> **samskiter said:**
> is there another part of the forum that would be better to place this?

No, you're in the best place: please be patient.

Among the questions the team might ask are, do you have a backup of your important data from your Ubuntu partition? If so, a fresh installation might be the easiest.

---

### Post by samskiter on 2011-01-28
yea, like i say im not too hung up on it, i dont need much of it. but if i can stick all the partitions back in without too much trouble, it would be nice

---

### Post by oldfred on 2011-01-28
Those are not different partitions but the partition history of your system. Most of them have start & ends that are only 1 or 2 sectors apart so it looks like you made minor adjustments several times.

---

### Post by steveneddy on 2011-01-28
IMHO - instead of dual booting - with such great strides in Virtual Machines, just install Ubuntu as the main OS and let Windows run in a VM - this is the way I run Win 7 (so I can have iTunes for my iPhone) and it works perfectly.

You have more control over Windows using this method and you don't have those messy partitions to worry about anymore.

---

### Post by Primefalcon on 2011-01-28
use a live disk and hav a look with gparted to see if the partition really is gone, if it isn't (windows had a habit of overwriting the main boot record)

this will help you there: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

if the partition really is gone, you can use a program called test disk, load up a live disk and run the command ```
sudo apt-get install testdisk
```, then run testdisk and search for your partition and restore, be careful here though....

testdisk is menu driven so should be pretty easy, I had no problems with it, of course do all this from a livedisk

---

### Post by samskiter on 2011-01-28
> **oldfred said:**
> Those are not different partitions but the partition history of your system. Most of them have start & ends that are only 1 or 2 sectors apart so it looks like you made minor adjustments several times.
the multiple entries of linux occured after updates, this was not something i manually did. my grub menu grew over time with more and more linux entries after big updates :S

> **steveneddy said:**
> IMHO - instead of dual booting - with such great strides in Virtual Machines, just install Ubuntu as the main OS and let Windows run in a VM - this is the way I run Win 7 (so I can have iTunes for my iPhone) and it works perfectly.

You have more control over Windows using this method and you don't have those messy partitions to worry about anymore.

a valid point, althought a VM in windows might be more appropriate in my case.

> **Primefalcon said:**
> use a live disk and hav a look with gparted to see if the partition really is gone, if it isn't (windows had a habit of overwriting the main boot record)

this will help you there: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


i think windows has messed with the MBR yes. but the drive is definitely not mountable, it is showing as empty!
> 

if the partition really is gone, you can use a program called test disk, load up a live disk and run the command ```
sudo apt-get install testdisk
```, then run testdisk and search for your partition and restore, be careful here though....

testdisk is menu driven so should be pretty easy, I had no problems with it, of course do all this from a livediskmy OP mentions using testdisk and shows a screenshot of its output. some guidance on how to proceed would be appreciate (there sound to be a lot of options and questions coming up)

final output of testdisk: [http://img337.imageshack.us/img337/6349/screenshot1mo.png](http://img337.imageshack.us/img337/6349/screenshot1mo.png)

if i mount the volumes from drive to remove data from my other partitions, do i risk altering these results?
[URL="http://img337.imageshack.us/img337/6349/screenshot1mo.png"]
[/URL]

---

### Post by samskiter on 2011-01-29
> **samskiter said:**
> the multiple entries of linux occured after updates, this was not something i manually did. my grub menu grew over time with more and more linux entries after big updates :S[URL="http://img337.imageshack.us/img337/6349/screenshot1mo.png"]
[/URL]
ive just seen another thread about this. its something to do with the different kernel numbers

[http://ubuntuforums.org/showthread.php?t=1652593](http://ubuntuforums.org/showthread.php?t=1652593)


for my problem, essentially i need some guidance about using testdisk, the risks involved and how how to add the partitions in with these multiple linux entries

---

### Post by Quackers on 2011-01-29
This may help :-)
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by samskiter on 2011-01-30
gave up on trying to get the partitions back and clean installed 10:10. got to mess about loads setting everything up again now.

thanks for the help, pity i couldnt get testdisk to undo the damage.

sam

---

