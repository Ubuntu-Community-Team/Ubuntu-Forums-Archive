---
title: "Ubuntu 12 &quot;Missing Operating System&quot;"
date: 2012-08-10
forum: General Help
---

### Post by -DarkAceZ- on 2012-08-10
First off, I'd like to say this computer is a laptop with no battery and no harddrive. The harddrive went bad along with the battery, so whenever the cord gets unplugged the computer turns off, and I'm/I was running my OS on a 16GB flash drive.
The computer has went through **many** unexpected shutdowns, and it never broke any data... Until recently.
I was watching a movie, when someone sat on the cord, it got unplugged and it immediately turned off. By now I'm pretty used to this, and I just plugged it back in and started it up, only to find:
```
error: file not found
Grub rescue: 
```
That's probably not good, and I did an "ls /" and **everything seemed fine until I "ls /home".** Nothing was there.
So I pop my flash drive into my 10.04 PC, only to find this in the root:
[IMG]https://dl.dropbox.com/u/22806246/Screencaps/OS12041.png[/IMG]
**2.3GB left would also indicate my data is still there.**

Someone in #ubuntu IRC suggested trying [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") (Second option, Recommended repair), but after using it (returned [http://paste.ubuntu.com/1136645/](http://paste.ubuntu.com/1136645/) ) when I tried booting from the flash drive again, it didn't even get to Grub:
```
Missing Operating system
Operating System not found
```
If I remove the drive and press enter it just prints "Operating System not found".

The drive is no older than 5 months... I doubt it already went bad...
Any ideas? I'm not sure how fsck works, and I figured I'd better see what you people think before trying that.

If I could at least just save my home folder...

---

### Post by oldfred on 2012-08-12
BootInfo is not showing grub nor the kernels in your install. If you look in /boot are kernals there? You show the links in / that should be to the most recent kernel, but the X looks like it may be broken? If /boot got deleted that is a major problem. I think because BootRepair did not find the kernels it just installed syslinux as a default boot loader when Linux files are not found.

---

### Post by -DarkAceZ- on 2012-08-13
/boot was there when I was on grub, but I didn't check it's contents.

When trying to read /boot (on another system), along with the rest of the missing folders, it gives me an "input/output error".

---

### Post by oldfred on 2012-08-13
I would backup anything that you can backup, if not already backed up.

I might try e2fsck, but since it is missing folders not sure if testdisk would do anything more.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by -DarkAceZ- on 2012-08-14
You're saying I should try 
sudo e2fsck -C0 -p -f -v /dev/sda1 
and then
sudo e2fsck -f -y -v /dev/sda1
?

---

### Post by oldfred on 2012-08-14
Yes the e2fsck will look for errors in file structure, but I am not sure it will then see missing files & folders. 

You might also look in lost & found or trash to see if boot folder is in those.

---

### Post by -DarkAceZ- on 2012-08-14
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
/dev/sda1:                                                                      Inode 130081 is in use, but has dtime set.  FIXED.
/dev/sda1: Inode 130081 has a extra size (1565) which is invalid
FIXED.
/dev/sda1: Inode 130082 is in use, but has dtime set.  FIXED.
/dev/sda1: Inode 130082 has a extra size (16412) which is invalid
FIXED.
/dev/sda1: Error while reading over extent tree in inode 130082: Corrupt extent header


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
ubuntu@ubuntu:~$ 


```
fsck /dev/sda1?

---

### Post by oldfred on 2012-08-14
the second version I posted does more if the first has issues. The -y answers yes on all issues which can be many.
See 
man fsck
man e2fsck

sudo e2fsck -f -y -v /dev/sda1

fsck does the same as e2fsck

---

### Post by -DarkAceZ- on 2012-08-14
sudo e2fsck -f -y -v /dev/sda1
worked, went through tons of output, and:
```
*** journal has been re-created - filesystem is now ext3 again *** e2fsck: aborted
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
```
Tried booting, same error ("Missing Operating system." then "Operating System not found")

---

### Post by oldfred on 2012-08-14
It made repairs but if files & folders are missing it is still an issue. Did you look in the lost & found or trash?

You may be able to chroot into your system and reinstall grub2 and install the current kernel if that is all that is missing. Otherwise backup what you can or have not backed up and totally reinstall.

I think this has a helper on the chroot as an option.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by -DarkAceZ- on 2012-08-14
"Did you look in the lost & found or trash?"
Lost and Found has nothing, and it won't read the trash folder.

And before we go any further, when trying to mount the drive it gives an error, thanks to fsck, I think:
"Unable to mount 12 GB Filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error
In some cases useful info is found in syslog-try dmesg|tail or so"

---

### Post by oldfred on 2012-08-14
Usually when that error occurs, you just have to run fsck (or e2fsck) to clear it.

Is this just from mounting in liveCD or trying to reboot?

What does dmesg|tail say?

---

### Post by -DarkAceZ- on 2012-08-14
"Usually when that error occurs, you just have to run fsck (or e2fsck) to clear it."
Okay, but it just seems like it's doing the same thing as last time...


"Is this just from mounting in liveCD or trying to reboot?"
Live CD.

"What does dmesg|tail say?"
```
ubuntu@ubuntu:~$ dmesg|tail
[ 5901.011133] usb 2-4: device descriptor read/all, error -71
[ 5901.124202] usb 2-4: new high-speed USB device number 14 using ehci_hcd
[ 5901.540196] usb 2-4: device not accepting address 14, error -71
[ 5901.596533] hub 2-0:1.0: unable to enumerate USB device on port 4
[ 5901.840222] usb 2-4: new high-speed USB device number 16 using ehci_hcd
[ 5901.993338] uvcvideo: Found UVC 1.00 device HP Webcam (0408:030c)
[ 5901.997127] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input15
[ 5902.315656] usb 2-4: USB disconnect, device number 16
[ 5903.464206] usb 2-4: new high-speed USB device number 17 using ehci_hcd
[ 5903.520518] hub 2-0:1.0: unable to enumerate USB device on port 4
ubuntu@ubuntu:~$ 
```


sudo fsck -y /dev/sda1 completed. Same mount error. fsck gave a different error this time, and didn't take quite as long:
```
Unattached inode 133674
Connect to /lost+found? yes

Inode 133674 ref count is 2, should be 1.  Fix? yes

Symlink ... (inode #133675) is invalid.
Clear? yes

Error deallocating inode 133675: Illegal doubly indirect block found

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sda1: ********** WARNING: Filesystem still has errors **********

e2fsck: aborted

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sda1: ********** WARNING: Filesystem still has errors **********

ubuntu@ubuntu:~$ 

```

---

### Post by oldfred on 2012-08-14
Is the webcam something you can disconnect temporarily. It looks like that is causing issue now.

If filecheck is not fully working, these are links to some advanced attempts to repair.

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by -DarkAceZ- on 2012-08-21
Somehow I got fsck/e2fsck to think my data is fine: (I was fsck-ing the disk here and there)
```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1 
e2fsck 1.42 (29-Nov-2011) 
/dev/sda1: clean, 11/730080 files, 85721/2917632 blocks
```
...But lost&found is the only folder showing up now. (No files)

TestDisk says "Warning: Bad starting sector (CHS and LBA don't match)" and shows:
```
Disk /dev/sdb - 16 GB / 15 GiB - CHS 15484 64 32 
Current partition structure:
      Partition                  Start        End    Size in sectors  
 1 * Linux                    1   0  1 11397  63 32   23341056  

Warning: Bad starting sector (CHS and LBA don't match) 
 2 E extended             11398  63 31 15482  63 32    8364034  

Warning: Bad starting sector (CHS and LBA don't match) 
 5 L Linux Swap           11399   0  1 15482  63 32    8364032  

Warning: Bad starting sector (CHS and LBA don't match)
```
```
Disk /dev/sdb - 16 GB / 15 GiB - CHS 15484 64 32
      Partition               Start        End    Size in sectors 
D Linux                    1   0  1 11397  63 32   23341056  
D Linux                    1   1  1 11398  63 32   23343072  
* Linux Swap           11399   0  1 15482  63 32    8364032
```

I don't quite understand what I should do after I do a "deeper search". "Write" would format my disk, wouldn't it? 

The webcam seems quite hard to remove, though I might be able to boot from another laptop, if it's a really big issue.

---

### Post by oldfred on 2012-08-21
Is this a different issue. Your fsck were on sda1 and the testdisk error is on sdb? Your sdb is only 16GB?

The write in testdisk updates partition or files that you have found and changed.

If just a partition start type issue you might see what this says.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by YannBuntu on 2012-08-22
Hello

- there is a read &write error on sda1. 

```
ls: cannot access /media/f28705d4-78f7-4eb0-bf7d-e1537df38f4d/boot/: No such file or directory
mkdir: cannot create directory `/media/f28705d4-78f7-4eb0-bf7d-e1537df38f4d/var': Input/output error
```

This explains why BIS didn't detect anything (nor grub nor kernels) inside /boot.

Furthermore:

> **oldfred said:**
> I think because BootRepair did not find the kernels it just installed syslinux as a default boot loader when Linux files are not found.

Nearly ;) See line 240 of the report: indeed B-R didn't detect nor grub-install (for simple GRUB reinstall) nor apt (for GRUB download and reinstall), so it defaulted to syslinux.

Missing (or unreadable) apt is a very severe problem, so I would recommend to format and reinstall Ubuntu.

---

### Post by -DarkAceZ- on 2012-08-27
> **oldfred said:**
> Is this a different issue. Your fsck were on sda1 and the testdisk error is on sdb? Your sdb is only 16GB?


I had unplugged the device for a bit, and it changed /dev/ names, I guess.
fsck is still saying it's clean, and testdisk does not find anything wrong with anymore either, while lost&found is still the only folder.

[QUOTE=YannBuntu]Missing (or unreadable) apt is a very severe problem, so I would recommend to format and reinstall Ubuntu.[/QUOTE]

I guess I'll do just that, then. I'm not losing many files, actually, it's just that it will take me a looong time to reconfigure GNOME just how I want. I'm picky and lazy. :p

---

### Post by YannBuntu on 2012-08-28
> **-DarkAceZ- said:**
> it will take me a looong time to reconfigure GNOME just how I want. I'm picky and lazy. :p

This method may be convenient then: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

