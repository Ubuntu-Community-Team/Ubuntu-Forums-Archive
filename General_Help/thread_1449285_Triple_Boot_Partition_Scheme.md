---
title: "Triple Boot Partition Scheme"
date: 2010-04-07
forum: General Help
---

### Post by Iceman692 on 2010-04-07
I have 160 GB to run the OSes and 1 TB for my Mythbuntu recordings, music, etc. I want to run OSX, Windows 7, and Mythbuntu. Mythbuntu would be my primary OS. I came up with the following partition scheme but am unsure. I searched all over the web for help but didn't find anything clear. My biggest problem is that I don't know what file format is compatible with all to use as a Shared Data drive.

If I decided to make my media storage a network drive, would I be able to access it via my Windows 7 laptop since the drive will be XFS?

What file system should I use for my inter-OS shared data drive (f:\)?

Thanks!

C:\   Mythbuntu;        60 GB;           ext3 
      D:\   Windows 7;         50 GB;         NTFS
      E:\   OSX;                  50 GB;          HFS+ (Journaled) 
      F:\   Shared Data;       20 GB;             ?       
G:\   Media Storage;    1 TB;           XFS

---

### Post by gamerchick02 on 2010-04-07
You usually can't go wrong with FAT32.  It's readable by all those OSes.

Is this partition going to be separate from the rest?

Amy

---

### Post by audiomick on 2010-04-07
As far as I know, FAT 32 has limits on the size of files it will deal with. I think the OSs you mention can all deal with NTFS as well. That might be a better idea if you have large files in your media stuff. I think the magic number is 4GB.

Yes, it is. Here:
[http://en.wikipedia.org/wiki/FAT_32](http://en.wikipedia.org/wiki/FAT_32)

---

### Post by giddyup306 on 2010-04-07
> **audiomick said:**
> . I think the magic number is 4GB.



You would be correct.

---

### Post by davec64 on 2010-04-07
It semms possible to mount Ext2/Ext3 in OSX:

[http://forums.macosxhints.com/showthread.php?t=39228]("http://forums.macosxhints.com/showthread.php?t=39228")

And to mount ext2/ext3 in Windows you can use Ext2 IFS:

[http://www.fs-driver.org/faq.html#acc_ext3]("http://www.fs-driver.org/faq.html#acc_ext3")

So its possible to go that way if you wish!

---

### Post by srs5694 on 2010-04-07
> **Iceman692 said:**
> If I decided to make my media storage a network drive, would I be able to access it via my Windows 7 laptop since the drive will be XFS?

That won't be a problem. You'll presumably use Samba on the Linux side to share the files. The Samba clients don't know what filesystem is used on the Samba server, and you can use any filesystem that Linux can handle -- ext2fs, ext3fs, XFS, NTFS, HFS+, ISO-9660, NFS, etc. There are restrictions on some of these, but they have to do with filesystem limitations or limitations on Linux's ability to handle the filesystems. For instance, you can't write to a read-only filesystem like ISO-9660.

---

### Post by Iceman692 on 2010-04-07
> **srs5694 said:**
> That won't be a problem. You'll presumably use Samba on the Linux side to share the files. The Samba clients don't know what filesystem is used on the Samba server, and you can use any filesystem that Linux can handle -- ext2fs, ext3fs, XFS, NTFS, HFS+, ISO-9660, NFS, etc. There are restrictions on some of these, but they have to do with filesystem limitations or limitations on Linux's ability to handle the filesystems. For instance, you can't write to a read-only filesystem like ISO-9660.

Thank you so much! I thought this part was going to give me a heart attack. lol That relieves me. So this will work out well after all!

Thanks for all the answers. I think I'll go with FAT32 for the Shared Data partition. I won't be using anything over 4 GB on that partition anyway.

Now I move on to my next predicament...How should I install these OS's? I read one guide that suggested installing OSX first, then install the Chameleon Bootloader and then the other 2 OS's. My problem is that this will be used on a primarily MythTV device. I assume my IR remote won't work to select the OS to boot, right? In that case is it possible to have Linux boot after a certain time limit or even only show the boot options with a certain key while booting?  I'd rather not have to whip out the keyboard every time I boot my PVR... Thanks!

---

