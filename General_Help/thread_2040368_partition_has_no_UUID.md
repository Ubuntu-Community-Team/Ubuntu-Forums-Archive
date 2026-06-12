---
title: "partition has no UUID"
date: 2012-08-10
forum: General Help
---

### Post by wesleykins on 2012-08-10
I can't get my Linux partition to show up by UUID;  it doesn't seem to have one.

blkid shows the UUID of my NTFS Windows XP partition and the Linux Swap partition (/dev/sda6), but nothing for my Linux partition (/dev/sda5).

It doesn't show up in /dev/disks/by-uuid either.

I tried to fix this by running gparted, which *does* list a UUID, the same UUID tht it *used* to have before I screwed it up (ran Windows FIXMBR trying to boot back into Windows, which didn't work either), and I added that UUID as a symlink in /dev/disks/by-uuid*

I then ran update-grub2 and it worked!!! grub.conf found and used the UUID of my partition... until I rebooted.

Now it's missing again from /dev/disks/by-uuid and doesn't output from blkid either.

The only way I can boot my machine now is by editing the Grub2 boot menu and replacing the UUID entry with /dev/sdx5, x depending on which drives I have plugged in at the moment.

Does anyone know why this isn't showing up, and how to fix it?  Does it need to be written to the MBR or something?

I have a working machine, so it's really just an annoyance, but I'd like to better understand how this works.

Thanks a bunch,

-Wes


* I just tried to auto-complete this path by hitting <TAB>.  It didn't work. Does that mean I'm not a n00b anymore?  like driving a car with an automatic transmission and kicking the floor looking for the non-existent clutch...

---

### Post by dcstar on 2012-08-10
> **wesleykins said:**
> I can't get my Linux partition to show up by UUID;  it doesn't seem to have one.

blkid shows the UUID of my NTFS Windows XP partition and the Linux Swap partition (/dev/sda6), but nothing for my Linux partition (/dev/sda5).

It doesn't show up in /dev/disks/by-uuid either.
.........

```
sudo tune2fs /dev/sda6 -U *"Your current UUID"*
sudo update-grub
```

---

### Post by wesleykins on 2012-08-12
David,

Thanks for your help.

tune2fs ran without any complaints, but didn't add anything to the /dev/disk/by-uuid folder, or to fstab, and nothing shows up in the output of blkid.

```
# tune2fs /dev/sda5 -U 'd6d454dd-fc37-4933-8c57-03220c459bd4'
tune2fs 1.42.4 (12-Jun-2012)

# blkid
/dev/sda2: UUID="A840C2E340C2B77A" TYPE="ntfs" 
/dev/sda6: UUID="6ddeda4a-9de6-420e-94f3-0c3c64a49c2b" TYPE="swap"

# ls /dev/disk/by-uuid
6ddeda4a-9de6-420e-94f3-0c3c64a49c2b  A840C2E340C2B77A

# cat /etc/fstab
<file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sdh5       /               ext4    errors=remount-ro 0       1
```gparted reports the uuid as ```
d6d454dd-fc37-4933-8c57-03220c459bd4
``` under the "information" tab, but that's the only place I've seen it.

I really don't understand how this works.

Maybe a stupid question, but do I have to run tune2fs with the partition *unmounted*, like from a live CD or initramfs, or something?

-Wes

---

### Post by wesleykins on 2012-09-22
Can anyone comment further on this?

It's frustrating when I change drives having do guess what the location of the device is in order to boot...

---

### Post by oldfred on 2012-09-22
fstab does not automatically get updated. In fact I do not know of any script that takes a new UUID and adds that to fstab. Generally we suggest manually editing fstab if required as some of the older gui tools are not current and do not include the correct parameters.

Does grub update correctly? 

# To clear cache and get new view:
sudo blkid -c /dev/null -o list


I think I saw one other user with UUID issues and it seemed more like a bug in blkid.

---

### Post by dcstar on 2012-09-22
> **wesleykins said:**
> Can anyone comment further on this?

It's frustrating when I change drives having do guess what the location of the device is in order to boot...

Your posts indicate that you are using a root shell which is not the Ubuntu recommended way of doing things.

Since this indicates that you are doing non-standard things to your system then unless you can specify **ALL** of these things that you have done to your system then this unusual problem probably has no resolution.

Unfortunately issues like this are usually caused by people doing all sorts of screwy things to the systems that they don't understand the consequences of, or by blindly following various "HOWTO's" and other scripts found on the 'net that can cause weird problems.

---

### Post by wesleykins on 2012-09-23
> **dcstar said:**
> Your posts indicate that you are using a root shell which is not the Ubuntu recommended way of doing things.

Since this indicates that you are doing non-standard things to your system then unless you can specify **ALL** of these things that you have done to your system then this unusual problem probably has no resolution.

Unfortunately issues like this are usually caused by people doing all sorts of screwy things to the systems that they don't understand the consequences of, or by blindly following various "HOWTO's" and other scripts found on the 'net that can cause weird problems.

Well, I certainly have done screwy things, but I sort of *had* to.

I have an NTFS-formatted windows software RAID array that I couldn't access, and Grub2 would not let me boot back into Windows (still won't, I figured out how to mount the array using dmsetup instead...), so I followed a tutorial and used the Windows disk to FIXBOOT and FIXMBR, so I could use NTLDR to boot, which clearly broke things.

Then it wouldn't boot at all, so I reinstalled Grub2 back on the MBR, and everything works, but the UUID is gone, and I can't get it back.

I'm running Debian, but I was a member of this forum first, and folks here seem pretty nice (thanks!) so I decided to ask here first.  Debian doesn't have a sudoers list by default, so I just open a root shell and do it that way.  Everything else seems pretty similar.

---

### Post by dcstar on 2012-09-24
> **wesleykins said:**
> Well, I certainly have done screwy things, but I sort of *had* to.

I have an NTFS-formatted windows software RAID array that I couldn't access, and Grub2 would not let me boot back into Windows (still won't, I figured out how to mount the array using dmsetup instead...), so I followed a tutorial and used the Windows disk to FIXBOOT and FIXMBR, so I could use NTLDR to boot, which clearly broke things.
............

Boot off a Live CD and see if the UUID exists or can be set, if not then the MBR and partition table may have some strange settings that need detailed analysis.

If you have the disk space, use gparted to copy the partition and see if that has a UUID.

---

