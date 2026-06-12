---
title: "Can't boot into Windows after loading BootMed CD"
date: 2012-01-16
forum: General Help
---

### Post by Kreen on 2012-01-16
Ok, so I am utterly lost and confused at this one, so I hope you guys can give me some insight.

I originally had an issue with two WD 1TB Black hard drives in a Raid 0 formation. The stripe broke and I created a BootMed CD to try and repair it with TestDisk. Ultimately, I could not get Windows to boot up again, but I did recover my data.

So, I ditched the Raid and did a normal Windows 7 64-bit install on one of the hard drives. The other hard drive, however, was being stubborn and wouldn't format in Windows, so I booted back to the BootMed CD to format it as NTFS. After doing so, I can no longer boot into the main Windows version. I double checked and I did not accidentally format the wrong hard drive. I did not open TestDisk, the only thing I did was look it up under gparted, which shouldn't have done anything.

The error message is "The boot selection failed because a required device is inaccessible". I get this message if I try to boot in normally with both hard drives plus a 500GB WD Black drive, and if I try to boot with only the single 1TB drive. There have been no changes to the BIOS, but I am overclocking my i7 920.

When I take a look at the good drive in TestDisk, it can read and recognise the System Reserved partition at the start, but not the NTFS partition. In gparted, it shows up as "Unallocated". TestDisk also reports that the MFT and the MFT mirror are bad and cannot be fixed. But I have no idea how that would even happen...?

Windows 7 CD can't fix it since it can't find any Windows installations.

In my old Raid 0, I could fix the stripe in TestDisk and recover my files, and the only problem I could find was it's MFT and mirror were also broken. I'm running BootMed 64-bit, and my only conclusion is that loading/mounting/attempting to mount the drives in BootMed's ubuntu 10.10 is somehow corrupting them? But it seems far-fetched.

Do you guys have any advice? I'm really starting to get worried cause now I can't even recover the data from the new Windows installation...

---

### Post by Kreen on 2012-01-16
Morning bump

---

### Post by oldfred on 2012-01-16
RAID puts meta data on a drive that needs to be removed for Linux, usually Windows ignores it.
What is BootMed? Do you have standard Ubuntu liveCD?

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Windows sometimes installs to one drive and puts  it boot loader on the other drive.

Post test version of boot info script from this. Italso may repair system if only minor repairs are needed.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Kreen on 2012-01-16
Thanks for the reply! BootMed is an Ubuntu 10.10 CD that includes a couple of data recovery and virus scanning tools, specifically it has TestDisk, which I needed to use for my original problem. But I went ahead and downloaded the Ubuntu 11.10 64-bit live CD to work in that.

For the raid metadata deletion, my first drive (with Windows installed) seemed fine, and the second drive didn't have anything on it. This makes sense because I formatted the second one in Ubuntu previously, but I just let Windows 7 install over the half-stripped sda drive. I can see /sdb and /sdc, but not /sda in disk utility.

```
ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda
Do you really want to erase "isw" ondisk metadata on /dev/sda ? [y/n] :y
ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sdb
no raid disks and with names: "/dev/sdb"
```For my BIOS, I have disabled RAID, and my drives are in native IDE. Everything is at its default settings except the Intelligence Tweaker, which is overclocking my i7 to 4ghz.

Here is the Boot Repair summary: [http://paste.ubuntu.com/806346/](http://paste.ubuntu.com/806346/)

It seems to be missing /sda2, which should be the NTFS primary partition. /sda1 is the System Reserved stuff... but again, I didn't manually partition it. Which in hindsight I'm doing from now on...

I'm going to try rebooting after using Boot Repair to try and fix things.

Quick Edit: No luck, still getting the required device is inaccessible error message. At this point, I'd be willing to just redo the Windows installation and manually and correctly partition things, but I still have the problem of recovering my data. Are there any other recommended data recovery tools? TestDisk can see the /sda1 System Reserved partition fine, but it can't see the other NTFS one.

---

### Post by oldfred on 2012-01-16
It only shows sda1, the typical 100MB boot/recovery partition for Windows and no sda2. Also your sdb is not partitioned. Testdisk is in the repository and you can download it into Ubuntu's standard liveCD or use the repair version you have.

[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Kreen on 2012-01-16
I did some more searching, and it looks like you were right in your first reply. Taking a look at sdb, I found there was an NTFS partition in TestDisk that had all my files. Windows split the System Reserved on sda, and the main portion on sdb. Also explains why things broke when I formatted sdb.

Solution? Well, I tried fixing sdb to boot off of it, but it just didn't work out. Now I can't recover any files except for the Users and Program Files (x86) folders... so I'm going to go ahead and recover all my documents while I still have a chance.

For future people... for the love of all that's holy, manually partition and only install Windows while you have one drive in.

---

