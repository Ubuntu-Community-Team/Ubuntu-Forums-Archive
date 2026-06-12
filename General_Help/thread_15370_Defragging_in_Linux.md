---
title: "Defragging in Linux"
date: 2005-02-14
forum: General Help
---

### Post by clarke.rainey on 2005-02-14
I have an [iAudio M3](http://eng.iaudio.com/)  (20GB Mp3 player) and it using FAT32... I was wondering how one would defragment it in linux?.. I downloaded the defrag program from the universal repositories, but even after searching for it through google and the search function on the forums I cannot figure out how to use the program... if anyone has any experience, any suggestions would be very much appreciated...

---

### Post by Jad on 2005-02-14
I don't think that linux filesystem need defragment

---

### Post by rwabel on 2005-02-14
[QUOTE=Jad]I don't think that linux filesystem need defragment[/QUOTE]
well he talks about an FAT32 drive. And indeed that's a good question.
I've also some fat32 partitions, especially one where my emails from thunderbird are saved. It would be very handy to defrag it from time to time.

It's obvious that linux filesystems don't need to be defragmented. But what's with the non linux filesystems which you can use under linux?

The defrag program in universe is only for ext2, minix and xiafs

---

### Post by nocturn on 2005-02-14
[QUOTE=Jad]I don't think that linux filesystem need defragment[/QUOTE]

ext2 can require that (after a very long time).  But his MP3 player uses FAT32, which does need it.

I have never heard of tools to do this on Linux.
The closest thing I know is tar everyting off the device, format it and unpack again.

This does not do a full defrag, but cleans up a little.

---

### Post by rwabel on 2005-02-14
the only program I've found is in beta and does only ext2 and ext3.
 It's in beta state, but I don't think they will support fat32. 
 [http://www.oo-software.com/en/products/oodlinux/index.html](http://www.oo-software.com/en/products/oodlinux/index.html)
 
 another solution could be to use vmware. I don't know if you can defrag from there the partitions.

---

### Post by piedamaro on 2005-02-14
If you need windows filesistem it means that you have *windows* so, use it to defrag.

---

### Post by mendicant on 2005-02-14
defrag from universe is not for fat32.  One thing you can try:

1. Copy all files somewhere safe (and have a separate backup, as well)
2. Format the drive
3. Copy all files back, leaving files that might change as the last files to copy

This assumes that the allocation of blocks is done in order.

However, defragmentation should only be needed if the files have changed in size, which would not normally seem to be the case (except for maybe playlists), or you do a lot of deleting and adding files.  These cases seem a little odd for an MP3 player.

Of course, this could damage all your data, and you'd never get it back again, so make sure you have complete backups.

---

### Post by nocturn on 2005-02-14
[QUOTE=piedamaro]If you need windows filesistem it means that you have *windows* so, use it to defrag.[/QUOTE]

No, it does not.
Things like MP3 players, digital camera's etc all use FAT32, but work perfectly fine with Linux (without any Windows).

---

### Post by rwabel on 2005-02-14
What filesystem does the IPod have?
 I guess it's also fat32 and I assume that under Mac OS X there is no defrag tool around. How does they handle that problem? Or does the player itself have a such a function?

---

### Post by friendly_guy on 2005-02-14
An alternative might be to find a third party windows utility & run it under wine; for those of you that do not know, wine allows many (not all, as it is in development) windows apps to run under Linux.  

I tried googling 'freeware defrag' & got a list as long as your arm.  Surely wine should be able to run one of them?  I would run it on something that is not mission critical like a usb pen just to make sure before turning it loose on critical data.

---

### Post by DJ_Max on 2005-02-14
> An alternative might be to find a third party windows utility & run it under wine; for those of you that do not know, wine allows many (not all, as it is in development) windows apps to run under Linux. 

I highly doubt that, Windows uses a different filesystem the Linux, you would completely screw up your OS.
There's a reason why any Unix based OS doesn't come with a defrag tool, including OS X. nocturn has the right idea about it, you really don't need a "defrag", rather a little clean up.

---

### Post by az on 2005-02-14
sudo parted /dev/sda
print
resize 1
whatever number you think is the smallest all the data can fit.
y

then resize 1
back to the full size.


Good luck and I am not responsible for this borking your key.

---

### Post by piedamaro on 2005-02-14
Uh, you are right guys. But I can't see the need to defrag my camera memory stick for ex. (yes it's fat32), even if a lot of data is going back and forth everytime.
Maybe with a 40GB iPod there could be some benefits from defragging, actually.

---

### Post by clarke.rainey on 2005-02-15
Well my mp3 player is a 20GB HD based one... and since it can be used as a portable HD alot I tend to write, read, and delete alot off of it... so I was figuring that if I had all the music at the begining that it would not have to spin up and down so much to load the data into the buffer since it would be near the front of the drive... and that might save a little battery life... but I guess I can always go to private computer lab that the CS majors have and use a good third party windows defragger to do it... it is no big deal... it just would have been more conveinient from my room... oh and thanks for all the suggestions guys!..

Oh and this is the player I have... [iAudio M3](http://www.jetaudio.com/products/iaudio/m3/index.html) 
it is by far the best player I have ever seen... although I do wish that you did not need a little adapter thing to plug it into usb and power... they are both small enough that one would think that they would just put them on the bottom of the actual device...  oh and do you guys know where one could get a very very short normal USB to USB micro cable?.. for just carying around with the player... thanks!..

---

### Post by friendly_guy on 2005-02-18
DJ_Max wrote 'I highly doubt that, Windows uses a different filesystem.'

With all respect I am aware of that & was not suggesting doing it a reaiserfs or an ext3 partition etc - the discussion was about defragging a FAT32 file system which *is* a windows filesystem not a unix/linux one.

---

### Post by Joh_ on 2005-04-09
[QUOTE=rwabel]What filesystem does the IPod have?
 I guess it's also fat32 and I assume that under Mac OS X there is no defrag tool around. How does they handle that problem? Or does the player itself have a such a function?[/QUOTE]
Actually, the iPod uses different file systems under Windows and MacOS X. It uses FAT32 under Windows and HFS+ under MacOS. I'm not sure, but maybe HFS+ doesn't need to be defragmented either so that's why you don't defragment your iPod under MacOS?

Also, as most other in this thread, I don't think there is a fat32 defragmenter for linux. Maybe someone should write one? :p

---

### Post by sb73542 on 2005-04-10
[http://www.die.net/doc/linux/man/man8/fsck.vfat.8.html](http://www.die.net/doc/linux/man/man8/fsck.vfat.8.html)

I think this would fix a FAT32 volume in the rare event of any observable problems...



fsck.vfat(8) - Linux man page
NAME 
dosfsck - check and repair MS-DOS file systems
SYNOPSIS 
dosfsck [-aAflrtvVwy] [-d  path -d  ...] [-u  path -u  ...] device
DESCRIPTION 
dosfsck verifies the consistency of MS-DOS file systems and optionally tries to repair them. The following file system problems can be corrected (in this order): .......

---

