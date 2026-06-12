---
title: "Unable to mount /home partition"
date: 2009-11-13
forum: General Help
---

### Post by al_mic on 2009-11-13
Hi all,

I have a problem with my karmic koala ubuntu 9.10, and I hope you can help me solve it:

It all started with a periodic disk scan while booting. 
I was in a hurry so I pressed Escape to skip the scan, and i quickly got to my Desktop
After that, I needed to restart the computer, and while booting I got an error message:
"One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for UUID=eccb7cbf-618a-4e03-aafe-634b4ca0a918
Press ESC to enter a recovery shell"



My /etc/fstab looks like this:
# / was on /dev/sda1 during installation
UUID=82c68f35-e68a-4cd1-af3e-cb503b1cf7e5  /  ext4  errors=remount -ro 0  1

# /home was on /dev/sda6 during installation
UUID=eccb7cbf-618a-4e03-aafe-634b4ca0a918  /home  ext4  defaults  0   2

#swap was on /dev/sda5 during installation
UUID=7bba7a29-e1da-461d-8fcd-414610f910db  none   swap  sw  0  0

/dev/scd0  /media/cdrom0  udf,iso9660 user,noauto,exec,utf8 0  0


I must also tell you that I selected to have an encrypted home directory, and i still have the passphrase that was generated just after install.

Any idea on what to do to fix it? 

Thanks.

---

### Post by bacardiandwatermelon on 2009-11-13
Wouldn't have a clue but I'm sure you could just boot into recovery mode and drop out into a root prompt. then run a.......... fsck /dev/sda6     to run a file system check on the home partition.

---

### Post by al_mic on 2009-11-13
Thank you for the reply!


I did as you told.
And after running: 
# sudo fsck /dev/sda6

I got:

/dev/sda6: clean, 7064/7290880 files, 1771617/29149934 blocks


So.. it seems that /home partition is ok.  Any idea what to do next?

---

### Post by hal10000 on 2009-11-13
> I got:

/dev/sda6: clean, 7064/7290880 files, 1771617/29149934 blocks


So.. it seems that /home partition is ok. Any idea what to do next?

If this did'nt work, then you have to enforce fsck to do a system check
Boot into the recovery console and do:
```
fsck.ext4 -f /dev/sda6
```

---

### Post by doas777 on 2009-11-13
well, if the fschk is done, try rebooting and try again

---

### Post by al_mic on 2009-11-13
I tried :
# sudo fsck.ext4 -f /dev/sda6

and the output:

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda6: 7064/7290880 files (8.3% non-contiguous), 1771617/29149934 blocks


I also tried:
# sudo mount -a

and the output:

mount: special device UUID=eccb7cbf-618a-4e03-aafe-634b4ca0a918 does not exist

I tried rebooting it, but it still stops at the same message.

---

### Post by doas777 on 2009-11-13
recheck your UUID. 
```

ls /dev/disk/by-uuid

```

and make sure it still matches the one in your fstab

also what does fdisk -l look like now?

---

### Post by al_mic on 2009-11-13
# ls /dev/disk/by-uid/

7bba7a29-e1da-461d-8fcd-414610f910db   
82c68f35-e68a-4cd1-af3e-cb503b1cf7e5

#fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

Device    Boot      Start   End    Blocks   Id  System
/dev/sda1  *        1    4868   39102178+  83  Linux
/dev/sda2           4869    19457    117186142+  5 Extended
/dev/sda5           4869     4941      586341    82  Linux swap/Solaris
/dev/sda6            4942    19457    116599738+   83 Linux

---

### Post by delcypher on 2009-11-13
Can you output
```
ls -l /dev/disk/by-uuid
```

Instead that will actually tell us what device the UUID actually corresponds to.

Also you say that you have an encrypted home partition, do you know if that uses LUKS? I use LUKS and do have an encrypted home partition but I did that myself. If you're encryption works the same then I may be able to help you. Did you specify a password when you encrypted your home directory.

Can you run
```
cat /etc/crypttab
```

This will show a list of devices that are supposed to be encrypted that need to be mounted at boot.

Just to note I also get the message "One or more of the mounts listed in /etc/fstab cannot yet be mounted:.." at boot, I wait for a few seconds and then I get prompted for my LUKS password.

---

### Post by al_mic on 2009-11-13
Thank you all for trying to help me!

# ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Nov 13 23:42 7bba7a29-e1da-461d-8fcd-414610f910db -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov 13 23:42 82c68f35-e68a-4cd1-af3e-cb503b1cf7e5 -> ../../sda1


# cat /etc/crypttab
# <target name> <source device> <key file> <options>


I do not know if the encryption uses LUCS. 
It uses whatever the Ubuntu 9.10 is using when you select the login option with password and home directory encryption (at install time) 
The other two options were : direct login, with no password check and password login.

I did wait a few seconds, minutes maybe, but it is not moving or displaying something else.

---

### Post by delcypher on 2009-11-13
Well your home partition isn't even being listed in the list of UUIDs.

I don't know what Ubuntu uses for default home partition encryption.

To find out if it is LUKS you can run
```
sudo cryptsetup luksDump /dev/sda6
```
and see what the output is.

You can try finding out your UUID for the home partition another way
```
sudo blkid /dev/sda6
```

You may just want to edit /etc/fstab for you now and just have the line
```
# /home was on /dev/sda6 during installation
/dev/sda6 /home ext4 defaults 0 2
```

instead of the UUID. I can't guarantee this will work though as I don't know how the encryption is working.

Oh quick edit - I've found something about encryption in ubuntu -->[http://bodhizazen.net/Tutorials/Ecryptfs/]("http://bodhizazen.net/Tutorials/Ecryptfs/")
Apparently uses ecryptfs. This means your home partition should just mount normally.

---

### Post by doas777 on 2009-11-13
you do have a few extra partitions in your fdisk output. is one of them your old home?

---

### Post by al_mic on 2009-11-13
# sudo cryptsetup luksDump /dev/sda6

Command failed: /dev/sda6 is not a LUKS partition

# sudo blkid /dev/sda6
#

There is nothing displayed.


I did place that line in /etc/fstab with /dev/sda6 instead of UUID and ...


WOW !!!


at first it showed that error message (now with sda6 instead of UUID):
"One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for /dev/sda6
Press ESC to enter a recovery shell"


but after a few seconds it disappeared and showed me the login prompt.

I am now on my Desktop!

Thank you so much!
Thank you all!  :KS

---

### Post by al_mic on 2009-11-13
> **doas777 said:**
> you do have a few extra partitions in your fdisk output. is one of them your old home?


/dev/sda1 is /  (a primary partition)
/dev/sda2 is a logical partition and it contains the swap and /home
/dev/sda5 is swap partition 
/dev/sda6 is /home

Thank you for helping me!

---

### Post by delcypher on 2009-11-13
Hmm not sure the problem is entirely fixed. I'm not sure why your home partition has no UUID.

---

### Post by al_mic on 2009-11-14
After restarting the computer once more, that error message was no longer displayed.

So I switched in /etc/fstab the lines for /home partition, by commenting the line with /dev/sda6 and uncommenting the line with 
UUID=eccb7cbf-618a-4e03-aafe-634b4ca0a918

After restarting the computer, an error message was again displayed, the same one, with 
"One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for UUID=eccb7cbf-618a-4e03-aafe-634b4ca0a918"

but this message was there only for a few seconds and the my login prompt was showed.

And then, just to check, I restarted the computer once more, and this time no error message was displayed.

ls -l /dev/disk/by-uuid now shows :

total 0
lrwxrwxrwx 1 root root 10 2009-11-14 13:15 7bba7a29-e1da-461d-8fcd-414610f910db -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-11-14 13:15 82c68f35-e68a-4cd1-af3e-cb503b1cf7e5 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-11-14 13:15 eccb7cbf-618a-4e03-aafe-634b4ca0a918 -> ../../sda6

So it is good.:)

---

### Post by OnuJack on 2009-12-27
I encountered the same kind of problem :)

Out of the blue the system was not able to mount the partition with my home folder. At first I noticed that it took some time mount a partition (did not note which one exactly it was).

I did everything in this thread and it worked out exatly the same way as it did with the author of this thread.

The only difference being - I did not use any encryption for the home partition.

I also used the disk utility to see what it reports. The funny thing is that before I mounted the home partition with /dev/sda it reported the partition as unknown or unrecognized. After mounting using /dev/sda it showed correct information again. As the author of this thread did - I too finally changed the fstab entry back to uuid and now it works again as normal.

Have no clue what caused this behaviour. Might the disk be failing? SMART status is fine, but experience shows that it can not predict very well in some cases.

Thanks for the help guys :)

---

### Post by stevetxt on 2010-01-05
I had this same problem and fixed it by the method in this thread.  But the uuid for my home partition did not show up in the lists again until the next morning.  I have not been able to find the cause as it seems to strike people out of the blue.  I think it might have something to do with upstart or udev losing the uuid on a particular startup, and udev only restarts periodically, not on every boot.  The problem for me showed up when i was setting up to make a presentation and restarted with the projector connected.  It was kind of annoying as I had to switch to the "other side" in my dual boot for the occasion.  It would be great if someone could explain where this problem comes from, as it seems to have affected quite a few.

---

### Post by ludovicc on 2010-01-05
Count me in, I had also this problem and managed to recover from it thanks to this thread. The timing is suspect, several people affected at the same time, was there a security update which caused this issue?

I'm running a dual boot Ubuntu Karmic 64bits with ext4 on my / and /home partitions, and Vista

---

### Post by sjosul on 2010-01-26
I had the same issue - solved thanks to this thread. It's never happened before, and as far as I can tell there were only three differences to my usual usage:

1. Fresh Karmic install, updating the Kernel straight from 2.6.31-14 to 17. Previous installation the updates were incremental
2. I had just set up two additional users on the system
3. I had used fast user switching

These may all be coincidence.

---

### Post by plapczynski on 2010-01-28
I had the same problem Al did.  My .home partition wouldn't mount.  Mine was a new install on 9.10 that had been running since it came out.  I did run all updates as they came out.

Here is what I did:

esc to enter recovery shell

vi /etc/fstab
commented out the entry for sda5 (my home partition)
entered the following the next line down.
/dev/sda5 /home ext4 defaults 0 2

I was using ext4 as my filesystem.

Saved the file.
Quit vi
rebooted

I got some disk checking at boot, but got to the gui login prompt.
Once logged in I edited the etc/fstab file again.

I uncommented the old sda5 entry
I commented the new sda5 entry I had just put in.

Rebooted.

No disk checks, no errors, just the gui login prompt.

ls -l /dev/disk/by-uuid
shows three partitions (sda1, sda5, sda3) all with uuid's

I was getting ready to just reinstall (had just backed up home to a USB drive a week ago so I wasn't worried about data loss) but I am thankful I tried this first.

Final notes - backup often and run vi every few days, I hadn't for months since I was using the gui editors.

Paul

---

### Post by tithily on 2010-03-31
We faced the same problem as al_mic (except for the encryption part), and solved the problem by referring to the block special device (/dev/sda4) directly in /etc/fstab in place of it's symbolic link as per delcypher's suggestion.

Thanks, delcypher and other members for your help!

Tithily.com

---

