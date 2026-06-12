---
title: "Change permission on FAT32???"
date: 2012-07-25
forum: General Help
---

### Post by Bucky Ball on 2012-07-25
Hi all,

External drive connecting via SATAII, three FAT32 partitions (don't ask). Can mount/unmount fine but permission set to root, not user, and can't change, regardless of what I've tried.

Any takers? Starting to think the only solution is to reformat but first release (10.04) I've ever had any trouble with. All fine in others (8.04 through 12.04) I didn't find something about this being a bug but also suggestions it had been fixed, probably in the next release, though! 

I'll keep digging cos need to move some things around. ;)

---

### Post by oldfred on 2012-07-26
I think on Windows formats, the owner is always root, but it does not matter.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

My NTFS shows  fred:root for everything.

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by Bucky Ball on 2012-07-26
Thanks oldfred, but second link, post #6 is referring to ntfs and ext, not fat. Is the ntfs line the same and simply change ntfs to vfat?

The first link looks promising. Remembering, don't want to mount this external drive every boot. Just want to be able to plug it in when required, switch it on, and have read/write permission. If I add the appropriate line to fstab I'm figuring this will only be picked up at boot, not mount the external FAT partition with permissions when I switch the drive on.

My plan is  actually to get a terrabyte drive, back this 500Gb one up and reformat to something more palatable. I formatted this in 2007 and had to be FAT for what I was doing at uni at the time.

What's got me is that 10.04 is the only install it doesn't work in (on that machine). All other releases I just plug in, turn on, and I'm away with all permissions ... what have they got that 10.04 doesn't??? Still, it is Xubuntu and not Ubuntu install so maybe there's something missing (and no, I don't have permissions in Nautilus, either). ;)

---

### Post by oldfred on 2012-07-26
The psychocats had a FAT example which is close to what I used to use. I converted my shared with XP data partition from FAT to NTFS in 2009. 

# before uuid  /dev/sda4 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0
UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0
> umask=000 sets the permissions of files and folders to 777 or rwxrwxrwx.
      umask=value
              Set the umask (the bitmask  of  the  permissions  that  are  not
              present).  The default is the umask of the current process.  The
              value is given in octal.
       dmask=value
              Set the umask applied to directories only.  The default  is  the
              umask of the current process.  The value is given in octal.

       fmask=value
              Set the umask applied to regular files only.  The default is the
              umask of the current process.  The value is given in octal
the new UEFI/efi partition is fat and I copied this from someone who had that (the 1 at end looks wrong now as Linux does not fsck FAT partitions even though now that is a system partiton?):

efi partition
# /boot/efi was on /dev/sda1 during installation
UUID=EA74-F7BE  /boot/efi       vfat    defaults        0       1

---

