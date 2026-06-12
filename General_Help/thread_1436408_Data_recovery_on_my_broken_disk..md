---
title: "Data recovery on my broken disk."
date: 2010-03-22
forum: General Help
---

### Post by Cyoor on 2010-03-22
A while ago my harddrive kinda failed. I didnt notice untill I got "Grub error 17" one time when I was trying to boot my computer. The problem is not really that I couldnt log on to my computer, but rather that I have alot of important information on the computer I would hate to lose.
At the time I used Ubuntu 8.04 and had reiserfs filesystem on the computer.
I bought a new computer and decided to wait untill I could rescue the data before doing to much dmg to it. But I dont really remember if I tried something to fix it before I realised that it was the harddrive and bad sectors that made me get gruberror 17. Hopefully I didnt do anything.

Anyway. Now today I had some extra time, so I decided to dive in. I booted from a linux mint disk and used ddrescue to transfer all the rawdata over the network to an image file laying on an ext4 drive. Once there I used reiserfsck to try and repair the filesystem. After that i mounted the image file and tried to access the files. Thats where the probelms started. I could see the whole treestructure of the harddrive and everything seemed ok, but when i tried to open the files, none of the pictures, documents and so on could be opend, and when I tried to open stuff like MP3 files they played quite strange. Videofiles was really messy, kept changing resolution and was almost always just gray and green squares on the screen.
I decided to use ddrescue and move the files from the image file and on to a clean disk. So when I was done I could mount the filesystem on the new disk, but with the same resault, so I did reiserfsck again, and when that didnt help I did a buildtree also. Still with the same resault.
So I decided to investigate the data abit. Opening files at random trying to understand what had hapend. And I saw that some MP3 files (the easiest to open) was some kind of mixing between several difrent mp3 files. Some files wasnt even in the same folder, so it was probably just that the file pointer was pointing at the wrong data on the disk. I dont know how that works really, so I dont know how to go on.

So now to the question. How do I get the data back? Have I done something wrong, can I redo somethig?
I still have the broken disk and can take data from it once again, but I want to wait to do that untill I really know what to do.
I also still have the image file, and the disk with the copied data.

I have a ubuntu 9.10 system at my disposal atm.

Thanks in advance!
[B][COLOR=Red]
I have started from scratch again, go to post 6.[/COLOR][/B]

---

### Post by bumanie on 2010-03-22
Grub error 17 is not usually associated with bad sectors and in most cases can be fixed by reinstalling grub via a live cd. However, what you have added re the state of the files on image you obtained via dd_rescue sounds somewhat ominous.
What you have done so far sounds good, as in, you have imaged the original drive and have another drive to copy retrieved data to. That is all good :).
Again, with how you have described the state of the files and (presumably) the filesystem, from here on, things don't look so good. You could try [this]("http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/") on the ext 4 image and see if it works, the drive sounds as though it could be fragmented, but more likely files have become corrupted by some other process.
If that doesn't make things look an better, it would be best to use dd_rescue again and re-image the original hard drive, to get the image back to an untainted/unchanged 'clone'. From there, the  only thing I can think of is to use a data carving program such as photorec (part of testdisk), magicrescue, foremost or scalpel and see what sort of data they can retrieve. They are all available in the repo's and you can find tutorials on the internet re how to use them. Magicrescue claims  "it looks for file contents, so it can be used both as an undelete utility and for recovering a corrupted drive or partition. As long as the file data is there, it will find it".
You should be able to get at least some files back. 
Hope this is a bit helpful. It at least will be an educational experience in data retrieval. Good Luck!

---

### Post by srs5694 on 2010-03-22
Disk directories are just files that are treated differently from other files, so it seems a bit odd that your directory structure is fine but most or all of your files are corrupt. This, along with the fact that you used ReiserFS on the original disk, has me thinking that the issue might be related to ReiserFS mount options or some other ReiserFS-specific issue related to file packing. (ReiserFS goes further than most Linux filesystems in packing small bits of files into the unused space at the ends of other files as a way to fit more data onto a filesystem. My thought is that this process may have gone wrong.)

My first specific suggestion is that you look at the /etc/fstab file on the original disk (or your copy of it) to see what mount options you used. Duplicate those mount options *exactly* on your image to retrieve your files. It's conceivable that an option such as "notail" is causing problems, either by its use or its omission on your recovery attempt.

If that doesn't work, you might try copying the raw image again but this time *don't* run reiserfsck on it. It's conceivable that your initial attempt at repair using this utility actually caused the damage.

Another possibility might be to play with the hash= mount option. (Type "man mount" and read the section on ReiserFS for details.) This one's definitely a shot in the dark, though.

I'd try subsequent mounts of the copied filesystem in read-only mode, to minimize the chance of needing to do another raw copy.

You could also try any of these tests on the original disk (using a read-only mount for safety). It's conceivable that ddrescue was being too sensitive about finding bad data and ended up introducing corruption where a direct access of the original would succeed.

---

### Post by efflandt on 2010-03-22
You might have better luck trying to copy files instead of trying to image a partially broken file system.  That way you may be able to recover some files even if others are broken.

I was trying to rescue a laptop hard drive that WinXP refused to boot even in safe mode, and gparted from Ubuntu CD refused to do anything with that partition until Windows fixed it.  I was able to mount the partition in Linux, but trying to copy the user's Windows home directory failed before it go to My Documents.

When I first put the drive in a USB enclosure, it would not mount in Windows or Linux.  But after sitting for a couple of weeks, I was able to mount it in Linux and copy most of the user's Windows home dir, except for something related to a game.

---

### Post by Cyoor on 2010-03-22
Thanks for the replays. I will test some stuff and answer more to what you have written later. (Need to go to bed now) But I will clarify some things first.

1.) The disk cant in any way be mounted in linux or windows. So I cant access the disk or its filesystem to check for any logs or copy any files. The only way I could get data was trough ddrescue.
2.) The image file is still rawdata from the reiserfs disk, so it should be reiserfs filesystem on the image even tho the image itself is laying withing a folder on my ext4 disk. (Or am I thinking wrong here?)
3.) The disk sounds awful when I try to boot from it, so its definitely broken physically. (Thats why I have decided not to touch it unless I really need to.)

One more question tho.
Is there any way to have the target be an empty drive on another computer? So i dont have to put an image somewhere in between?
For example:
ddrescue /dev/hda2 //192.168.1.9:/dev/hdb

If so.. how exactly should I write and is it something extra I need to do that? (Remember I will need to install stuff and so on while on a bootCD)

The important partition on the disk is 46GB and I have another empty drive (on another computer) that is 320GB. I cant put the 320GB disk in the old computer, since its S-ATA and I only got IDE connectors on the old computer.

---

### Post by Cyoor on 2010-03-27
So.. I have started from scratch again. Here is what I have done so far:

1.) I copied all the data from the broken disk to an immage file using ddrescue with the parameters: -r3 -v. I got a total of 8 errors and and an errorsize of 4096B total.

2.) I copied the data from the immage to an empty drive suing ddrescue and all went well. (Then I rebooted the system just to make sure)

So now I have a disk with Reiserfs and an immage.

3.) I tried to open the disk, and I got this error:
> Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so4.) I then tried to mount the immage and got the same error.

5.) I tried to rebuild the superblock on the disk using:
```
sudo reiserfsck --rebuild-sb /dev/sdb1
```but got the errormessage:
> Failed to open the device '/dev/sdb1': No such file or directoryI really dont wanna mess up this time, so here I would like some sugestions on how to move on. Anyone that have something?

---

