---
title: "Partitioning Problem"
date: 2006-03-19
forum: General Help
---

### Post by sholdens12 on 2006-03-19
Please help: I have a Thinkpad T23. It had XP on it, and I installed 5.10 from an install disk, keeping XP. Everything was going fine. I was working on it. Then I decided to do an update. I got all the repositories and clicked everything. I guess I installed a new kernel. After I rebooted, nothing. No XP, no Ubuntu. In fact, there is no operating system at all on the computer. I reinstalled Ubuntu, but when I get to the partitioning screen, I can't do anything. Please help!

---

### Post by cilynx on 2006-03-19
Drop in a LiveCD and see what you've actually got left on the computer.  Most likely, your bootloader (GRUB) took a dump and all you have to do is set that back up.

---

### Post by sholdens12 on 2006-03-19
So if I burn a Live CD instead of the installer, I should be able to figure it out?

---

### Post by sholdens12 on 2006-03-19
I hate to sound stupid, but I am a complete newbie. Is there a way I could just reformat the hard drive and start over?

---

### Post by cilynx on 2006-03-19
You --can-- dump the system and start over, but I don't think you need to.  When you try to boot the machine right now, what is the error that it gives you?

---

### Post by sholdens12 on 2006-03-19
If I try to boot it without the Ubuntu install disk, I get this:

Intel Base-Code, PXE-2.1 (built 083)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel PXE ROM.
Operating system not found


If I boot up and start the Ubuntu install, it goes through everything normally up to the partitioning. It makes me Manually edit partition table. I click that.

I get this menu: 
Configure software RAID
Configure the Logical Volume Manager
Guided partitioning
Help on partitioning

Undo changes to partitions
Finish partitioning and write changes to disk.

I get no indication of any partitions already existing. So if I click on Configure software RAID, and try to keep the current partition layout and configure RAID, and try to create MD device, it says the following:

"No RAID partitions available. No unused partitions of the time "Linux RAID Autodetect" are available. Please create such a partition, or delecte an already used multidisk to free its partitions. If you have such partitions, they might contain actual file systems, and are therefore not available for use by this configuration utility."

That's about as far as I can go in the install. I end up just scrapping the install.

---

### Post by cilynx on 2006-03-19
I'm guessing you're not actually wanting to be playing with RAID.  What does it do if you try Guided Partitioning?

---

### Post by sholdens12 on 2006-03-20
It says: 

Disk space to partition:

And there's one option: Manually edit partition table.

And I end up back where I started.

---

### Post by sholdens12 on 2006-03-20
Anyone have a thought about this? I got in through a LiveCD, but I don't know what to do now....

---

### Post by sholdens12 on 2006-03-20
I'm still stuck. what can I do from the LiveCD?

---

### Post by ssalman on 2006-03-20
Try to mount your harddrive partitions and see if your files are still there. try both the windows partition and the ubuntu partition. our next step is based on what you find.

---

### Post by sholdens12 on 2006-03-20
I hate to sound like a complete idiot, but how do I mount my disks?

---

### Post by sholdens12 on 2006-03-20
I mean mount my partitions?

---

### Post by ssalman on 2006-03-20
Goto menu: System->Administration->Disks
Type your password
Select your harddrive and click on the partitions tab
Select your partition and fill an access path, ("/mnt" will work)
Click on enable

You should now have it mounted, go to your file browser (Applications->Accessories->File browser) and then on the left panle double click on "File System", then on the right panle double click on "mnt"

if your partitions are still okay, you should see your files here....

---

### Post by sholdens12 on 2006-03-20
No, unfortunately, that doesn't work. I have two disks: 
/dev/mapper/casper has one partition, "Partition per-snapshot," but it doesn't let me mount the drive.
tmpfs has no partitions.

Apparently my partitions are broken. Any thoughts?

---

### Post by ssalman on 2006-03-20
So you can't find a &#8220;/dev/hda1&#8221;?? 

I'm not sure what is missing here, I don't have a live CD with me now to boot and check what is the default behavior... the instructions I gave you were based on a HD boot, and I though it is going to be the same&#8230; maybe someone with more experience will drop in. Sorry I couldn&#8217;t help.

---

### Post by sholdens12 on 2006-03-20
Perhaps someone could explain to me how I could just wipe my hard drive clean so I can reinstall Ubuntu?

---

### Post by bittercold on 2006-03-20
Hi! yesterday I gave the same error as you describe. After a little work I saw that the HD of my laptop was not well installed, probably by the movement I don't know, so I open a small lid (the HD one) and put it at the correct position. And that's all. I'm sure that this is your problem, try it and say if you have solved the problem

---

### Post by RavenOfOdin on 2006-03-20
So this doesn't happen again in the future, I'll recommend that you get your hands on hard drive diagnostic tools.

If you're running Seagates, they should have some easily available from their site.

---

### Post by cilynx on 2006-03-20
Whether you're wiping clean or trying to recover what you had, you still have to go through the partitioner.  

When you go to "manually setup partition table", what does it offer you?

Another thing to possibly look at in the live system: If you do an "fdisk /hda" (assuming you're using IDE) and press 'p' for "print", what does it show for your partition table? (If you're using SCSI or SATA, you're probably looking at sda as opposed to hda.  'q' will get you out of fdisk)

---

### Post by sholdens12 on 2006-03-20
Cilynx, thanks for still checking up on me. I'm still having issues. 

When I go to "manually setup partition table," the overview of my partitions shows me nothing. Guided partitioning gives me nothing but the option to once again manually edit the partition tables.

When I'm in the live system, and I do fdisk /dev/hda, I get this: 

Disk /dev/hda: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders

Disk /dev/hda doesn't contain a valid partition table

Oy.

---

### Post by cilynx on 2006-03-21
That is not a good sign.  What is/are the hard drive(s) in your system?

---

