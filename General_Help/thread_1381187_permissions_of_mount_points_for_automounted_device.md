---
title: "permissions of mount points for automounted devices"
date: 2010-01-14
forum: General Help
---

### Post by bugagashka on 2010-01-14
Ubuntu 9.10
I have a problem - when I mount other partitions of my hdd or the system automounts usb disks these are mounted in /media directory with permissions 0700. 
So there are two problems there:
 - when I switch user on my desktop to another that user can't read data from the usb disks
 - I can't share data through network because smbd doesnot have read permissions on the created mount points 

I think editing /etc/fstab is wrong way, there would be more right way to change permissions on mount point.
I tried to change/add parameters umask, allow_other in gconf-editor (/system/storage/default_options, subsections vfat and ntfs-3g) but that does not show any results.

Article [https://wiki.ubuntu.com/GnomeMount](https://wiki.ubuntu.com/GnomeMount) recommends  Open Places &#8594; Computer. Every volume except the generic File system one should have a Drive and Volume tab in its properties dialog where you can set mount options. But I didnot find those tabs.

Where should I set option to mount usb disks with permissions rwx for every user of my system?

---

### Post by Richard1979 on 2010-01-14
As far as I know, the only place for physical disks is in /etc/fstab.

Not so sure about USB devices though this might help:
[http://ubuntuforums.org/showthread.php?t=70616](http://ubuntuforums.org/showthread.php?t=70616)

---

### Post by SuperSonic4 on 2010-01-14
Wouldn't a recursive chown on the directory work?

```
sudo chown :group -R /media/disk
```

where :group is a group such as admin or optical

---

### Post by doas777 on 2010-01-14
ok, heres how I do it. first add all common users to the group 'users'.
then mount your disk. use chown to set all files to be owned by <youruser>:users, that way all your common users are part of the owner-group. then use chmod to turn on the suid and sgid. this will ensure that all files saved to the drive are owned by the group "users" and the owning user is the user that created the file.

---

### Post by Morbius1 on 2010-01-14
> So there are two problems there:
 - when I switch user on my desktop to another that user can't read data from the usb disks
 - I can't share data through network because smbd doesnot have read permissions on the created mount points The first part is a problem if you don't want to mount it through fstab because linux can't change ownership or permissions on a windows filesystem outside of a mount or fstab. ( and I'm assuming this is either a FAT32 or NTFS formatted USB device )

The second problem has an easy fix: 

Add the following line to smb.conf:
[B]
force user = your_login_user_name[/B]

Where to put that line depends on what method of file sharing you're using:

If it's Nautilus-share ( Nautlius > Sharing Options ) then add the line to [COLOR=Blue][global][/COLOR] section of smb.conf.

If you're using Classic Sharing then you need to add the line to the share definition section in smb.conf.

When you're done with the changes then issue a **sudo service samba restart**

---

### Post by bugagashka on 2010-01-29
You say:
*The first part is a problem if you don't want to mount it through fstab because linux can't change ownership or permissions on a windows filesystem outside of a mount or fstab. ( and I'm assuming this is either a FAT32 or NTFS formatted USB device )*

Can you explain me why?

---

### Post by bodhi.zazen on 2010-01-29
> **bugagashka said:**
> You say:
*The first part is a problem if you don't want to mount it through fstab because linux can't change ownership or permissions on a windows filesystem outside of a mount or fstab. ( and I'm assuming this is either a FAT32 or NTFS formatted USB device )*

Can you explain me why?

Because windows file systems (FAT/NTFS) do not understand permissions. Permissions are set at the time of mounting. Mounting a partition == prep the partition for use.

---

### Post by RhubarbMan on 2010-02-17
Ubuntu 9.10

Hi ! I've got the same problem. When the USB hard drive is connected at boot (or inserted after boot), the user that is logged in gets 'ownership' of the drive. Log out and in as another user and there's no access to it :-( I've spent HOURS being misled by udev, fstab and chown references with no success. I just want to poke a USB drive in and let whomever's logged in have full access to it. It's FAT32, so no user permissions on the files I'm afraid... Where do I control the automounted permissions ?

Secondly, this drive needs to be accessible via a samba share, which in theory means setting the 'directory' it's mounted into as a share. Simple enuff, but when the share name is determined by /media/'volume_name', ya can't samba share it until you know the mount point name , which isn't defined until you plug the drive in. I've set '/media' as the share atm until this is resolved.

I know his doesn't help fixing the reason for this post, but there's gotta be someone out there that can point us in the right direction.

Jem in Sussex

---

### Post by RhubarbMan on 2010-02-18
Just found this:

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501)

looks like it's a known issue with 9.10.

It also says that the problem isn't in Jaunty (9.04) so I'm gonna download that and try it. 

Many hours wasted so far...

I'll report back when installed and tried.

Jem.

---

### Post by RhubarbMan on 2010-02-21
Hi again,

The two problems don't happen in 9.04. Plop a USB disk in and all users have access to it. Leading on from this, it is also Samba shareable.

Sorted !

Two weeks (of evenings) trying to sort out a new Freevo box running on 9.10 cut down to one evening using 9.04. But 9.04 has issues that 9.10 doesn't so it might not be all plain sailing :-)

Hope this is helpful.

Jem.

---

### Post by Marky-boy on 2010-04-08
Thank god I finally found this thread! I have been driving myself MENTAL trying to get my usb ntfs media drive to share via samba after upgrading from 8.04 to 9.10. Was about to give up on linux over this, after 3 years of proud Ubuntu use.

Anyone know if this is resolved in Lucid betas? RC Beta 2 out today, so I might install that. I can't wait til end of April.

(Post #23 on the above linked bug by Matthew Holtz is spot on. When stuff like this breaks, even medium level IT-savvy people switch off completely.)

---

