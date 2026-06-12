---
title: "Partitions in a ThinkPad"
date: 2011-11-12
forum: General Help
---

### Post by the big e on 2011-11-12
I have a ThinkPad T500 with dual boot (Ubuntu and Windows Vista.)
Somebody suggested I could have a third partition and use that for things that I might want to look at in both environments (keep my itunes library in it for instance).

But I tried to do this and it turns out that the ThinkPad has a limit of four partitions, and two of them are the pre-installed system tools for diaglnostics and troubleshooting (which they call ThinkVantage) and one partition is Windows and one partition is Ubunti, so I have already used up my quota.

Is there another way? Is it safe to delete the ThinkVantage stuff, or will I need it in the event of a crash? If I can't set up a fourth partition, is it possible and safe to give music software in my Ubuntu partition access to my itunes library?

---

### Post by PPY on 2011-12-06
I don't know how it is possible to limit number of partitions on particular laptop, I would think it more depends on hard drive. But may be you can try to insert this hard drive into another laptop and create partition there. What software do you use for partitioning? I was able to do dual boot partitioning with G-parted on Compaq Presario with no problems, although I didn't have any extra partitions on the disk.

---

### Post by stevennlv on 2011-12-06
If you are working outside of the operating system with the tools on the Vista disk (from boot) then it will not allow you to create more than 4 partitions on a drive. But, other tools will let you over come this. Such as G-parted. I'd highly suggest that you download the Ultimate Boot CD. (FREE!) [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) It has a lot of great tools on it, including G-parted.

As far as deleting all of the built in recovery stuff goes:

That depends on how comfortable you are with building custom systems. Personally I think all that stuff is crap. The first thing that I do when I get any box is wipe the whole drive and build it out for myself from scratch.

But, this means that you will lose everything (programs / whatever) that came on it from the factory if the back up you create with a third party tools gets corrupted and you have to do a rebuild from bare metal. You may be able to get some of it back through downloads. But, a lot of it will be permanently lost.

Once again: Personally I think all that stuff is crap.

As far as third party back up tools / how to recover your system goes: once you kill the factory restore stuff get To Do Back Up. [www.todo-backup.com/]("http://www.todo-backup.com/") (FREE!) It's a great tool.
 

 If you use it properly then you can even save all of the factory stuff currently on your system in the To Do back up (if you want / need it) so that you can can have you cake and eat it too by keeping all that stuff and freeing up drive space. Just make sure that back up doesn't get corrupted though.
 

 I highly recommend not having your back up on the same physical drive as your system. This can cause a lot of heartaches if you get infected or corrupted. You should always either burn your backups to DVD / CD or use a USB back up drive (~ $50-75 US)

---

### Post by rewyllys on 2011-12-06
> **the big e said:**
> I have a ThinkPad T500 with dual boot (Ubuntu and Windows Vista.)
Somebody suggested I could have a third partition and use that for things that I might want to look at in both environments (keep my itunes library in it for instance).

But I tried to do this and it turns out that the ThinkPad has a limit of four partitions, and two of them are the pre-installed system tools for diaglnostics and troubleshooting (which they call ThinkVantage) and one partition is Windows and one partition is Ubunti, so I have already used up my quota.

Is there another way? Is it safe to delete the ThinkVantage stuff, or will I need it in the event of a crash? If I can't set up a fourth partition, is it possible and safe to give music software in my Ubuntu partition access to my itunes library?
My Thinkpad T420, purchased last September, has 3 physical partitions that are formatted NTFS, and include the SYSTEM_DRV, the Windows 7, and the ThinkVantage partitions. A 4th physical partition, about 210GB, is set up as an extended partition.. It contains 4 logical partitions. One of about 160GB is formatted ext4 and serves as my /home directory.  Two other ext4 logical  partitions of about 20GB each provide space for 2 root (/) partitions for different versions of Linux.  The 4th logical partition is about 12GB and serves as the Swap file.

I assume your iTunes files are in an NTFS-formatted partition;  Ubuntu should be able to access them there.

---

### Post by N00b-un-2 on 2011-12-06
This is something I've thought about a lot since my switch to linux.  as much as I try to shy away from anything Windows or Microsoft related, the best type of partition to store shared data on in my experience is NTFS because can be mounted as read/write in all major operating systems (Windows, Linux, BSD, and Mac OSX).  I create small primary partitions for my operating systems in whatever file system they require, and then one large extended NTFS partition to use as a communal storage for files.  Then I configure my "home" or "My Documents" folders to point to that drive. On Mac and Linux just delete the folders from your home and then create symlinks to the folders on the NTFS drive, and add the NTFS drive to your /etc/fstab.  On Windows XP use Winbolic to junction to them or on Vista/7 just change their target in file properties.
That way the same data is accessible from whatever OS you're booted into at the time.

Here is the output of fdisk -l on my netbook

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00048e47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    58855958    29427948   af  HFS / HFS+
/dev/sda2        58857472   121772031    31457280    7  HPFS/NTFS/exFAT
/dev/sda3   *   121774078   488396799   183311361    5  Extended
/dev/sda5       121774080   153231359    15728640   83  Linux
/dev/sda6       153233408   484202495   165484544    7  HPFS/NTFS/exFAT
/dev/sda7       484204544   488396799     2096128   82  Linux swap / Solaris

```

if you plan on multibooting, partitioning your drive is the first step.  You should plan out how you are going to set up your computer before you install any operating system.  It should never be an after thought.  And if you plan on multibooting Windows with Linux and any other OS (Mac OSX in my case) you should make sure you have proper install disks for each OS, ie; NOT RECOVERY DISKS.  Although it's possible to start from a factory install of Windows, because of the modifications that manufacturers do to the OS and partitions can cause all sorts of headaches when trying to install addition operating systems.

---

### Post by gordintoronto on 2011-12-06
Rewyllys got it right. If you had created an Extended partition, and installed Ubuntu into a logical partition within it, you could have made other logical partitions.

If it were my computer, I would copy the content of the diagnostic and troubleshooting partitions, blow them away, then boot Windows and use its tools to reduce the size of the partition. Make an extended partition out of all the free space, then make small logical partitions with the same names as the diagnostic and troubleshooting partitions and copy the content back, and make another logical partition, formatted NTFS, for whatever space is available.

In doing this, your existing Grub will stop working, so you will have to recover it by using a LiveCD. Google is your friend in finding the description of what to do.

---

### Post by N00b-un-2 on 2011-12-06
> If it were my computer, I would copy the content of the diagnostic and troubleshooting partitions, blow them away, then boot Windows and use its tools to reduce the size of the partition

In my experience, you Windows will often not boot if you remove these kinds of partitions, and in many cases will be irreparable.  Computer manufacturers do some pretty heinous things with Windows, which is why I advise any serious linux user to obtain a regular copy of Windows.

---

### Post by gordintoronto on 2011-12-06
That's why you put them back before you boot Windows again. Oops, I had a sequence error: shrink the Windows partition before messing with the other ones.

---

### Post by N00b-un-2 on 2011-12-07
and another problem: you can't modify a currently mounted partition.  It's simply not possible, and Windows doesn't have good tools for editing partitions anyway, although it can be accomplished to some extent from the command line.  The last time I messed with partitions from within Windows, I used Acronis Disk Director which you used to configure the partition changes you wanted to make while booted into Windows, then you put the Acronis boot disk in and rebooted.  At which point it would carry out the formatting from outside of Windows.  But why do that when booting an Ubuntu CD and running GParted is SOOO much easier and doesn't require expensive proprietary software?

---

### Post by gordintoronto on 2011-12-07
Actually, Windows 7 can shrink the active C: drive. That's how I got the space for Ubuntu on my HP G62 laptop. I think the same procedure works in Vista, but I'm not sure. Here's a quote from my description of what I did:

Back to the C: drive, I right-clicked and selected Properties.  One of the "Properties" is Tools, and one of the Tools is defragmentation. I ran that, and it only took a few minutes on a brand-new hard drive.

In Windows Control Panel, search for "disk," and one of the items is "Create and format hard disk partitions." I clicked on it, highlighted the C: drive and selected "Action," "All Tasks," "Shrink Volume." That opened up more than 100 GB of free space...

---

### Post by N00b-un-2 on 2011-12-08
Interesting!  I did not know that.  I've only ever messed with partitions on Windows using either a program like Acronis Disk Director or via cmd.exe using DISKPART.

---

### Post by rewyllys on 2011-12-08
> **gordintoronto said:**
> Actually, Windows 7 can shrink the active C: drive. That's how I got the space for Ubuntu on my HP G62 laptop. I think the same procedure works in Vista, but I'm not sure. . . .

The same procedure does work in Vista.

---

