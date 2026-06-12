---
title: "Extending Ubuntu Partition"
date: 2010-11-30
forum: General Help
---

### Post by MarkVLK on 2010-11-30
Hey everyone,

I'm a new Ubuntu user, I just bought this Asus Eee PC 1001PX-MU27 last weekend and it came installed with Windows 7 Starter. I partitioned the drive and installed Ubuntu 10.10 so I'm now dual-booting the two OS's. I'd like to expand my Ubuntu partition now because I have a large amount of the hard drive that is listed as unallocated but am unable to extend my Ubuntu partition into that area as I would like to.

Here's what happened:

The computer came with a 160 GB hard drive split into 2 partitions. One held Windows, and the other was to be used for recovery. The Windows partition was 80 GB and the recovery partition was about 50 GB. I wanted to split up the Windows partition so that 50 GB was allocated for Windows and 30 GB was allocated for Ubuntu, so I partitioned it and then had a 50 GB partition with Windows, a 30 GB partition that was unallocated, and a 50 GB partition for recovery.

I used Netbootin and ran the Ubuntu installation off a USB drive, but when it booted it wouldn't let me install Ubuntu on the 30 GB unallocated partition I had just freed up so I had to use 30 GB from the 50 GB recovery partition. Since the 30 GB unallocated partition I initially planned on using for Ubuntu was now just unallocated space, I extended the 50 GB Windows partition into the 30 GB unallocated space so the Windows partition is back to 80 GB.

Here's where I'm at now, I have an 80 GB Windows (NTFS) partition, 1 MB unallocated space, 15 GB FAT32 partition, 28.61 GB (supposed to be 30 GB...) Ubuntu (ext4) partition, 25.42 GB unallocated space, and 20.84 MB "unknown". This information is according to GParted, running in Ubuntu and Windows Computer Manager says about the same (except it says the last part is 21 MB... not a big difference from 20.84 MB).

I'm trying to extend the Ubuntu (ext4) partition that is currently allocated 30 GB (or apparently 28.61 GB) into the 25.42 GB unallocated space but for some reason GParted won't let me. I can't remember but I thought I extended the 50 GB Windows partition into the 30 GB unallocated space but maybe I first had to format that unallocated space. Thinking this is what I had to do I tried to format the unallocated 25.42 GB space but GParted is saying that I'm only allowed to have 4 primary partitions.

I have no idea what the 15 GB FAT32, 1 MB unallocated, or 20.84 MB "unknown" parts are and the 1 MB unallocated space is only noted on GParted in Ubuntu, not on Windows Computer Manager, but in the end all I want is to extend the Ubuntu partition into the 25.42 GB unallocated space so that I can have more room for Ubuntu. I've attached a screenshot taken while running GParted in Ubuntu. Any help would be greatly appreciated.

Thanks,
Mark

---

### Post by Helkaluin on 2010-11-30
Are you trying to resize from a LiveCD/USB/whatever environment? Remember you have to unmount the partitions first since you are using EXT4, and you can't do that if you are booting from that very partition.

---

### Post by MarkVLK on 2010-12-01
Oh ok, I wasn't aware of that. I'm a new Ubuntu user so I don't know much about how it works. I was trying to resize it from both the Windows partition using Windows Computer Manager and through GParted using the Ubuntu partition. I wasn't aware that I had to boot it from the USB and then unmount it.

So should this work then, if I boot Ubuntu from the USB that I used to install Ubuntu, unmount it, and then extend the Ubuntu ext4 partition into the unallocated space?

---

### Post by Helkaluin on 2010-12-01
That's exactly what you should do. So, yes.

---

### Post by MarkVLK on 2010-12-01
I attempted to do this and was unsuccessful. I feel like this should be a fairly simple task but being unfamiliar with my way around Ubuntu and its applications I'm not exactly sure what to do.

I booted Ubuntu by booting the Ubuntu 10.10 installer off of my USB drive and choosing the "Try Ubuntu without installing" option. Once I got into Ubuntu I opened the Disk Utility but all partitions were already unmounted, or so I assume as I had the option to mount them all via the Mount Volume button at the bottom. When I tried to run the GParted application it crashed. I tried it several times but with the same result.

Am I not approaching this the correct way? Is there some way for me to extend the Ubuntu partition through Windows or can someone explain how I do it through running Ubuntu off my USB drive? I'm assuming if I unmount the Ubuntu partition while running it off of my hard drive terrible things will happen... Although I don't exactly understand the idea of "mounting" drives in the first place. I'm only familiar with mounting virtual discs through Daemon Tools like CDs or DVDs so please help me understand what I should do to correctly extend my Ubuntu partition.

I can supply details or more screenshots upon request.

Thanks again.

---

### Post by oldfred on 2010-12-01
What is sda4? That shows an error. If in gparted you mouse over that what does it say? I think as long as you have an error it may not work.

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

You do have a 4 primary partition limit. If you can fix sda4 then you can convert it to an extended partition and use that space.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by NCLI on 2010-12-01
> **MarkVLK said:**
> I attempted to do this and was unsuccessful. I feel like this should be a fairly simple task but being unfamiliar with my way around Ubuntu and its applications I'm not exactly sure what to do.

I booted Ubuntu by booting the Ubuntu 10.10 installer off of my USB drive and choosing the "Try Ubuntu without installing" option. Once I got into Ubuntu I opened the Disk Utility but all partitions were already unmounted, or so I assume as I had the option to mount them all via the Mount Volume button at the bottom. When I tried to run the GParted application it crashed. I tried it several times but with the same result.

Am I not approaching this the correct way? Is there some way for me to extend the Ubuntu partition through Windows or can someone explain how I do it through running Ubuntu off my USB drive? I'm assuming if I unmount the Ubuntu partition while running it off of my hard drive terrible things will happen... Although I don't exactly understand the idea of "mounting" drives in the first place. I'm only familiar with mounting virtual discs through Daemon Tools like CDs or DVDs so please help me understand what I should do to correctly extend my Ubuntu partition.

I can supply details or more screenshots upon request.

Thanks again.

Step by step:

1. Launch Ubuntu from the USB drive.
2. Launch gparted.
3. Use gparted to change the partitions.
4. Make gparted apply the changes.
5. Reboot.

Do NOTHING other than this. Don't mount or unmount anything, everything that needs to be unmounted should be unmounted when you start from the USB drive.

---

### Post by MarkVLK on 2010-12-01
> **oldfred said:**
> What is sda4? That shows an error. If in gparted you mouse over that what does it say? I think as long as you have an error it may not work.

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

You do have a 4 primary partition limit. If you can fix sda4 then you can convert it to an extended partition and use that space.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Thanks for the links oldman. I'm not sure what sda4 is or where it came from. I've attached a screenshot of the Properties of sda4. Should I try deleting it since that is an option?

> 
Step by step:

1. Launch Ubuntu from the USB drive.
2. Launch gparted.
3. Use gparted to change the partitions.
4. Make gparted apply the changes.
5. Reboot.

Do NOTHING other than this. Don't mount or unmount anything, everything that needs to be unmounted should be unmounted when you start from the USB drive.


That's what I tried doing as I described above, did I do it correctly by choosing "Try Ubuntu without installing"? If so, this is what I did and GParted would not run for some reason, it continuously crashed. Do I have any other options?

---

### Post by MarkVLK on 2010-12-01
> **MarkVLK said:**
> Thanks for the links oldman. I'm not sure what sda4 is or where it came from. I've attached a screenshot of the Properties of sda4. Should I try deleting it since that is an option?



That's what I tried doing as I described above, did I do it correctly by choosing "Try Ubuntu without installing"? If so, this is what I did and GParted would not run for some reason, it continuously crashed. Do I have any other options?

Sorry... Forgot to attach the screenshots.

---

### Post by oldfred on 2010-12-01
Do you have a new motherboard with an EFI boot system (may also have a BIOS mode). If so you should keep the efi partition, most tools do not correctly see efi or bios_grub partitions for some of the new systems.

Edit
I found this that also says you may want to keep your efi partition.
[http://crunchbanglinux.org/wiki/asus_eee_pc_1001px_crunchbang_installation_guide](http://crunchbanglinux.org/wiki/asus_eee_pc_1001px_crunchbang_installation_guide)

---

### Post by MarkVLK on 2010-12-02
> **oldfred said:**
> Do you have a new motherboard with an EFI boot system (may also have a BIOS mode). If so you should keep the efi partition, most tools do not correctly see efi or bios_grub partitions for some of the new systems.

Edit
I found this that also says you may want to keep your efi partition.
[http://crunchbanglinux.org/wiki/asus_eee_pc_1001px_crunchbang_installation_guide](http://crunchbanglinux.org/wiki/asus_eee_pc_1001px_crunchbang_installation_guide)

Thanks for the link, yes I know that my netbook does have the BIOS Boot Boster feature and it looks like that's what that partition holds.

Any suggestions as to what I should try now? Again, I tried running Ubuntu by choosing the option to try it without installing so that I could attempt to extend my Ubuntu partition without it being mounted but GParted crashed every time I tried to run it through that option.

---

### Post by emoneylovesyou on 2010-12-02
At this point wouldn't it be easier to just use windows to reformat/partition everything to the way you want it then install Ubuntu where you want?

---

### Post by MarkVLK on 2010-12-02
> **emoneylovesyou said:**
> At this point wouldn't it be easier to just use windows to reformat/partition everything to the way you want it then install Ubuntu where you want?

I tried to do that but for some reason I can't extend the Ubuntu partition into the unallocated space in Windows. I don't know why but my only guess was that maybe Windows doesn't have the ability to extend EXT4 file systems?

I don't want to reformat my entire hard drive because then I would lose everything.

---

### Post by dre12b on 2010-12-02
My advice as a fellow newbie:
1) Take a deep breath.  Or several.  I've crashed my entire system and lost data by desperately trying to solve an issue that was only a minor inconvenience.  Don't escalate the situation!

2) File systems.  There's plenty to learn here - I'm not an expert, but here are the take-home messages: 
- NTFS is the Windows default - it's fast for file transfers and works well.  As of the last couple years, Ubuntu/Linux handles NTFS well/dependably.  You can read and manage a NTFS partition from Ubuntu.
- Ext4 is now the Ubuntu default - it's fast and very dependable.  Windows will NOT read or manage/resize an Ext4 (or Ext3) partition.  It can read it with additional software, but that's another story.

3) Resizing existing partitions can be a little buggy, particularly when using NTFS (the default windows file system).  I HIGHLY recommend making a backup of every original partition on your hard disk to a USB drive before messing around with this further.  Then you can experiment with impunity!

From windows, I use Acronis to backup a partition.  There are other tools available for Ubuntu, which may require a little more learning in order to use successfully.

3) If you're having trouble with GParted from an Ubuntu live USB, one option is to use the GParted Live USB.  This is lighter weight and boots quickly if your only objective is to alter partitions.  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

4) Partitions for dual-booting.  The arrangement that works well for me is:
- Primary NTFS (~35GB w/page file) Windows
- Extended Partition: Ext4 (~16GB w/swap) Ubuntu
- Primary NTFS (remaining available space), with entire user directory(ies) from windows install.

Then I create symbolic links from my Ubuntu home directory to the user folders on the second NTFS partition for downloads, documents, music, etc.  This provides enough space for Windows and Ubuntu to operate and install tons of programs, while reserving as much space as possible for your user files in the third partition.

As a last note, Ubuntu usually installs itself to an extended partition.  This avoids the problem of maxing out the number of primary partitions on a hard drive.  

Good luck and if you have the patience, take notes of what you're doing.  If you're like me, the minute you get things working you'll forget how you did it and will be obligated to relearn the whole process through trial and error next time round.

---

### Post by dre12b on 2010-12-02
Forgot to mention:

On my wife's EEE, from what I remember I did the following:
- Backed up all partitions
- Wiped the drive clean except for the EFI boot partition.
- Copied the Windows partition back onto the machine.  Resized it.
- Installed Ubuntu.  Sometimes the partition editor in the installation manager gives me trouble, so I probably just selected "install to largest free space" and later resized the partition using Gparted from a USB.  
- Created third NTFS partition, then moved her Windows user directory to this partition and created symlinks from Ubuntu.

This may not be the best arrangement, but it has worked well for her and I still have a backup of the original partitions on a USB drive in case we ever want to restore to factory state.

---

### Post by MarkVLK on 2010-12-02
Can you explain exactly what a symbolic link is and the purpose of a swap for Ubuntu? From what I've read a swap is basically allowing an Ubuntu partition to use space from a different partition in case it runs out of memory. Is this essentially what a swap is or am I completely off? I didn't set up a swap when I installed Ubuntu onto its own partition because I figured 30 GB (and hopefully soon 50 GB) was plenty of space.
 
I have no idea what a symbolic link is although I seem to remember creating one when I was trying to install a JDK but I was simply following a guide and was really unsure of what exactly I was doing...
 
I tried installing GParted Live onto a USB drive similar to how I installed the Unubtu installer onto a USB drive but for whatever reason it wouldn't boot. I'm not sure but I think maybe the USB drive I used to install GParted Live onto isn't bootable so I'll probably try using the USB drive I used to install Ubuntu off of to hopefully get that working.
 
Thanks everybody for your help, I hope to figure this out soon!

---

### Post by oldfred on 2010-12-02
When your computer runs out of RAM, it copies data into swap. With lots of RAM, some say you do not have to have swap, but most think you should have some. I suggest 2GB as a default size. Swap needs to the the same size as RAM if you want to hibernate, but on my system I can boot just about as fast as recover from hibernate. Old systems with only 256MB of RAM needed swap twice the size of RAM.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Linking is a way to make a folder look like it is in your /home when it is really somewhere else. It is like a shortcut in windows.

 I use linking for my /data partition with many folders that I link into /home. If only one or two folders you can just directly mount them into /home. I used to do that for my /shared (NTFS) partition but I now changed that to a link, but did not have to.
You still have to have a mount point, an entry in fstab mounting the folder into your system.

This is basically how I link a data folder into home it:
sudo mkdir /mnt/data
sudo chown -R fred:fred /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music

---

### Post by MarkVLK on 2010-12-02
Is there any reason in particular for creating symbolic links? I don't plan on accessing any data on my Windows partition from Ubuntu or vice versa so I don't see much use in it. Also, would you suggest that I add swap space? At the moment I only have 1 GB RAM but I plan on eventually getting a 2 GB stick to replace the 1 GB. Could anything bad happen if I don't add swap space?

I attempted to make my flash drive bootable using the instructions listed at [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) but that didn't seem to work. I tried both methods (using the script and using Netbootin) but neither worked, the USB will not boot.

I never would have guessed merely extending a partition into unused space would be so difficult.

---

### Post by Helkaluin on 2010-12-03
> **MarkVLK said:**
> 
I never would have guessed merely extending a partition into unused space would be so difficult.
Wow, talk about derailing threads.

Let's go back to what OP was relevant last time, i.e. GParted crached when running from a LiveCD environment.

The first thing is to try to run it again from the LiveCD but this time try to run it from a terminal instead of from the menus: ```
gksu gparted
```

When the program crashes, post any terminal output.

---

### Post by MarkVLK on 2010-12-04
Thanks for all your help guys but I finally ended up solving the issue. Parted Magic ([http://partedmagic.com/]("http://partedmagic.com/")) ended up being my savior. I used UNetbootin to install Parted Magic to USB and ran the Live version of Parted Magic from the USB on my netbook. From here I used the Clonezilla application that was in the Live version of Parted Magic to backup my entire hard drive to my external 1 TB hard drive as an image (in a 300 GB EXT4 partition of the 1 TB that is) just to be safe.

After that was complete I used the Partition Editor application also included in the Live version of Parted Magic to then extend my Ubuntu partition into the unused section of my hard drive and it seems to have worked as I am posting this message to you all now via Ubuntu.

Thanks again for all your help and the information, I appreciate it.

Mark

---

