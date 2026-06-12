---
title: "USB sticks - FAT or NTFS?"
date: 2012-03-10
forum: General Help
---

### Post by Loerie on 2012-03-10
Which is the most **reliable** file-system to use for backup and archiving of data on USB sticks (and USB-HDD's)?

Being portable, they should work on Ubuntu and Windows.


[This]("https://help.ubuntu.com/community/LinuxFilesystemsExplained") is an excellent article explaining the different file-systems, indicating that a journaling system such as NTFS is superior to FAT or FAT32. However some say that FAT should be used for USB sticks.

Is there expert consensus about what is the best and most reliable file-system to use for USB devices?

Many thanks!

---

### Post by MisterGaribaldi on 2012-03-10
Hmm... well... here's some opinions of my own:

Sticks of 2GB or less might as well stick with FAT32 because you cannot run into the file size limitations of FAT32 on such small media. (The limitation is 2.1GB, so you have to be dealing with a 4GB or larger flash drive.)

Beyond that, the biggest issue I see with using NTFS is compatibility. Now, true, we've got read/write support for Linux and it's pretty solid, but if you develop any issues with an NTFS partition, you may have to go back into Windows to fix them, which could be a problem.

Also, if you're planning on having this as truly multi-platform, then Mac users will have to install something like OSXFUSE and NTFS-3G to be able to write to the thing, with the same issues that Linux users would probably have for unclean NTFS partitions, etc.

NTFS makes total sense if:

1. You need to traffick in files larger than 2.1GB *and*
2. You need truly cross-platform compatibility; *or*
3. #1 is true, but you're *only* dealing with Windows.

Because, otherwise, EXT2/3/4 and others all support >2.1GB files, and so does Mac OS Extended.

---

### Post by disabled20191128 on 2012-03-10
I use NTFS

---

### Post by evilsoup on 2012-03-10
NTFS is objectively superior to all forms of FAT.

However, Linux support for NTFS is... pretty lacking. You can read and write (which is all most people need), but it does so very s l o w l y. I use FAT most of the time for USBs (for cross-platform compatibility), and when I had to use NTFS (because I needed to transfer a large video file) it took about three times as long to put the thing on the memory stick. So, stick to FAT32 unless you need to transfer large files.

Depending on your use case, it might also be practical to install EXT-drivers on windows computers (obviously not an option if you need inter-operability with computers you don't own, like work PCs). This would also have the advantage of preserving Linux permissions.

---

### Post by MSPdwalt on 2012-03-10
Where does one find these ext drivers for windows?

Have you thought about doing a cheap NAS for backups?

---

### Post by sudodus on 2012-03-10
> **evilsoup said:**
> NTFS is objectively superior to all forms of FAT.

However, Linux support for NTFS is... pretty lacking. You can read and write (which is all most people need), but it does so very s l o w l y. I use FAT most of the time for USBs (for cross-platform compatibility), and when I had to use NTFS (because I needed to transfer a large video file) it took about three times as long to put the thing on the memory stick. So, stick to FAT32 unless you need to transfer large files.

Depending on your use case, it might also be practical to install EXT-drivers on windows computers (obviously not an option if you need inter-operability with computers you don't own, like work PCs). This would also have the advantage of preserving Linux permissions.
+1

@MisterGaribaldi: The file size limit of FAT32 is 4GiB, otherwise I agree with you too.

---

### Post by evilsoup on 2012-03-10
One could try [ext2fsd](http://www.ext2fsd.com), and the [sourceforge page](http://sourceforge.net/projects/ext2fsd/) (note I can't vouch for these personally, I don't own any windows machines, and I use FAT to transfer files to other peoples' windows machines).

If you do end up using this solution, IIRC you should use EXT2 for USB memory sticks (this allows the memory stick to last longer), and EXT4 for hard disc drives (because of the journaling). Though of course anyone with more in-depth knowledge will probably come across and correct me soon.

---

### Post by MisterGaribaldi on 2012-03-10
> **sudodus said:**
> +1

@MisterGaribaldi: The file size limit of FAT32 is 4GiB, otherwise I agree with you too.

Der... You're right. Sorry, I had the 2.1 stuck in my head. That's the limit for FAT16.

@OP: as a practical matter, I use nothing but FAT32 for all my own flash drives. I use NTFS on hard drives I intend to use for cross-platform purposes. Otherwise, I tend to stick with native partition table systems and native partition types.

---

### Post by Loerie on 2012-03-12
Thanks to all for the response.
Let me see if I can sum this up.

We agree that NTFS is superior to all forms of FAT (evilsoup).
The issue is interoperability which could make it less universally compatible to FAT32. Because, should things go wrong, Linux support for NTFS is... pretty lacking (MisterGaribaldi)

For file sizes >4GB NTFS makes sense (MisterGaribaldi).
For file sizes <4GB Dennisgre uses NTFS, evilsoup says stick to FAT

Perhaps I should rephrase my question:

Dennisgre, have you, or has anyone else experienced interoperability problems when using NTFS?
If, yes, could it be fixed without you losing data?

Thanks!

---

