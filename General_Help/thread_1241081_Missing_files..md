---
title: "Missing files."
date: 2009-08-15
forum: General Help
---

### Post by Dale rose on 2009-08-15
Ok a friend at uni had a virus ridden machine, so i went for a full reformatt approach.
I pconnected his harddrive to my pc and accesed it with the latest update of this distro.
So i cut an pasted his documents includding his uni coursework of  2 years to my hardrive so i could store fro the reformat.
Well the problem is i only got the text and pdf files, all the picture and movie files arnt their and their not in the orginalll folder.
The paste timer showed that ubuntu was copy all 9.8gb of his files yet i only have recived 48mb.
I tried doing a full reste check on his harddrive and came up empty.
Any advice?

---

### Post by Herman on 2009-08-15
So have you really reformatted your friend's hard drive yet or not?

If you did, what do you actually call 'reformatting'?

If you only set a new partition table that won't affect your friend's data at all, you can easily restore the old partition table with TestDisk. 
In case it's any help, I have a page in my website about how to use TestDisk, [TestDisk Page]("http://members.iinet.net.au/%7Eherman546/p21.html").

If you have created a new file system in a partition then you will have overwritten at least the old file system blocks most likely, but you can probably recover files from the rest of your partition by a process known as 'data carving'.  
PhotoRec is a program that comes with TestDisk and that's the one I have used for that kind of thing with good results.

[Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") is a special version of Ubuntu which comes with all of the best file recovery programs already installed. They also have their own [Forums]("http://ubuntu-rescue-remix.org/forum"). Probably you will get better advice there too, from people who are experts in that field.

The first thing they will probably advise you do do is make a dd backup copy of the entire drive to a USB drive or some other drive which is larger than the one you need to recover the files from, then work on the backup copy, not the original drive.
It's also a good idea to have a nice large disk to copy the files to that you're trying to recover, a good large USB externel hard drive is ideal.

You should still be able to recover the files, or at least most of them if the virus hasn't already destroyed them.

---

### Post by g_krishna on 2010-08-14
Hi, I am new to ubuntu. I copied my data from pen drive and pasted in the hard disk. My laptop has both windows as well as ubuntu. When I logged in in windows, I could not see the pasted files! and I went back to ubuntu and again I am not able to see my pasted files!! I am just wondering where did my files disappear!!?? Can anybody help me!?

---

### Post by Herman on 2010-08-14
> Hi, I am new to ubuntu. I copied my data from pen drive and pasted in  the hard disk. My laptop has both windows as well as ubuntu. When I  logged in in windows, I could not see the pasted files! and I went back  to ubuntu and again I am not able to see my pasted files!! I am just  wondering where did my files disappear!!?? Can anybody help me!?     You said you copied the files, (as opposed to cutting them), so I presume you still have the original copies of the same files in your pen drive. If not, you should try running photorec in both your pen drive and your hard disk partition to see if you can get some of your files back. Photorec is a program that you can install in Ubuntu and it comes bundled with another program called TestDisk, so when we install TestDisk we get PhotoRec at the same time,
```
sudo apt-get install testdisk
```Both your hard disk and your thumb drive may have cache memory to make them seem faster. Data being written to a disk may be deposited temporarily in the hard disk or USB disk's cache memory and queud there while the hard disk's read and write heads are busy writing earlier data to disk. If you're writing to a flash memory drive, the data may be queued waiting for the drive's controller to erase old memory blocks and write the new data.
This can be imagined as something like a number of cars queuing to get into a parking lot.
Unfortunately the hard disk's cache memory is the type of memory known as 'volatile' memory, meaning that as soon as power to the disk is cut off, like when the computer is shut down, any data still left queud in a disk's volatile memory will be lost. 
Normally when the USB drives are unmounted by right-clicking and selecting 'safely remove drive', or 'unmount', the disk will be given time to complete any pending operations before it is removed and there is no problem. For internal hard disks, of the operating system is shut down the normal way, there is normally no problem. The operating system, or more specifically probably the kernel, takes care of everything.

You didn't mention what file system you have, FAT16, FAT32, NTFS or a Linux file system like EXT2, 3 or 4.

Another possibility is the file system itself. Most partitions have something called a file system in them, which is a reserved area of disk space where the operating system can record exactly where on the disk it puts our files or parts of our files if we have large files that need to be written to more than one empty place in the disk.
Whenever data is written to a disk or deleted from a disk, the operating system the kernel to be more exact, has to update the file system with the details of the transaction, the same as a bank teller records details of deposits and withdrawals from your bank account.
If you went into a bank and just threw you money over the counter and ran out without taking the time to identify yourself and have the transaction recorded, you would lose your money right? Well it's something like that with a file system too, the kernel writes to the file system and records details about files being transfered in or out.

When a partition is 'formatted', that means giving it a new empty file system, (which is something like a new empty bank book).
Now another thing that can happen is, Windows might for some reason not agree with some detail about the way Linux or even Windows itself has written details in the file system and it will helpfully offer to reformat it for you. If you agree to this, the operation takes place quite quickly, and it's possible to click on that without thinking. There's no sudo in Windows. 
That's something like a bank teller saying, 'hey, I can't read your bank book, the print's a bit blurry and I left my specs at home, tell you what, we'll just forget it and start over again with a brand new shiney empty account, how would you like that?

Another thing to think over is what about the condition of the disk itself. Hard disks use patterns of positive and negative magnetic flux to record data as a lot of 1 and 0 s on the disk surface. Magnets don't last forever, they weaken with time and heat, and if the magnetic properties of the hard disk is getting relatively weak in a few spots then it is said that the hard disk has some 'bad blocks'.
All hard disks have some bad blocks, even when they are new and fresh from the factory, and to hide that fact, they are provided with an ample supply of spare bocks, which are reserved and used to silently replace any bad bocks that may appear as the disk ages. 
Now if a bad block were to occur and a file system sector, it wouldn't take to much imagination to realize that could cause a few problems.
Use 'Disk Utility' in Ubuntu, (System, Administration, Disk Utility), to check on the health of your hard disk.

Another thing that can go wrong is, a hard disk or a flash memory stick can have a faulty controller, the little block of firmware that the operating system talks to and tells the read and write heads what to do, or performs wear leveling and erases and writes blocks of flash memory.
I have one flash memory stick right now that has a five year warranty and has a faulty controller. It appears as an empty disk but it was full of data and about every twentieth time or if I'm lucky when I plug it in the data shows up sometimes, but most ot the time it seems empty. I'm sending it back to the manufacturers for a replacement.

I could go on, but already you can see that there are lots of ways data loss can occur.
We have come to assume that computers are perfect because most of the time they are, or seem to be, but in reality, computers and computer hardware and software is designed by humans and can have faulty material and all kinds of other faults and nothing is perfect.

That's why we always keep at least one or more backup copies of all of  our data the we care about in some other media like a CD or DVD.   :)

---

### Post by robbrownu on 2011-03-04
Any ideas on how to restore files lost during a file transfer to a memory stick?  I dragged them from my folder to a memory stick.  When done, i removed the stick and tried to read it on another PC, only to find the stick was "empty."  When I went back to my original files on my first PC, they weren't there (as if by dragging them to the memory stick, I deleted them).
 
I'm been trolling message boards for a while trying to find someone with a similar issue, and this was the closest I found.  Anyone have any ideas.  I"m at wit's end with losing these files.

Rob
 
[EMAIL="robbrownu@yahoo.com"]robbrownu@yahoo.com[/EMAIL]

---

### Post by Herman on 2011-03-04
:) I expect dragging and dropping files should 'copy' the files to the other drive, not 'move' them, (at least it works that way in my Ubuntu), so it seems strange that the files have apparently disappeared from your hard drive.

It's very important to use the 'safely remove hardware' icon if you use Windows, or in Ubuntu you right-click on the desktop icon for the drive and click 'Safely Remove Drive' before unplugging any USB drive.

Your data could have been in your RAM while it was waiting to be transferred to the USB, and since flash memory is a little slow to write to, some of the faster USBs may have a little memory cache (volatile). Unplugging a USB drive suddenly and thus removing the power erases volatile memory.

I have no way of knowing if that's what happened times time or not, but at work I see the majority of my co-workers ripping out USB drives as a matter of routine and most of the time they seem to get away with it. Other times they don't. 

You could try running photorec on your hard drive to see if you can recover the deleted (moved) files from your hard drive. Try taking a look in my [TestDisk Page]("http://ubuntuforums.org/TestDisk%20Page") and see if anything there will help you. I hope you will be able to get them back.  :)

---

