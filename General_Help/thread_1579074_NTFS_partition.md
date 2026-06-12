---
title: "NTFS partition"
date: 2010-09-21
forum: General Help
---

### Post by SuperFreak on 2010-09-21
I am contemplating installing Ubuntu on a new computer with no other operating system. I have all my data (about 1 TB worth) on a Win XP system right now so it is all in NTFS file format. I understand it would be best if all my files are EXT 4 rather than NTFS unless I have access to a Win OS to repair any corrupt data on the NTFS files. I guess I could back all the data up onto an external drive before I install Ubuntu and then reinstall the data in the EXT format. Would this be the best way of proceeding. Will this prevent me from using Windows in the future if Ubuntu does not work out for me? I really wanted to get away from the idea of a dual boot with Windows as it kind of negates the value of free Ubuntu if I have to shell out money for Win 7 on my new computer.

---

### Post by coffeecat on 2010-09-21
> **SuperFreak said:**
> I understand it would be best if all my files are EXT 4 rather than NTFS unless I have access to a Win OS to repair any corrupt data on the NTFS files.

This is good strategy but I think you're confusing files and filesystems. You need Windows to repair a corrupt NTFS file**system**. There is very little you can do about corrupt files. Ext4, NTFS, FAT32, etc refer to the filesystem. It doesn't matter what filesystem the files are stored on. The only thing that doesn't transfer from a Windows filesystem to a Linux one and vice versa are ownership and permissions because Windows and Linux use entirely different permissions systems. But for personal files that doesn't matter at all.

What you need to do is to copy all your personal files from Windows to an external drive formatted with a filesystem that Linux understands. That will have to be NTFS or FAT(32) because Windows doesn't undertstand Linux filesystems. Then transfer onto your Ubuntu system. If the day comes that you want to go back to Windows, just go through the reverse process. You could even switch over to a Mac and have your files on the Mac hfs+ filesystem. It won't affect the files. The only problem I can see is if you really have 1TB of personal files. You are going to need a lot of intermediate media.

The one thing I would suggest you double-check is that date/time stamps are preserved. They should be but occasionally bugs creep in and the date/time is changed to current on a copy. This is errant behaviour but I've seen it on occasion.

I have personal files from way back that have lived at various times on Windows, Mac and Linux filesystems. They are all still just fine.

---

### Post by wyliecoyoteuk on 2010-09-21
Yes, I run a mixed network and transfer files between Windows, Linux, BSD and Macs all of the time.
Moving the files between filesystems will not change their contents.
There is even a driver available to read EXT filesystems in Windows.
The Macs are the only issue for a couple of reasons:
They create files in 2 parts(although you can ignore the resource fork) and they allow slashes in filenames! grrr!

---

### Post by Mark Phelps on 2010-09-21
> **wyliecoyoteuk said:**
> ... There is even a driver available to read EXT filesystems in Windows...

Unless they've updated it very recently, this driver does NOT read Ext4 filesystems -- the default filesystem used for Ubuntu 10.04.

---

### Post by Mark Phelps on 2010-09-21
> **SuperFreak said:**
> ...I understand it would be best if all my files are EXT 4 rather than NTFS unless I have access to a Win OS to repair any corrupt data on the NTFS files...

Not necessarily ...

There's no problem in MS Windows and Ubuntu both sharing files stored in an NTFS filesystem.  That's the generally accepted practice for creating shared data partitions.

As to Linux system files and Linux personal (/home) files, yes, those should be stored on an Ext4 filesystem.

---

### Post by SuperFreak on 2010-09-21
Thank you all for your answers. 
I regularly back up all my files to external hard drives ( I have 1 TB and  a few smaller external drives) now so I will just reformat my internal hard drive before installing Ubuntu and set it up in the EXT format( I am reusing the old 2 TB HD drive in my Win XP machine in the new Ubuntu machine).
Is the EXT format a superior file system to NTFS or just a different proprietary file system ? Would EXT 4 be the best choice? I am waiting till the release of Ubuntu 10.10 before doing anything

---

### Post by -kg- on 2010-09-21
> **SuperFreak said:**
> Is the EXT format a superior file system to NTFS or just a different proprietary file system ? Would EXT 4 be the best choice? I am waiting till the release of Ubuntu 10.10 before doing anything

If you are planning on going exclusively Ubuntu (or Linux), then the ext file system would be the best choice.  Just as it has been mentioned that there are drivers available to enable Windows to read the ext file system (they ***still*** haven't updated that driver to read ext4?!), Linux also has to have a driver to read NTFS and FAT.

It's not that one or the other is proprietary; those file systems are *_native_* to their respective OSes.  For one to read the other, a driver is required...for example, in order for Linux to read the NTFS file system, the "ntfs-3g" driver is required.  Naturally, each OS will be able to better deal with partitions formatted to it's native format.

As to which is superior to which, the debate goes on... :-k :P

---

### Post by srs5694 on 2010-09-21
First, a naming/terminology nit to pick: "Ext" or "extfs," short for "Extended File System," is the name of an early Linux filesystem that was retired long ago. Extfs was quickly succeeded by its second-generation variant, the "Second Extended File System," aka ext2 or ext2fs, which held sway for some time and is still a viable filesystem. Then came ext3fs and now ext4fs. I know the terminology is awkward, but nobody today uses extfs, except perhaps on ancient computers; it's ext2fs, ext3fs, and/or ext4fs. These filesystem names are also usually lowercase, or i-capped at the starts of sentences, since they're not acronyms (unlike JFS for Journaled File System or FAT for File Allocation Table, for example).

As -kg- says, in terms of NTFS vs. ext2/3/4, it's not a question of which is superior, but which one is native to which OS. To elaborate a bit, OSes rely on particular filesystem features to do important things. For instance, Linux assumes that every file will have associated with it a user ID (UID) number, a group ID (GID) number, and a series of permission codes that tell the OS whether the file's owner, group, and everybody else can read the file, write the file, and execute the file. All Linux-native filesystems (ext2/3/4, ReiserFS, XFS, JFS, and Btrfs) support these features, and Linux relies on these features for basic operational functions, such as controlling who can execute programs. There are also special file types (such as device files and symbolic links) that are used in standard Linux installations. Windows, however, doesn't encode its ownership and permission information in the same way, and it doesn't support the same types of special files; Windows uses different data structures, and these aren't translated by the Linux drivers. Thus, NTFS cannot be used as a Linux root (/) filesystem, or even as the filesystem that holds user home directories (normally root or /home). It goes the other way, too; Linux-native filesystems such as ext2/3/4 don't support the features that Windows requires to function, so these filesystems couldn't be used as a Windows boot partition even if the drivers existed to support this type of operation.

What you *can* do is set up a shared data partition to exchange user files, most of which don't need the OS-specific filesystem features. A quick-and-dirty way to do this is to give Linux access to the Windows boot partition; however, because Linux doesn't understand the Windows security features, this can be risky -- it becomes too easy for an ordinary user to accidentally trash the Windows installation. (To be sure, lots of people go for months or years like this without problems; but the same can be said about driving without wearing a seat belt.) It's better to set up a separate partition for data exchange and access it in both OSes.

One more point: Although ext4fs is the default in recent versions of Ubuntu, you shouldn't feel compelled to use it. IMHO, ext4fs offers few advantages over its predecessor ext3fs for most desktop user. It'll be a bit faster at some things, but that's about it.  There are some who think it's less reliable than ext3fs even today, although that's a claim that's hard to quantify. Personally, I prefer ReiserFS, since it feels a bit snappier in actual use, although most benchmarks suggest otherwise. For big partitions, such as my MythTV video storage space, I use XFS, which has a longer track record than ext4fs. (XFS, JFS, ext4fs, and Btrfs are all capable of storing bigger files, are quicker at handling big files, and can hande larger filesystems than can ext2fs, ext3fs, and ReiserFS. Btrfs is still experimental, so I wouldn't recommend it unless you want to live on the bleeding edge.)

---

### Post by coffeecat on 2010-09-21
> **SuperFreak said:**
> Is the EXT format a superior file system to NTFS or just a different proprietary file system ? Would EXT 4 be the best choice?

Just to clarify one point. Whether or not the ext family of filesystems is superior to NTFS (I'm not going to get dragged into that argument :)), you cannot use NTFS for a Linux operating system **except** for  keeping data on a separate data partition. NTFS is a Microsoft filesystem and doesn't support the Unix permissions which are essential for a functioning Linux system. And, as I think has been covered, NTFS for a separate data partition is an unwise choice if you don't have a Windows system with physical access to it in case you need to repair filesystem corruption. Linux NTFS tools are simply not up to this job.

As far as the choice between ext3 and ext4 is concerned, I've used ext4 since it became the default for Ubuntu systems and not yet had a problem. Certainly, I'm much happier with the swifter filesystem check that is performed once every so often when you boot up. An ext3 check can be irritatingly slow.

**Edit:** I was typing my post when srs5694 posted, and my post is probably superfluous. Listen to srs5694. He knows what he is talking about. I have learnt a lot from his posts and links.

---

### Post by bodhi.zazen on 2010-09-21
I suggest you keep your data on the NTFS partition and dual boot Linux and Windows for a while. This way if you have a problem with the ntfs drive, and you can not solve it from Ubuntu, you can still boot windows.

If you decide you no longer wish to run Windows, back up the data and convert to ext4 or btrfs.

For now I do not understand why you need to upgrade windows at all, I would not upgrade windows.

---

### Post by SuperFreak on 2010-09-21
I will be purchasing or building a new computer and I will not be able to install my Win XP OS from the old computer because of copyright. I was hoping to get completely off of Windows as I believe Linux is more secure and also because of the added cost and headaches of purchasing, installing and running a second OS. However I do see some advantages to a dual boot system. I have run the Live CD of Ubuntu 10.04 and tried installing a few programs as well as printer drivers and it seemed fine. I am not looking forward to trying to migrate my Outlook Express folders and contacts to Evolution but from what I have read it may be possible; but that is another topic. I am most grateful for all the advice I have received and I am saving text files of this thread so I can use the advice when I am ready.

---

