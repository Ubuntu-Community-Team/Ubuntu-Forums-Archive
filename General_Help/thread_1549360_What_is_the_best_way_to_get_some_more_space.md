---
title: "What is the best way to get some more space?"
date: 2010-08-09
forum: General Help
---

### Post by RJ12 on 2010-08-09
Ok, so I have started to run out of comfortable space for my needs (I like to do a lot of VM work) and so I have taken some space out of my Windows partition (which I hope to be blowing out within Christmas). I want to also carry some stuff over to Ubuntu so I was thinking of formatting the unallocated space as NTFS / FAT32. I have some things over 3 GBs so I was thinking NTFS (because of restrictions on FAT32), but Ubuntu can't write well to NTFS real well. I will eventually be expanding my Ubuntu partition to take this space, but for now I need some space both Ubuntu and Windows can look, and use. I have posted a screenshot of my GParted layout which is current.

Thanks!

---

### Post by earthpigg on 2010-08-09
if you've never run this command, been using that install for a while, everything is working fine on that install, and you are confident that you will continue to have broadband internet, then this ought to free some space:

sudo apt-get clean

it deletes all the stuff in /var/cache/apt/archives - stuff only needed if you have a slow internet connection ***and*** if an update ever breaks something.


it would be nice if there was a windows driver that supported ext4 filesystem. that would solve all of your problems immediately. unfortunately, only support for ext3 is available at present.

actually, you *could* make that shared partition ext2 or 3. or maybe fat32. ubuntu and windows both have just about perfect fat32 support.

---

### Post by darolu on 2010-08-09
> Ubuntu can't write well to NTFS real well
I can write to NTFS without any problem at all, where does this statement come from?

Anyways, another option is to use Ext4 or similar filesystem and install a *nix filesystem reader software in Windows, I know there are some programs/libraries (whatever they use in win) like [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by nmaster on 2010-08-09
> **darolu said:**
> I can write to NTFS without any problem at all, where does this statement come from?

same for me.  i have my external drive formatted with ntfs and its never been a problem.

---

### Post by linux18 on 2010-08-09
get rid of the recovery partition if you backed up windows, shrink your swap to 2048MB and move it all the way to the right. grow the ubuntu partition to fill all empty space. you need to use a live cd for this it should be fairly straightforward:

-boot live cd
-delete swap
-delete recovery
-apply
-grow /dev/sda3 to fill all empty space
-grow /dev/sda5 to fill all but 2048MB
-make a 2048MB swap partition
-apply


you will gain about 54GB

---

### Post by earthpigg on 2010-08-09
> **darolu said:**
> I can write to NTFS without any problem at all, where does this statement come from?

> same for me. i have my external drive formatted with ntfs and its never been a problem. 

i've had problems with it. specifically, if windows locks up without properly shutting down.... you then have to do a bunch of terminal kung fu to make ubuntu mount the partition.

to replicate this behavior:
-format a thumb drive as ntfs. not fat32 which is the default, but ntfs.
-plug it into a windows computer.
-remove it without doing the 'properly remove' thing. or just turn the computer off without properly shutting down. (we're simulating a windows hard freeze here)
-plug it into an Ubuntu machine.
-attempt to mount it ***without*** opening a terminal or entering your sudoer password at any point. good luck.



another one for ya:
-do a large file copy/write operation in ntfs on ubuntu.
-do the same with ext4 on ubuntu.
-do the same with ntfs on windows.
-compare results.

---

### Post by nmaster on 2010-08-09
> **earthpigg said:**
> i've had problems with it. specifically, if windows locks up without properly shutting down.... you then have to do a bunch of terminal kung fu to make ubuntu mount the partition.

to replicate this behavior:
-format a thumb drive as ntfs. not fat32 which is the default, but ntfs.
-plug it into a windows computer.
-remove it without doing the 'properly remove' thing. or just turn the computer off without properly shutting down. (we're simulating a windows hard freeze here)
-plug it into an Ubuntu machine.
-attempt to mount it ***without*** opening a terminal or entering your sudoer password at any point. good luck.


you can fix this one with ```
sudo ntfsfix /dev/sdaX
``` (just replace sdaX appropriately).  recently (two days ago) i had to do this.  i did notice that it failed in ubuntu.  luckily i have a spare box running debian (lenny).  for some reason it worked perfectly there.  i see your point though and not everyone has the time/desire to keep a debian installation around.

> 
another one for ya:
-do a large file copy/write operation in ntfs on ubuntu.
-do the same with ext4 on ubuntu.
-do the same with ntfs on windows.
-compare results.
i've never tried this, but i'll take your word for it.  i usually get 25-30MB/s when transfering files from my local IDE ext4 drive to an external ntfs drive through usb2, so i've never really cared much.

---

### Post by RJ12 on 2010-08-09
I guess it seems NTFS is good. I have never really had a crash with my Windows Partition. I will just be very careful I guess, if there is a better way to do things, I am open for ideas. I have heard of a program called NTFS-3G. What is it and what does it do?

---

### Post by scouser73 on 2010-08-09
> **nmaster said:**
> same for me.  i have my external drive formatted with ntfs and its never been a problem.

+1 for this.

---

### Post by -kg- on 2010-08-09
I've never had any large issues reading/writing to NTFS partitions, either, and if Windows screws it's mounts up in a hard freeze, I just boot back into Windows and let it clean up its own mess.  Good to know the Linux side fix for it, though.

> actually, you could make that shared partition ext2 or 3. or maybe fat32. ubuntu and windows both have just about perfect fat32 support.

That's true, except:

> I have some things over 3 GBs so I was thinking NTFS (because of restrictions on FAT32)

Actually, I think that's over 4 GB, but the point remains.  There *are* drivers that will allow Windows to read ext2/3 partitions, though, so that's definitely an option.

@ linux18:

> get rid of the recovery partition if you backed up windows, shrink your swap to 2048MB and move it all the way to the right. grow the ubuntu partition to fill all empty space. you need to use a live cd for this it should be fairly straightforward:

-boot live cd
-delete swap
-delete recovery
-apply
-grow /dev/sda3 to fill all empty space
-grow /dev/sda5 to fill all but 2048MB
-make a 2048MB swap partition
-apply


you will gain about 54GB 

A few mistakes here.

His recovery partition is not sda1, if that's what you're referring to.  It is sda4 (labeled "HDDRECOVERY") and is located at the end of the drive.  I don't think he wants to delete sda1 (labeled "System").

Now if you intended him to delete sda4 in the above scenario, you have skipped a step.  In order for the OP to expand sda5 into the free space (-2048MB...you could also either shrink the existing swap partition or create it at the end before expanding sda5), you will first have to expand sda3 (The Extended partition) into that space.  You cannot expand a Logical partition into free space outside of the Extended partition it resides in.

Another thing:

> -grow /dev/sda3 to fill all empty space
-grow /dev/sda5 to fill all but 2048MB
-make a 2048MB swap partition
-apply


With the exception of deleting partitions, when I perform partitioning operations such as this, I click "Apply" between each and every operation I perform.  I've experienced ***_MAJOR_*** problems performing multiple operations at the same time.  One time I completely hosed a hard drive and was almost unable to recover from it.  I still can't get some Windows software to run with it (Norton Ghost, in particular, though at this point I don't really care anymore).

In any case, I like the OP's idea of a shared Windows partition better.  I'm leery of giving Linux unfettered access to the partition the Windows OS resides on.  A shared partition is much better.

---

### Post by -kg- on 2010-08-09
> **RJ12 said:**
> I guess it seems NTFS is good. I have never really had a crash with my Windows Partition. I will just be very careful I guess, if there is a better way to do things, I am open for ideas. I have heard of a program called NTFS-3G. What is it and what does it do?

NTFS-3G is the Linux driver for reading and writing to NTFS formatted partitions.  It is installed by default and you won't have to worry about it.  From [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions"):

> NTFS (New Technology File System) is a file system developed by Microsoft and used by Windows computers (Windows 2000 and later). Until 2007, linux was not able to write to this type of filesystem, it could only read from it. The stable ntfs-3g driver now allows linux systems to read and write NTFS formatted partitions.

The ntfs-3g packages comes pre-installed in currently supported versions of Ubuntu and most NTFS devices should work out of the box without further configuration. 

---

### Post by RJ12 on 2010-08-09
-kg-, I was wondering about the EXT2/3 driver, but isn't that not really stable? Plus wouldn't Windows have problems with the whole system of UNIX Permissions?

I like your idea of appling operations each time, because yes I have heard that things like that happen, because nothing is perfect.

Let me explain my partition layout that I have right now.

/dev/sda1 should be the small 100mb partition Windows 7 makes to store boot and I think recovery stuff

/dev/sda2 should be my Windows 7 install

/dev/sda3 extended partition

/dev/sda4 - 5 Should be Ubuntu

/dev/sda5 should be the actual recovery of my system (and I will want to keep that)




That should clear up any partition issues

---

### Post by -kg- on 2010-08-12
> **RJ12 said:**
> -kg-, I was wondering about the EXT2/3 driver, but isn't that not really stable? Plus wouldn't Windows have problems with the whole system of UNIX Permissions?

I haven't heard of any major problems with the driver, other than it won't work with ext4 (yet).  That doesn't mean there aren't any.

As far as permissions go, I think that is OS specific rather than file specific.  I could be wrong.  I only use NTFS for shared partitions.

> **RJ12 said:**
> I like your idea of appling operations each time, because yes I have heard that things like that happen, because nothing is perfect.

Well, that isn't completely the reason.  The major reason is that such operations take so much time.  The more time you take for partitioning operations, the more time there is for things like power failures to happen, or for hardware to heat up and fail.

Then there are those that just don't understand that these operations take a lot of time.  When they set several operations up in a row, then come back 12 hours later and it's still running, they'll panic and cancel the operation at a crucial time.

> **RJ12 said:**
> Let me explain my partition layout that I have right now.

/dev/sda1 should be the small 100mb partition Windows 7 makes to store boot and I think recovery stuff

/dev/sda2 should be my Windows 7 install

/dev/sda3 extended partition

/dev/sda4 - 5 Should be Ubuntu

/dev/sda5 should be the actual recovery of my system (and I will want to keep that)

Have you already changed it, or is this your original layout?  If you're describing your original layout, then your screen shot of GParted says something different:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=165978&d=1281383835[/IMG]

From that screen shot, sda1 is labeled as "System" and is approx. 1 1/2 GB.  Sda2 should be your OS partition, at 128.5 GB.

Sda3 is your Extended partition, which allows you to have more than the maximum 4 Primary partitions.  Any partition inside an Extended partition is called a Logical partition, and is labeled as sda5 and above.

Sda5 is your Ubuntu root partition at around 46 GB and sda6 is your swap partition.

You will notice that the Extended partition ends, and just after that is Partition sda4, at around 8 GB.  The fact that this partition is labeled as sda4, formatted as NTFS, with a label of HDDRECOVERY tells me several things.

First, the last partition on your disk is a Primary rather than a Logical partition.

Second, the partition letter/numbering convention is such that, instead of the order of the partitions on the disk, they are assigned chronologically.  Somehow, sda4 was created *_after_* the Extended partition was created.  Otherwise, the Extended partition would be sda4.

Do you know what might have created that partition?  The designation scheme has me quite confused.  Normally, if there are Primary partitions present, the Extended partition (which is normally created in the installation process) is "sda(highest number =<4).

You can read all about this at the link in my signature block.  For now, though, do you have enough room in your Ubuntu partition for what you need?  If so, then all you will need is the extra space for the new NTFS partition.

Because of the 4 Primary partition limit (and you already have 4) the only thing you'll be able to do is to make it a Logical partition.  You will need to boot to the Live CD and run GParted from there.  You will first need to expand your Extended partition (sda3) into the free space space behind sda2.

Then you'll be able to create the new partition (it will be sda7) and format it to your desired format.  If you need some more space in your Ubuntu partition (it doesn't look too bad at this point...more unused space than used) you'll need to expand it a bit before you create the new one in the rest of the space.

Unless you're planning to heavily use your Ubuntu partition in the near future, I'd just opt for the storage partition, whatever format you choose.  Like I said...read at the link in my signature block for further information on basic partitioning operations.

---

