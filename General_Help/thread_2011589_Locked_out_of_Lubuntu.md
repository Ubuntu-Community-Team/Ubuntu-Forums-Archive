---
title: "Locked out of Lubuntu"
date: 2012-06-27
forum: General Help
---

### Post by kthalu on 2012-06-27
I hope someone can guide me in the right direction.

I have a bunch of laptops (40-50) that are being used for a kids computer camp. They do animation, create games, make movies etc.

One "solution" a bunch of us came up with was to use VirtualBox. The guest OS being XP. Then all we have to do for each camp is to copy & replace the virtual disk over every 2 weeks. 

I tried the virtualbox forums and got somewhat of a helpful answer but nothing they can resolve. "a full disk is a full disk" which I do understand, but not sure how it happened.

The virtual disk takes up about 25-26G of drive space and is non-expandable.  the laptop drives are 72G, 58G and 35G. with 28-29G of used space when the virtual disk is copied over. nothing else is installed. this is a clean lubuntu installation. my free space will be, 3.8G, 24G and 43G on each drive once i copy everything over.

Now they are getting locked out, username and pw will not work. I am able to get into tty. I was told to do df -h and found that I have NO space left anymore. even on the 72G drives.

Is there something that I can do to free up space? Maybe a cache I can clear? A setting to prevent virtual box from using up the hosts space? I just can't see how a virtual disk is creating this issue and where it may be putting files when the kids save their work on the virtual drive or a flash drive. most of them have no idea they are using lubuntu. they only see XP.

any help is greatly appreciated. thanks.

---

### Post by dino99 on 2012-06-27
as i understand your issue, you may have created too narrow xp.vdi partition under virtualbox, nothing to be scared about. Delete it and create a new one, adding your cloned image.

[http://www.addictivetips.com/windows-tips/create-disk-image-clone-hard-disk-partition-with-ubuntu-live-usb/](http://www.addictivetips.com/windows-tips/create-disk-image-clone-hard-disk-partition-with-ubuntu-live-usb/)

---

### Post by kthalu on 2012-06-27
thanks for the reply!

so how can I avoid this with the other laptops that are currently working?

could there be something that they are doing in VB/XP that is taking up the space? maybe a usb camera recording something?

i'm close to reinstalling xp on all these machines with the 20g of software. not a happy week.

---

### Post by zero2xiii on 2012-06-27
Hay,

To see what eats up the space to give a beter diagnostic folow this:

```
 du -hc --max-depth=1 /
```
```
 du -hc --max-depth=1 /home/$(whoami)
```

And so forth. Folowing the directories with abnormaly large sizes.
(the max depth is just to keep the output manageble since the tool du is already recursive by nature.)

Assuming it IS the VM image that eats the drive space. You will see a directory bigger than the drive created (assuming you set it to allocate the space on creation) and then finaly the file. (there are easier ways, but it would require to install some tools and it sounds like there is no space for this.

An example will look like this:

```
 du -hc --max-depth=1 ./ISO\ files/
4,6G	./ISO files/Linux
853M	./ISO files/Other
1,2G	./ISO files/Windows
6,5G	./ISO files/
6,5G	total

```

This shows us the directory "Linux" is huge (4.6GB)
Now lets look inside:
```
 du -hc --max-depth=1 ./ISO\ files/Linux
```
```
4,6G	./ISO files/Linux
4,6G	total

```

Now we see no directories INSIDE the Linux directory. To see the size of the FILES inside a directory use:

```
cd /ISO\ files/Linux #only for my example. I cd to the directory.
```
```
ls -goh1 ./
```
```
-rw-r--r-- 1 105M Oct 22  2011 clonezilla-live-20110922-natty.iso
-rw-r--r-- 1 687M Dec 15  2010 ubuntu-10.04.1-desktop-amd64.iso
-rw-r--r-- 1 690M Jul 15  2010 ubuntu_10.04_LTS_alt-install.iso
-rw-r--r-- 1 693M Dec  1  2010 ubuntu-10.10-alternate-NO-GUI.iso
-rw-r--r-- 1 699M May  8 03:07 ubuntu-12.04-desktop-amd64.iso
-rw-r--r-- 1 1,8G Jul  9  2011 ubuntustudio-10.04-alternate-amd64.iso

```

This shows the files inside the directory with their respective sizes in the third column.

So to recap: (in my example)
```
du -hc --max-depth=1 / #note this scans root
cd /home
du -hc --max-depth=1 ./ #note this scans current directory
cd ./$(whoami) #changes to directory INSIDE current directory. Stops me from typing the entire path each time
du -hc --max-depth=1 /
cd ./ISO\ files
du -hc --max-depth=1 /
cd ./Linux
ls -goh1 ./
```

You can replace the max depth with 2 for example to go quicker, but it generates a LOT of output if you have busy directories in your current location.

This will help you identify abnormaly large folders/files and root the problem. I have had lock outs due to numerous reasons that ate my drive's free space. Snapshots come to mind when working with VM's.

Hoping this isn't OVER complicating the matter.:lolflag:
Cherz

---

