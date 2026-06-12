---
title: "Common storage partition for dual boot Win7 &amp; Lubuntu?"
date: 2011-12-18
forum: General Help
---

### Post by 2009Prius on 2011-12-18
I just managed to set up dual boot of Win 7 Starter and Lubuntu on a netbook. I tried various ways to pass files back and forth between Win and Lubuntu without success. 

I first tried using an NTFS partition on the hard drive as the common storage. The Lubuntu side can see all the files from the Win 7 side and can make new files or make changes to existing files. But the Win 7 side can not see the new files or the changes. Also Win 7 chkdsk comes back with errors. I checked and found ntfs-3g is installed already.

Then I tried a SDHC card formatted as FAT32. It has read errors on some files when trying to read from the Lubuntu side. Also the disk appears as read only on the Lubuntu side thus can not be changed, i.e. can not copy file to the SDHC card from the Lubuntu side.

Ideally I would like to be able to work on one side, then hibernate, then turn on the PC and boot into the other side to work, then hibernate, then turn on the PC and boot into the first OS, then ... etc. But so far I don't have good luck with either NTFS or FAT32.

Please help! Thanks!

---

### Post by xyzzyman on 2011-12-18
Have you tried the NTFS without hibernating the OS's? I have just a 320GB partition in my notebook, and I run Ubuntu, Arch & Windows 7. So I have 2 NTFS partitions set up for storing my data between the 3. Never had a problem.

---

### Post by 2009Prius on 2011-12-18
Thanks for the quick reply! No I haven't tried rebooting. Hibernation is really much more preferred since I don't have to re-open various programs and re-arrange their windows (within the small real estate of a netbook screen) each time I switch the OS. Thanks!

---

### Post by wildmanne39 on 2011-12-18
Hi, I have read in other threads that hibernating and not shutting down completely to boot the other operating system can cause a severe crash in both systems.

---

### Post by xyzzyman on 2011-12-18
The best explanation is that part of the file system table is always in memory. So when you hibernate, the drives aren't being unmounted. The other OS opens the drive, and even minimal changes throws everything off the next time you're in the other OS (assuming you don't already have problems.) You're seeing that already. Windows thinks the file system looks one way, you pause it, linux makes changes, windows wakes up and everything is different but it doesn't know it. It's like a blind person going to sleep, you sneak in and rearrange all the furniture in his house... When he wakes up he thinks things are the way they were last night.

On the SDHC, you can try unmount it before hibernate (In windows you 'safely remove usb device' I think it's called.) Remember if you want larger files you'll need to use NTFS.

---

### Post by 2009Prius on 2011-12-18
Thanks! I guess that makes sense but it's also amazing that in the 21 century the OS is still so dumb that it can't refresh the content of the disk unless it's unmounted and re-mounted (in the case of SDHC it would need physically eject and re-insert the card, adding to the wear and tear and I suppose in the case of HDD it's impossible for Win 7 to "eject" the drive). :(

---

### Post by xyzzyman on 2011-12-18
You shouldn't have to physically eject the SDHC. Just right click and choose the option, but then leave it physically in the slot.

---

### Post by 2009Prius on 2011-12-19
> **xyzzyman said:**
> You shouldn't have to physically eject the SDHC. Just right click and choose the option, but then leave it physically in the slot.

But how do I re-mount it without physically ejecting and re-inserting under Win 7?

---

### Post by Mark Phelps on 2011-12-19
You can't use the Windows partitions for sharing data if you Hibernate -- that's the way Hibernation is DESIGNED to work.  It will restore the partitions to the state they were in when Win7 was hibernated.  Thus, any changes you made to the partition contents while Win7 was hibernated will be lost when Win7 is awakened from hibernation.

If you want to use the partitions for sharing data, you must turn off hibernation.

You can't have it both ways.

---

### Post by 2009Prius on 2011-12-19
After Windows wakes up from hibernation, why can't it **take a look at the hard disk** and see that some files have changed and some new files have been added? :confused:

Two programs can do this easily. Here is an example. I can edit a file using Notepad. Then when I switch to, say, BeyondCompare, that **already had the same file open**, it would ask me that the file has changed on the disk and whether to reload the file or not.

What makes it so difficult for two OS' to do the same? :confused: All the file info is written to the hard disk physically, right? Why is it so hard to take a look and find something changed? :confused: (Maybe that's why it's called a **hard **disk - short for "hard to read" disk? ;))

---

### Post by xyzzyman on 2011-12-19
> **2009Prius said:**
> After Windows wakes up from hibernation, why can't it **take a look at the hard disk** and see that some files have changed and some new files have been added? :confused:

Two programs can do this easily. Here is an example. I can edit a file using Notepad. Then when I switch to, say, BeyondCompare, that **already had the same file open**, it would ask me that the file has changed on the disk and whether to reload the file or not.

What makes it so difficult for two OS' to do the same? :confused: All the file info is written to the hard disk physically, right? Why is it so hard to take a look and find something changed? :confused: (Maybe that's why it's called a **hard **disk - short for "hard to read" disk? ;))

Everything would have to be rewritten for this in mind. OS's, drivers, file systems, all your programs. You would have to keep much more information in memory, and how do you account for just a few characters changing in a file? Keep an MD5 sum of every file in real-time? From now on everytime you go to sleep at night, make sure you check nothing in your house was moved the night before. Not even someone swapping DVD's between cases. ha I also don't think you know what hibernate is. It's taking a snapshot of your RAM exactly the way it is. All the different services and programs and DLL's. They don't know they've been hibernated. That's why it can be so quick. It's not doing all the check and other stuff. If so you might as well cold boot.

---

### Post by 2009Prius on 2011-12-19
> **xyzzyman said:**
> Everything would have to be rewritten for this in mind. OS's, drivers, file systems, all your programs. You would have to keep much more information in memory, and how do you account for just a few characters changing in a file? Keep an MD5 sum of every file in real-time? From now on everytime you go to sleep at night, make sure you check nothing in your house was moved the night before. Not even someone swapping DVD's between cases. ha I also don't think you know what hibernate is. It's taking a snapshot of your RAM exactly the way it is. All the different services and programs and DLL's. They don't know they've been hibernated. That's why it can be so quick. It's not doing all the check and other stuff. If so you might as well cold boot.

I am not saying every program has to check the hard disk all the time, nor am I saying hibernation should go beyond saving the RAM to disk. All I am asking is, say, when I click the "refresh" button in Windows Explorer or File Manager, the OS would kindly go to the hard disk and see if some file has changed. Again, how does BeyondCompare or Notepad++ know that an open file has be changed outside of the program? Why can't Windows Explorer do the same?

---

### Post by xyzzyman on 2011-12-19
> **2009Prius said:**
> I am not saying every program has to check the hard disk all the time, nor am I saying hibernation should go beyond saving the RAM to disk. All I am asking is, say, when I click the "refresh" button in Windows Explorer or File Manager, the OS would kindly go to the hard disk and see if some file has changed. Again, how does BeyondCompare or Notepad++ know that an open file has be changed outside of the program? Why can't Windows Explorer do the same?

You're confusing Windows Explorer with the underlying operating system and file structures. If it's a simple thing for windows explorer to handle your problem, download [http://surf.svprogramming.net/](http://surf.svprogramming.net/) which is an open source file manager for Windows and make the changes. BeyondCompare being notified of a file change in a current session is unrelated to how it works. Hibernation was added over a decade after these systems were designed, so it has to operate around that pre-existing model without changing everything. And if you're going to rewrite all that, might as well just write one OS so you don't dual-boot.

---

### Post by Synoc on 2011-12-20
I envision bad things for a pc to wake up and ifs environment has changed and jounaled file systems woild be scarier, such as ntfs and ext4. Like have three bosses with 4 ways for to go about your job. Someone is getting fired. What need ix ghere for three OSs? Maybe we can kill the underlying problem?

---

### Post by xyzzyman on 2011-12-20
BeyondCompare and Notepad++ both work in Wine. Depending on his amount of ram maybe he could also use virtualbox in seamless mode.

---

### Post by 2009Prius on 2011-12-20
Thanks! I am developing open source software for both platforms so that's why I need to switch back and forth. For now I just use the FAT32 formatted SDHC card that seems to be working (crossing my fingers).

---

### Post by killermist on 2011-12-20
> **2009Prius said:**
> After Windows wakes up from hibernation, why can't it **take a look at the hard disk** and see that some files have changed and some new files have been added? :confused:

Two programs can do this easily. Here is an example. I can edit a file using Notepad. Then when I switch to, say, BeyondCompare, that **already had the same file open**, it would ask me that the file has changed on the disk and whether to reload the file or not.

What makes it so difficult for two OS' to do the same? :confused: All the file info is written to the hard disk physically, right? Why is it so hard to take a look and find something changed? :confused: (Maybe that's why it's called a **hard **disk - short for "hard to read" disk? ;))

One thing about hibernation that isn't often considered is that hibernation is intended for computers with only one OS installed.  If something has changed the contents of drive while the computer was "sleeping" then it is manifest evidence that something is catastrophically wrong with the hardware because the computer was supposed to be asleep.

There MAY be other implementations of hibernation (probably not called hibernation) that don't make the assumption of [computer should have been sleeping], but trying to resume a running instance of the OS from a partition that has been modified is ... dangerous at best.

---

### Post by 2009Prius on 2011-12-20
No the OS partitions are not changed, only the (separate) storage partition is changed.

---

### Post by Mark Phelps on 2011-12-20
> **2009Prius said:**
> After Windows wakes up from hibernation, why can't it **take a look at the hard disk** and see that some files have changed and some new files have been added? :confused:
Because ... that is NOT how Hibernation works.  You can't expect a basic function like Hibernation to do just what YOU want.

> What makes it so difficult for two OS' to do the same? :confused: All the file info is written to the hard disk physically, right? Why is it so hard to take a look and find something changed? :confused: (Maybe that's why it's called a **hard **disk - short for "hard to read" disk? ;))
NO -- it's called "hard" disk to distinguish it from what used to be common -- "floppy" disks.

You're asking for something very different from how Hibernation is designed to work -- so, either quit using Hibernation, or get used to how it is supposed to work.

---

### Post by 2009Prius on 2011-12-20
It's funny how people dug up old posts and start ... without looking through the thread. Again I am not asking the hibernation mechanism to magically detect changes on the hard drive. I am just wondering why Windows Explorer does not take a look at the hard drive when I click the **refresh **button after waking up from hibernation. How good is "refresh" then?

Another thought: Is it possible that LUbuntu does not write all the necessary indexing info on the NTFS partition? I vaguely remember there are two tables. Maybe Lubuntu only write one and neglect to write the other?

---

### Post by xyzzyman on 2011-12-20
Not everything is written until the drive is unmounted. I normally rip out memory cards and USB drives, but last week for some reason I decided to properly eject it for some reason and it actually took about 20 seconds writing data and the writing LED on my USB drive kept blinking. Go figure. I was running on battery so I think it holds more in RAM to minimize writes.

---

### Post by 2009Prius on 2011-12-20
Thanks! Is it possible to unmount an NTFS partition on an HDD in Win 7? I right click on a drive but there is no unmount or eject in the menu.

---

### Post by killermist on 2011-12-20
To unmount a "system" drive (which is to say the partition holding the kernel and most of the OS) in windows, I don't think is possible, without doing a full shutdown.

As was recommended earlier, I would shrink the existing partitions to free up some space and create an additional (NTFS or fat32 probably) common partition to pass files and stuff back and forth.
That partition, not being a "system" partition should be dismountable so it can be safely used by both.  (though I still think that using hibernation to get "more quickly" back and forth is a bad idea, just my opinion though)

---

### Post by xyzzyman on 2011-12-20
You have to go into disk management to unmount drives in Windows. And you can't unmount the system partition. There is probably a way to do it via command line and make a batch file. It's not as quick to mount/remount though as Linux for fixed drives.

---

### Post by 2009Prius on 2011-12-21
> **xyzzyman said:**
> You have to go into disk management to unmount drives in Windows. And you can't unmount the system partition. There is probably a way to do it via command line and make a batch file. It's not as quick to mount/remount though as Linux for fixed drives.

Thanks! I just went into Disk Management and the closest option of actions is "Delete Logical Drive ..." which I am afraid of clicking on.

---

### Post by killermist on 2011-12-21
It's been so long since I've administrated a Windows system.
I know that with actual removable drives, the dismounting process is fairly trivial.
I don't recall what the process is for partitions on internally mounted drives (IDE, SCSI or SATA channels).

[edit]
An option to consider would be to craft a NAS that can share with samba to windows or nfs/sftp/ssh to linux.  This would also save the issue of having to dismount manually...
FreeNAS ([http://wiki.freenas.org/](http://wiki.freenas.org/) , version 7 series) works great with "legacy hardware" to easily create a file storage server.

---

### Post by Mark Phelps on 2011-12-22
> **2009Prius said:**
> Thanks! Is it possible to unmount an NTFS partition on an HDD in Win 7? I right click on a drive but there is no unmount or eject in the menu.

All that Win7 allows, using Disk Management, is mounting or unmounting an entire "drive" -- physical device.

If you click on the box containing the drive name, you will see an Offline option.  That is essentially the same as Unmount.

But, you can't do it for individual partitions.

---

### Post by killermist on 2011-12-22
> **Mark Phelps said:**
> But, you can't do it for individual partitions.

This kind of reinforces the options of use a NAS or a USB secondary drive as the "common storage" option.

I've said before and I'm sure I'll say again, Windows sucks.

---

### Post by xyzzyman on 2011-12-23
> **Mark Phelps said:**
> All that Win7 allows, using Disk Management, is mounting or unmounting an entire "drive" -- physical device.

If you click on the box containing the drive name, you will see an Offline option.  That is essentially the same as Unmount.

But, you can't do it for individual partitions.

Wrong. 

[QUOTE=MS Technet]A volume with no designators is considered to be unmounted.[/QUOTE]

They use 'designators' to mean drive letter. Which you can remove and change in the same spot.

Hence why both OS's have their problems and suck.

---

### Post by killermist on 2011-12-23
> **xyzzyman said:**
> Hence why both OS's have their problems and suck.

Linux (unlike windoze) can reference partitions by UUID quite easily, making USB and external drives (or internal partitions) very easy to designate and mount/unmount.
This puts it head, shoulders, torso, and upper legs above windows which assumes itself to be the exclusive user of ALL the disc-resources, exclusively.

Again, and back to the topic at hand, I recommend using a NAS to store the files needed for both windoze and linux, especially as this frees you to completely nuke and reinstall the "client" machine with whatever you want whenever you want.

---

### Post by xyzzyman on 2011-12-23
Most people don't want to run a NAS and waste electricity. When I was 14 I thought it was cool to run an old 486 as my router and file server, until I started working for a living and the electric bill would come and I could see how wasteful I was and just feeding the electric companies. It's also why I realized that wiping and reinstalling the OS every 6 months to a year (Windows 98 seemed monthly) was a waste of time and I had to start getting a life and becoming active instead of sitting on the computer.

No matter the OS, no one should ever have to worry about the UUID's unless they're developing the OS itself. When you're using the system it's a tool whether it be for entertainment, communication, research. Now that I'm 30 and have lymphoma I look back in disgust at all the time I wasted editing configuration files just to make something work in Linux or as simple as fonts smoothing well. I know how to do it but you shouldn't have to.  Hence, why all OS's suck. Although it probably makes sense why iOS and tablets are becoming so popular, the majority of people just want their tools to work. Get on, do what you want, and go. It's been overkill how quickly they keep releasing new devices. People complain about Unity sometimes with Ubuntu, but they're the 1% and using Unity full-time since August it seems like Mark Shuttleworth is moving in the right direction.

---

### Post by 2009Prius on 2011-12-23
> **xyzzyman said:**
> Most people don't want to run a NAS and waste electricity. ....I didn't know that but I guess it makes sense.
> ....No matter the OS, no one should ever have to worry about the UUID's unless they're developing the OS itself. When you're using the system it's a tool whether it be for entertainment, communication, research.I can't agree more!
>  Now that I'm 30 and have lymphoma...Really sorry to hear and hope you get better soon.
> ... It's been overkill how quickly they keep releasing new devices.It's still a culture shock for me to see brand new digital camera would become obsolete in 6 months, and software company comes up with a new version every 6 months.

---

### Post by xyzzyman on 2011-12-23
> **2009Prius said:**
> I didn't know that but I guess it makes sense.
I can't agree more!
Really sorry to hear and hope you get better soon.
It's still a culture shock for me to see brand new digital camera would become obsolete in 6 months, and software company comes up with a new version every 6 months.

A NAS is a network accessible storage device. Easiest way to think about it is instead of having an external USB drive, you've got a glorified router with a few hard drives in it that acts like a mini-server on your network. Alot of them now use the atom processors that are in the netbooks or the equivalent from AMD. They are a lot better than running a full desktop 24/7 just to always have your files on. I bet if you go to Best Buy they've sold alot more Roku boxes for streaming from the cloud than NAS's. :) (I once sold my soul to a big-box store **sniff sniff** I did learn to stop thinking like a nerd with brand biases and think like a regular everyday person. So many kids would want to work there but they'd be like, "I'd never let anyone buy a Dell" but they'd recommend a Gateway that has the same parts inside. Or they would think they would talk everyone out of getting a system with an integrated video card... Well sorry. I actually had my grandmother get a $299 tower/monitor/printer package years ago made my emachines that my father uses now. Would we go crazy using the system? Yes. It's an f'n celeron so even with RAM it's not responsive enough. My grandmother though thought it was amazing. And building an equivalent system ordering everything from New Egg was within $30 once a copy of windows oem was factored in. I used to ask the really bad salesman we'd get what sort of pots and pans they used and bakeware. If they owned any there were always cheap crap. So I'd just turn it on them because I'm kinda a snob when it comes to my kitchen stuff. Sometimes they got the point. 

And instead of looking at the cameras as obsolete, look at it as not having to wait as long for clearance to come around! 

But anyways, as asked before what programs do you run on each OS that you can't do on the other? Maybe we'll know of something. The fact you're running on a netbook limits the kind of programs so maybe you'll be lucky and they'll run under wine with no configuration.

---

