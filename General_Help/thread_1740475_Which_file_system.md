---
title: "Which file system?"
date: 2011-04-27
forum: General Help
---

### Post by otacon507 on 2011-04-27
I have one computer with windows and one with ubuntu.  I have an external drive (FAT32) with files taken from an NTFS (mp3s and such) and I would like to put them and use them on an ext4 ubuntu platform.  Can I make a partition of the /home folder NTFS and the system ext4 and function properly? I do have configuration files in the /home folder since Im building a domain controller that utilizes samba on ubuntu: would I be better off using a dual boot with windows/ubuntu and placing the files on the Windows partition?  what is my best option?>
Please help!

---

### Post by Lars Noodén on 2011-04-27
Have you considered running the Windows-only applications under WINE?  That way you could run everything in Linux and take advantage of EXT4.

---

### Post by otacon507 on 2011-04-27
not too shabby of an idea, but i have pdfs, videos and mp3s and it seems a bit redundant to store that many NTFS files in an ext4 plus all the apps i would need for wine.  is there any other way?

---

### Post by Grenage on 2011-04-27
> **otacon507 said:**
> I have one computer with windows and one with ubuntu.  I have an external drive (FAT32) with files taken from an NTFS (mp3s and such) and I would like to put them and use them on an ext4 ubuntu platform.  Can I make a partition of the /home folder NTFS and the system ext4 and function properly? I do have configuration files in the /home folder since Im building a domain controller that utilizes samba on ubuntu: would I be better off using a dual boot with windows/ubuntu and placing the files on the Windows partition?  what is my best option?>
Please help!

I'd personally keep any native Linux partitions EXT4 or EXT3, and dual boot where need be.

---

### Post by otacon507 on 2011-04-27
are there consequences to making linux NTFS? can i mount a dual booted windows volume to my domain controller for sharing? is there no way to convert my files to ext4?

---

### Post by Lars Noodén on 2011-04-27
> **otacon507 said:**
> not too shabby of an idea, but i have pdfs, videos and mp3s and it seems a bit redundant to store that many NTFS files in an ext4 plus all the apps i would need for wine.  is there any other way?

There would be less redundancy than dual boot because all programs and data would be available under a single linux system.  

Using WINE, you would not need NTFS, only EXT4.  For PDFs, videos an mp3's you have a lot of programs available in Ubuntu and so WINE would not be needed for much.  Overall it's a lot more efficient than worrying about dual boot.

---

### Post by otacon507 on 2011-04-27
> **Lars Noodén said:**
> There would be less redundancy than dual boot because all programs and data would be available under a single linux system.  

Using WINE, you would not need NTFS, only EXT4.  For PDFs, videos an mp3's you have a lot of programs available in Ubuntu and so WINE would not be needed for much.  Overall it's a lot more efficient than worrying about dual boot.
no doubt. my friend however i cannot run these files (an mp3 from windows on an mp3 player in ubuntu) due to their compatibility implication.  at least i tried with one file and it didnt work

---

### Post by Lars Noodén on 2011-04-27
MP3s should open and play on any system you have a player for, be it Ubuntu, OS X or even Windows.  kaffeine, rhythmbox and vlc are some of the common players.

---

### Post by otacon507 on 2011-04-27
what if i download a file via a torrent client in WINE..will it be ext4?  Thanks so much for your help Lars!

---

### Post by yetiman64 on 2011-04-27
> **Grenage said:**
> I'd personally keep any native Linux partitions EXT4 or EXT3, and dual boot where need be.

+1, NTFS for a linux home partition won't work as NTFS does not support Linux file ownership/permissions. An important file (hidden) in your home folder is ".ICEauthority" and if is not in your ownership and with permissions of 600 will constantly cause error messages on startup of the desktop or in some cases stop the desktop loading. 

You would probably be best with a dual boot setup and non important files to Ubuntu placed on a shared NTFS data partition so both systems have easy access to them (Ubuntu has full read/write capabilities with NTFS partitions).

The WINE idea may work and could be used in conjunction with a dual boot if necessary, but note not all Windows programs will work under it, check them all out at the winehq.org database, or give them a good test out under WINE yourself before relying on them. [see http://appdb.winehq.org/]("http://appdb.winehq.org/")

> what if i download a file via a torrent client in WINE..will it be ext4?Wine's folder exists in your home folder and is on an ext4 partition, so yes they are stored on the ext4 partition. Note: files are the same under either of the filesystems mentioned (doesn't matter where you store them) so long as their permissions/ownership aren't an issue with the programs that access them if stored on a NTFS partition.

---

### Post by Ad@m on 2011-04-27
otacon507, you can transfer files from one file system to another.

Files stored on an NTFS partition can be copied to an EXT3/EXT4 partition.

Storing a pdf file an an NTFS file system does not make that pdf file only accessible on NTFS file systems.  The pdf file will always be the same regardless of the file system of the hard disk drive.

A pdf file will always be a pdf file!

It is therefore perfectly fine to transfer files from an external USB drive that is formatted with an NTFS file system to your Ubuntu PC that has an EXT4 file system.

All the files will be accessible.

The file system has no impact on the file type.

---

### Post by otacon507 on 2011-04-27
> **yetiman64 said:**
> 

You would probably be best with a dual boot setup and non important files to Ubuntu placed on a shared NTFS data partition so both systems have easy access to them (Ubuntu has full read/write capabilities with NTFS partitions).



Wine's folder exists in your home folder and is on an ext4 partition, so yes they are stored on the ext4 partition. Note: files are the same under either of the filesystems mentioned (doesn't matter where you store them) so long as their permissions/ownership aren't an issue with the programs that access them if stored on a NTFS partition.

That makes since, the files are the same no matter what kind of partition they are on.  If I went for a dual boot, would I put the non essential files in the same NTFS partition as Windows?  How exactly does a "shared partition" work>?  If I dont need Windows applications to run my media I will just use Ubuntu. Thank you

---

### Post by yetiman64 on 2011-04-27
> **otacon507 said:**
> That makes since, the files are the same no matter what kind of partition they are on.  If I went for a dual boot, would I put the non essential files in the same NTFS partition as Windows?  How exactly does a "shared partition" work>?  If I dont need Windows applications to run my media I will just use Ubuntu. Thank you

I would be very careful using the Windows drive to store the data, although Ubuntu can read and write to it, the technology is not perfect.

I would definitely recommend you create a separate NTFS partition to the Windows install partition to store data. It will automatically be detected under Windows and a drive letter assignment allocated to it (D:\ if your cd drive hasn't taken D:\ or E:\ if it has - you can manually reassign drive letters in Windows if you wish).

The new partition can be manually mounted in Ubuntu from the Places > Removable Media panel menu or automatically on boot up with an entry put in /etc/fstab (ntfs-config can do this rather easily if you install and use it - note just installing it is not enough, you must run it at least once from System > Administration > NTFS Configuration)

You can re-partition your drive easily with gparted from a live cd, but a word of caution, fully back up all your important data off the drive **before** you attempt it. Accidents can and do occasionally happen causing the loss of data.

---

### Post by Lars Noodén on 2011-04-27
> **otacon507 said:**
> what if i download a file via a torrent client in WINE..will it be ext4?  Thanks so much for your help Lars!

If you download inside WINE, it will use what ever file system you are using for Ubuntu.  The filesystem doesn't affect the format of the files it stores.  

So an MP3 will be an MP3 regardless of whether it lands in a  EXT4 or NTFS (or HFS or NFS or AFS and so on) partition.  Same for MPEG and any other format.  

For what it's worth, there is a really good torrent tool for linux called [Transmission](http://packages.ubuntu.com/eo/maverick/transmission).  So WINE is not needed to do torrents.

---

### Post by otacon507 on 2011-04-27
Thanks alot for all the help guys, and by the way the USB drive I am using is FAT32, dont think that will make a difference.  I appreciate all your guys help, my RAID crashed yesterday and I JUST started using Linux and switching over.  Love it so far.  I dont think i will go with a dual boot as all the tools i need are in linux already!

---

### Post by yetiman64 on 2011-04-27
FAT32 access from Ubuntu is fine, no problems. +1 for using Transmission for bittorrents natively in Linux, I use it here, it works great. Only dual boot if ABSOLUTELY necessary or if you particularly like or need Windows. Cheers and good luck however you choose to go. :)

---

### Post by Jagoly on 2011-04-27
Vuze is good for torrents to. Not as quick as transmission, but loaded with other features.

---

### Post by bobwyajnr on 2011-05-01
> **Jagoly said:**
> Vuze is good for torrents to. Not as quick as transmission, but loaded with other features.

+1 for Vuze. Complete overkill really - but a really nice cross-platform (Java-based) bittorrent client. XBMC, UMplayer, VLC, etc. are all very capable media players that should be checked out - before you think you still need a Windows install... Video encoding is harder - but video/audio playback is well supported. 3D gaming is usually the area that forces most users to dual-boot since WINE is still quite flaky for most games (the newest, DRM-laden ones being the worst offenders).

Ah makes me chuckle a bit to hear that Ubuntu might not play Windows mp3 files... I have been able to watch mounted (decrypted) BluRay disc images in (an Ubuntu installed) version of Mplayer (OK still waiting for BluRay menu support) - so things are definitely moving along a lot!! Also finally got my optical output pass-through working this week - so full surround-sound, 6 channel DTS/AC3 audio on Ubuntu is also possible. Just illustrating that you don't have to wear a sack-clothes to be a UNIX user!!

The NTFS-3g driver - a userspace (FUSE) driver used to mount NTFS partitions is very mature now. I (personally) would happy to use a 2 partition setup (Windows - NTFS, Ubuntu - EXT4) and share files on a folder in the NTFS partition. OK back in the day it was flaky as hell and NTFS partitions were read-only under Linux - but times have moved on. The only problem I have with it these days is the speed bottleneck (about 30-40 Mb/s transfer rate).

Bob

---

