---
title: "VirtualBox XP: how do I swap hard drives around?"
date: 2011-04-03
forum: General Help
---

### Post by t0p on 2011-04-03
I've got VirtualBox on my Ubuntu computer, with guest additions and a virtual Windows XP.  Being a bit of an idiot, I allocated just 6GB for the C: drive, as a result of which it keeps filling up.

I have since created more drives - Local Disk (E: ) and Disk 2 (F: ) which each have 50GB.  What I want to do is make C: bigger, possibly by swapping it  with E:, so C: will have 50GB and E: will have the miserly 6GB.

Unfortunately I have no idea how to do this.  Can anyone help?

Cheers.

---

### Post by techunit on 2011-04-03
Such an awkward process in a vm, but because its WinXP boot the VM off a linux distro Ubuntu preferably and use gparted to increase the cdrives size. Good luck.

---

### Post by bodhi.zazen on 2011-04-03
> **t0p said:**
> I've got VirtualBox on my Ubuntu computer, with guest additions and a virtual Windows XP.  Being a bit of an idiot, I allocated just 6GB for the C: drive, as a result of which it keeps filling up.

I have since created more drives - Local Disk (E: ) and Disk 2 (F: ) which each have 50GB.  What I want to do is make C: bigger, possibly by swapping it  with E:, so C: will have 50GB and E: will have the miserly 6GB.

Unfortunately I have no idea how to do this.  Can anyone help?

Cheers.

There is no easy way to do this.

Best bet, IMO, is to boot the VM with any live CD, use gparted to copy the partition from the c drive to the e driver, and resize the partition to take up the remaining free space.

The shut down the machine and remove the previous, old, c drive.

HTH.

---

### Post by techunit on 2011-04-03
> **bodhi.zazen said:**
> There is no easy way to do this.

Best bet, IMO, is to boot the VM with any live CD, use gparted to copy the partition from the c drive to the e driver, and resize the partition to take up the remaining free space.

The shut down the machine and remove the previous, old, c drive.

HTH.
NO offence meant by this but wouldn't that create drive confusion in windows that would cause it to fail to boot. In gparted he should be able to delete the other partitions and increase the size of the C drive. It could take a long time though.

---

### Post by bodhi.zazen on 2011-04-03
> **techunit said:**
> NO offence meant by this but wouldn't that create drive confusion in windows that would cause it to fail to boot. In gparted he should be able to delete the other partitions and increase the size of the C drive. It could take a long time though.

Not sure if it would be a problem with Windows. I do not see why it would, but I am not very familiar with windows.

The current e drive is configured from the vbox admin panel so I do not see why it would be anything more then setting the drives in vbox.

---

### Post by robertcoulson on 2011-04-03
Hey t0p..I use virtual box and never had that problem, when I install ANY OS I use "expanding hard disk storage"...That way it keeps expanding and does not seem to get filled up..See attachment as to where I use "expanding hard disk storage"...I hope this is what you are talking about.
Robert

---

### Post by techunit on 2011-04-03
> **robertcoulson said:**
> Hey t0p..I use virtual box and never had that problem, when I install ANY OS I use "expanding hard disk storage"...That way it keeps expanding and does not seem to get filled up..See attachment as to where I use "expanding hard disk storage"...I hope this is what you are talking about.
Robert
The problem is he set the partitions inside of the vm smaller than they need to be. Not the size of the VM-HD

---

### Post by robertcoulson on 2011-04-03
Could he not delete XP and try reinstalling it..But the trouble I found while doing that is Virtual Box hides info in 2 different locations, one is easy to find and the other isn't...The one that is hard to find will hold the disk space forever even after you delete the OS through the GUI...Maybe his best bet IS to delete and reinstall.
Robert

---

### Post by techunit on 2011-04-03
> **robertcoulson said:**
> Could he not delete XP and try reinstalling it..But the trouble I found while doing that is Virtual Box hides info in 2 different locations, one is easy to find and the other isn't...The one that is hard to find will hold the disk space forever even after you delete the OS through the GUI...Maybe his best bet IS to delete and reinstall.
Robert
Why when he could consolidate? He has what he need to do it, I don't know why he wouldn't just merge the partitions. Unless I am missing something.

I often over complicate things so sometimes the simplest solution is the most annoying.

---

### Post by robertcoulson on 2011-04-03
Ya techunit, you may be right...The simple way is usually the easiest way.
Robert

---

### Post by t0p on 2011-04-04
Thanks for all the replies.  I don't have a live disk to hand, so I shall download the .iso later then try to resize the C: partition then.

But there's something I don't understand.  The C:, E: and F: drives aren't real drives or partitions - they are .vdi files, on an external dist drive,  in the directory .../VirtualBox/HardDisks.  So I don't see what a partition editor would do exactly.

So, the .../HardDisks directory contains 3 .vdi files: windows-xp1.vdi (the C:  drive, size 6GB), XP1HardDisk1.vdi (E: drive, size 50GB) and XP1HardDisk2 (F: drive, size 50GB).  Is it possible to swap things around, so windows-xp1.vdi became a 50GB file and one of the others becomes the 6GB file?

Please forgive me or my ignorance in these matters.  Cheers!

---

### Post by howefield on 2011-04-04
You could use Clonezilla to clone the 6gb to one of the larger virtual drives. 

I can't remember if Clonezilla will take up all the new drive or whether it will appear a 6gb and the rest unallocated, if this is the case, gparted should sort you out with resizing.

---

### Post by NadirPoint on 2011-04-04
When you reinstall XP in a new virtual machine, allow it to set dynamic disk space for the Windows C: drive on a pre-existing (hopefully large) Linux partition.

Is it possible to enable this setting on an existing virtual machine Windows drive?

---

### Post by timgood on 2011-04-04
> **robertcoulson said:**
> Hey t0p..I use virtual box and never had that problem, when I install ANY OS I use "expanding hard disk storage"...That way it keeps expanding and does not seem to get filled up..See attachment as to where I use "expanding hard disk storage"...I hope this is what you are talking about.
Robert

Dynamically expanding storage does not keep expanding - only up until the maximum size specified when you create the VM. If you want to expand the size of the disk after that, you need to use ```
vboxmanage modifyhd .VirtualBox/HardDisks/<nameofyourharddrive>.vdi --resize <size in KB>
```. In other words, if your VM hard drive is called WinXP and you want to make it 10GB in size, you would use ```
vboxmanage modifyhd .VirtualBox/HardDisks/WinXP.vdi --resize 10000
```. You then need to boot from a boot disk with a partition manager on it and resize the partition to fill up the empty space. tOp could use the same method to resize the existing C drive on his VM and then delete one of the other drives.

Hope this makes sense.

---

### Post by NadirPoint on 2011-04-04
I've only done this a couple times, so that's why I asked.  Sounds like you set the max size on install to constrain it, and then it expands to fill that as needed.

Is that what we're saying?

---

### Post by timgood on 2011-04-04
> **NadirPoint said:**
> I've only done this a couple times, so that's why I asked.  Sounds like you set the max size on install to constrain it, and then it expands to fill that as needed.

Is that what we're saying?

Indeed. Suppose on installation you choose dynamically expanding storage with a max size of 10GB, but you only use 4GB for the installation. The file size of the HD reported to the VM will be 10GB, but the file size of the .vdi file on your Linux box will only be 4GB. This will expand up to the 10GB limit as you fill it with data. Once you are nearing the 10GB limit you will receive 'disk nearly full' messages on your VM and may then need to either delete files to create space or resize the .vdi to a larger size. The advantage of using dynamically expanding storage is that it only uses the actual amount of data stored on the host machine. You could have a VM disk of 100GB but only use 6GB of storage on your host.

Hope this makes sense.

---

### Post by t0p on 2011-04-07
> **timgood said:**
> Dynamically expanding storage does not keep expanding - only up until the maximum size specified when you create the VM. If you want to expand the size of the disk after that, you need to use ```
vboxmanage modifyhd .VirtualBox/HardDisks/<nameofyourharddrive>.vdi --resize <size in KB>
```. In other words, if your VM hard drive is called WinXP and you want to make it 10GB in size, you would use ```
vboxmanage modifyhd .VirtualBox/HardDisks/WinXP.vdi --resize 10000
```. You then need to boot from a boot disk with a partition manager on it and resize the partition to fill up the empty space. tOp could use the same method to resize the existing C drive on his VM and then delete one of the other drives.

Hope this makes sense.

Thanks for the response timgood.  But I have a problem: the command **vboxmanage** doesn't exist on my system.  If I try to run that command I get the following response:

```

The program 'vboxmanage' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose

```

You see, I don't have the open source edition of virtualbox.  I installed the closed-source version for its usb support (the main reason I use vbox at all is to print stuff, as my printer won't play nice with ubuntu).

---

### Post by timgood on 2011-04-07
I also use the 'closed source' version of VirtualBox. Try ```
VBoxManage
``` (note that Linux is case sensitive) instead of vboxmanage and tell me what happens.

More info on VBoxManage can be found [here]("http://www.virtualbox.org/manual/ch08.html").

Have Fun!

---

### Post by NadirPoint on 2011-04-10
Hey Tim, I just confirmed your CL after expanding the .vdi my daughters have been using up too quickly with their iTunes music.

Thanks!

---

### Post by t0p on 2011-04-11
Hey everyone!  Thanks for all the comments and suggestions.  I haven't tried any of the suggested fixes yet because I'm not geographically close to the computer in question.  I wouldn't want anyone to think I'm not grateful for the help.

When I get back home and have a little spare time I will see what works.  And I shall post here to let you know which solution worked for me.

Cheers.

---

### Post by NadirPoint on 2011-04-11
Be aware that you must also expand the partition from within Windows itself or otherwise utilize the additional unallocated space "after" you have told Virtualbox the max size it can be with the VBoxManage command.

---

