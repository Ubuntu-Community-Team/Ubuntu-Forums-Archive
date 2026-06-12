---
title: "convert from UUID"
date: 2012-03-16
forum: General Help
---

### Post by MyD0j0 on 2012-03-16
I need to convert my UUID in fstab to the symlink -- /dev/sda1 -- so that i can use ping to create an image and copy to a new disk.

I believe I need to run update-grub and other than changes in fstab, I am not clear what else I need to update so that I don't have any trouble getting booted up on the new disk.  Once I'm booted up on the new disk, I intend on converting back to the UUID.


Thanks for any thoughts anyone has!

---

### Post by oldfred on 2012-03-16
There also are a few places where it saves drive info:

UUID in grub, fstab & in
/etc/initramfs-tools/conf.d/resume

Install drive:
more /var/cache/debconf/config.dat  | grep /dev/disk
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

I just prefer clean installs and copy over whatever you want. Clean install then housecleans all the old stuff and at least is fully configured. I only do clean installs now but this is what I backup (but I keep old install just in case I miss something).

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by MyD0j0 on 2012-03-16
I would love to do a clean install--the disk already has that with all my backed up items restored.

The one problem I have that will prevent a clean install from being used is the ef-ing bcm4311 wireless card that I cannot get working.  Apparently something has changed since my original install and after spending a day with ndiswrapper and fwcutter (STA does not work at all), I got nowhere.  After several clean installs that took a few hours to get working on previous releases, I can tell you that that one issue almost had me not using linux on a couple occasions.

Thanks for the info!

---

### Post by MyD0j0 on 2012-03-16
I thought I recognized your handle:

[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by MyD0j0 on 2012-03-21
oldfred--thanks for your earlier help!  I'm restored using the disk image and am now looking at restoring the system to use UUIDs.  In doing so, I am following along with the [UsingUUID]("https://help.ubuntu.com/community/UsingUUID") documentation here and have a couple questions I'm hoping you can help with.

when i changed my fstab to use /dev/sda1 and /dev/sda5 instead of the uuids, all i did was comment out the uuid entries and created a new entry for each.  Now that I want to update resume and fstab, i look to see what the uuids are:

```

eric@MasterD0j0:~$ sudo blkid
/dev/sda1: UUID="50646b9d-59aa-4a9b-906e-a67c61778cca" TYPE="ext4"

```This is the same uuid i had before...shouldn't it have changed with the new disk?
Where did the entry for /dev/sda5 (swap) go?

The documentation doesn't say anything about converting to UUID for non-dapper systems and using those commands (for the fstab part anyway) errors with 'no such file' and 'no command found'.  grub is identifying the correct install_devices.

When I look at disk utility, sda1 shows up as ext4, sda2 shows as extended and sda5 shows as swap, so I'm not sure if I missed something...

so again, my 2 questions are:

This is the same uuid i had before...shouldn't it have changed with the new disk?
 Where did the entry for /dev/sda5 (swap) go?

---

### Post by oldfred on 2012-03-21
One of the issues with disk images and then restoring to another drive and keeping old drive is that the image is just that including the UUIDs. So no they would be exactly the same. That lets you restore with grub & fstab having correct entries.

Not sure what happened to swap entry. You should just be able to add one. But did you just restore sda1 and not sda5. Swap is just empty partition with no format. So if you do not have a sda5, create one and use the new UUID in you fstab to mount it. System will work without swap if you have a fair amount of RAM, unless you load a lot of programs or edit videos. But generally it is better to have some Swap.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by MyD0j0 on 2012-03-23
The swap partition was there, it just wasn't being used.  The link to the swap faq got me back in the game though!  I really would have preferred a clean install, but for what ever reason I just could not get my bcm4311 wireless working again--and a laptop without wireless is nearly useless except as a word processor...

Thanks for all your help! I really do appreciate it!

---

### Post by oldfred on 2012-03-23
Glad you got it working. :)

---

