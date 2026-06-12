---
title: "Windows Sharing And Auto Mount?OK, it's me again!  I got a question on sharing files"
date: 2011-04-23
forum: General Help
---

### Post by ken0069 on 2011-04-23
OK, it's me again!  This time I got a question on sharing files across a windows network and auto mounting additional internal hard drives.  

I have 3 desktop computers and my Wife has a new Dell laptop.  All 3 of my desktop computers are multi-boot systems of various versions of Windows installed on separate hard drives along with Ubuntu 10.10 being installed on it's own drive also.  One of those computers has 6 hard drives in it and my problem is 1) how to auto mount them at boot and 2) how to share them on my network with other computers and 3) how to stop Ubuntu from looking for one of those drives if I remove it from the system.  

I'm on a home network with a router with a firewall so I'm not concerned about "security" so I don't want any password junk or limited use of these shares.  I want to be able to access EVERYTHING on those computers from any other computer on my network.  I guess that would be something like chmod 777 that is on some of my website forum files.

For sharing I've tried to make it work through -->places-->then choosing the Windows drives/partitions after which I right click on the share name at the top of the page and choose Properties where "share" is the last tab to the right.  I try to make it share and a nautilus popup comes up and says it's going to make the necessary shares but in the end all I can see from my Wife's computer is the drive letter and that's it??  I've also tried using the "Permissions" tab to allow access to those Windows drives but nothing works.  Believe me, I've been messing with this stuff now for about 3 days and STILL can't get to the drive on this computer from any other computer on my system, and not only that, but I can't get from here to any other Ubuntu computer's Windows shares either?

So this is yet another stumbling block in my path to total Ubuntu computing and online searches haven't given me anything that works to date.  

Anyone got any help for me on these problems?

Thanks,

Ken

---

### Post by ken0069 on 2011-04-24
OK so this was posted late last night and it's probably three pages back now so I'm going to bump it back up to see if anyone has a fix for me with these problems.

Thanks,

Ken

---

### Post by Morbius1 on 2011-04-24
First, the requirement of (1) conflicts with the requirement of (3) so I'm not sure how far we are going to get. 

Second, we need some information. Please post the output of the following commands:
```
sudo blkid -c /dev/null
cat /etc/fstab
```

---

### Post by ken0069 on 2011-04-24
This is the computer my Wife usually backs up data too on a D: partition on the Windows drive.  I had this one configured at one time with v9.04 where it auto mounted and shared those two partitions but when I upgraded to 10.04 something got changed as auto mount and sharing went away and each time the computer was booted I had to hit the S key twice to get it to boot.  Then I went looking trying to fix that and broke the whole thing and had to do a complete reload after I spent a day or two recovering data off this drive.  That is why I would like the system NOT to stop if one or both of those partitions aren't there any more.  Somewhere in the past I've seen something mentioned somewhere in code that stated "fail gracefully" which I interpreted as it looked for smething then continued on when it didn't find it?  There should be a way to make Ubuntu continue to boot if those partitions aren't there? Yes/No?

Anyway, I really need to get THIS computer shared on the network so my Wife can backup her data each night.  The others aren't as important as I can boot in Windows and do file swaps if needed but it would be nice NOT to have to do that either.  About the only time this computer gets booted into Windows is when I need to use PGP encryption to send an Email message to a friend who will only communicate that way.

Thanks,

Ken

```
ken@xxxxxxxxxx:~$ sudo blkid -c /dev/null
[sudo] password for ken: 
/dev/sda1: UUID="1ba6ecf2-04cc-43c0-8205-168e8fd4cd90" TYPE="ext4" 
/dev/sda5: UUID="5f4298d0-4bc7-41a8-8441-73fceb9e9d3b" TYPE="swap" 
/dev/sdb1: UUID="462050FE2050F701" TYPE="ntfs" 
/dev/sdb5: UUID="766483366482F85F" TYPE="ntfs" 


ken@xxxxxxxxx:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5f4298d0-4bc7-41a8-8441-73fceb9e9d3b none            swap    sw              0       0

```

---

### Post by Morbius1 on 2011-04-25
The normal way to automount partitions is to add them to fstab. If for whatever reason you remove the drive where that partition resides you will get an error during boot. So don't remove the drive, remove the line from fstab if you do remove the drive, or don't automount the partitions on that drive.

If you do decide to automont the ntfs partitions then the procedure should go something like this:
[1] Create mount points for the ntfs partitions:
```
sudo mkdir /media/WinC
sudo mkdir /media/WinD

```[2] Add the following lines to fstab:
```
UUID=462050FE2050F701 /media/WinC ntfs defaults,nls=utf8,umask=000,uid=1000 0 0
UUID=766483366482F85F /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000 0 0
```[COLOR=Blue][I]This will result in partitions with full read / write access by everyone.

[/I][/COLOR][3] Run the following command to test for errors and mount the new partitions:
```
sudo mount -a
```*On a personal note I wouldn't mount my "C Drive" at all or if I did I would mount it read only. It's best to isolate the Windows OS partition from Linux - but that's my opinion. If you want to mount it read only the fstab line would look like this:*
```
UUID=462050FE2050F701 /media/WinC ntfs defaults,nls=utf8,umask=222,uid=1000 0 0
```

---

### Post by ken0069 on 2011-04-25
(SOLVED)

Thank you for your help Morbius1!!  Only thing I had to do other than this was to go into properties on each partition and add the share there and it works.  Now I have what I need to do the rest of the drives on the other computer.  Wish me luck as I'm NOT a command line guy!  ;)

Thanks again!!

Ken

---

