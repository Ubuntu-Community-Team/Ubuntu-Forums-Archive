---
title: "System disk changes to Read Only arbitrarily"
date: 2009-08-11
forum: General Help
---

### Post by mvandemar on 2009-08-11
Earlier today as I was working on some stuff I suddenly could not save anything. The entire disk had changed to read only. I powered down, and when I brought it back up the boot failed, and said it could not run fsck automatically, I needed to do so manually. I did, and had to answer "y" to a few hundred questions about inodes that "has EXTENTS_FL flag set on filesystem without extends support" and did I want to fix, and inodes with 0 dtime. I went on the assumption that yes, they should be fixed, and just answered yes to them all.

Logged back in, and aside from my email IMAP directory needing to be re-downloaded it seemed ok, but now 4 hours later it just happened again. I have not logged out and run fsck again because I am hoping to get some feedback before I do, in case that's not the actual solution. A search on the EXTENTS_FL message and [ubuntu read only error] did not seem to yield any results that would apply to this issue, since it is a system disk with no changes that flipped while it was in use. I think the last update was 2 days ago, machine has been running fine since them up until just now.

I am running Ubuntu 8.10, and cannot get much more info at this time because neither About Ubuntu or About Gnome widows will open for me (they open, but no info). Sysinfo won't open at all, nor will htop, nor terminal for that matter (blank window, no prompt).

Please help. :)

Thanks.

-Michael

---

### Post by Cato2 on 2009-08-11
This is a weird one, I hope you have up to date backups as it's a sign of disk or filesystem corruption when the FS goes readonly as you may know.  Ubuntu isn't that great at flagging this.

You may have lost quite a lot of data, so probably you need to back up anything you can get hold of, onto a fresh disk, and reinstall...  You need to boot from a live CD to recover stuff.

As to why it happened, I have no idea - possibly an ATI driver issue based on some Fedora reports(?) but could be something else entirely. See the Red Hat entry at [http://www.google.co.uk/search?q=extents_fl+flag+set+on+filesystem+without+extents+support](http://www.google.co.uk/search?q=extents_fl+flag+set+on+filesystem+without+extents+support) - does seem to indicate an ATI driver is at fault.  

When you reinstall, I would recommend you disable write caching on all disks (hdparm -W0 /dev/sda for example) and consider setting data=journal on ext3 in fstab, and using tune2fs for the root FS.  I have started doing this to ensure data integrity on ext3, as it's actually highly vulnerable to disks re-ordering write operations (when there is a crash).

To recover your data, see my posts on [http://ubuntuforums.org/showthread.php?p=7769865](http://ubuntuforums.org/showthread.php?p=7769865)

---

### Post by mvandemar on 2009-08-11
> **Cato2 said:**
> This is a weird one, I hope you have up to date backups as it's a sign of disk or filesystem corruption when the FS goes readonly as you may know.  Ubuntu isn't that great at flagging this.

You may have lost quite a lot of data, so probably you need to back up anything you can get hold of, onto a fresh disk, and reinstall...  You need to boot from a live CD to recover stuff.

As to why it happened, I have no idea - possibly an ATI driver issue based on some Fedora reports(?) but could be something else entirely. See the Red Hat entry at [http://www.google.co.uk/search?q=extents_fl+flag+set+on+filesystem+without+extents+support](http://www.google.co.uk/search?q=extents_fl+flag+set+on+filesystem+without+extents+support) - does seem to indicate an ATI driver is at fault.  

When you reinstall, I would recommend you disable write caching on all disks (hdparm -W0 /dev/sda for example) and consider setting data=journal on ext3 in fstab, and using tune2fs for the root FS.  I have started doing this to ensure data integrity on ext3, as it's actually highly vulnerable to disks re-ordering write operations (when there is a crash).

To recover your data, see my posts on [http://ubuntuforums.org/showthread.php?p=7769865](http://ubuntuforums.org/showthread.php?p=7769865)

Cato, thanks. Is there anything else aside from reinstall that I could try first? Will I harm anything by allowing fchk to fix the issues it finds? I am not running any ATI drivers afaik, but I am running the restricted drivers for my nvidia card. Do you think if I get it back into read-write mode and disable those (go with the recommended) it might have any effect? Any harm in trying?

Thanks again.

-Michael

---

### Post by dcstar on 2009-08-12
> **mvandemar said:**
> Earlier today as I was working on some stuff I suddenly could not save anything. The entire disk had changed to read only. **I powered down**, and when I brought it back up the boot failed, and said it could not run fsck automatically, I needed to do so manually. I did, and had to answer "y" to a few hundred questions about inodes that "has EXTENTS_FL flag set on filesystem without extends support" and did I want to fix, and inodes with 0 dtime. I went on the assumption that yes, they should be fixed, and just answered yes to them all.
........

The root filesystem is mounted so if there is an error it goes into RO mode to preserve your existing data, your hardware is obviously causing these errors and you need to find out why.

If you "powered down" by just powering off the PC instead of going through the correct shutdown procedure, then you will greatly increase the chances of corrupting your data.

---

### Post by Cato2 on 2009-08-12
> **mvandemar said:**
> Cato, thanks. Is there anything else aside from reinstall that I could try first? Will I harm anything by allowing fchk to fix the issues it finds? I am not running any ATI drivers afaik, but I am running the restricted drivers for my nvidia card. Do you think if I get it back into read-write mode and disable those (go with the recommended) it might have any effect? Any harm in trying?


You can try recovering your data, and if you have the space I'd recommend doing an image backup using gddrescue, from a Live CD - see my other post and the Ubuntu DataRecovery page, and also Parted Magic (live CD).  If you can mount the filesystems with your data (/home and /etc) I'd also back those up by simply copying the files onto an external drive.

You can try letting fsck fix all the issues (fsck -y I think) but do this AFTER you have backed up.  My recent experience of a similar issue was that I had a bootable system that was mostly working - then I did an fsck and it was completely hosed and unbootable (but of course with a fixed filesystem).  When you get this many errors, backing up data must be your first priority.

It probably isn't the Nvidia driver, and in any case the first thing is to recover your data. 

Implementing my suggestions about writeback caching (put this in the /etc/rc.local on the recovered system) and data=journal will *probably* avoid disk corruption in future, or at least make it far less likely.  Writeback caching combined with ext3 is really evil, and should be banned!

The commands for /etc/rc.local are:

```
# Disable write caching on all hard disks
hdparm -W0 /dev/sdb
hdparm -W0 /dev/sda

```

---

