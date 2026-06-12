---
title: "File system format for Mac OSX 10.5 and Ubuntu for large files"
date: 2010-09-19
forum: General Help
---

### Post by fantastic on 2010-09-19
Is there a file system that both Mac OSX 10.5 and linux can read/write for large files (like 4gb files)?

My desktop is Ubuntu and I run most from there, but I want to back up my MacBook and linux box on the same external hard drive. 

Seems there are some (paid) apps for Mac that will mount NTFS but I'm wondering if there is just a shared files ystem that will work for both.

---

### Post by uselpa on 2010-09-19
Since HFS+ and ext4 (or whatever you use on Ubuntu) are quite different, the best option is to use FAT32 and then put your backup into some sort of container:
- a sparsebundle for HFS+
- a tar archive for ext.

---

### Post by fantastic on 2010-09-19
> **uselpa said:**
> Since HFS+ and ext4 (or whatever you use on Ubuntu) are quite different, the best option is to use FAT32 and then put your backup into some sort of container:
- a sparsebundle for HFS+
- a tar archive for ext.

Is there something that will hold files 4.3gb in size? FAT32 is limited to 4gb. (That's my fault, I should have specified in the original post my largest file size).

---

### Post by jocko on 2010-09-19
I'm pretty sure ubuntu have read+write support for HFS+ (but you may need to install  the package "hfsplus" from the repo to be able to write to a journalled HFS+).
So there should be no need to make a microsoft file system just to share files between mac and linux.

---

### Post by Joe of loath on 2010-09-19
Yup, Ubuntu can r/w HFS+. My friend's iPod was formatted on his mac, and I could still put music on it with 9.10.

---

### Post by fantastic on 2010-09-19
> **jocko said:**
> I'm pretty sure ubuntu have read+write support for HFS+ (but you may need to install  the package "hfsplus" from the repo to be able to write to a journalled HFS+).
So there should be no need to make a microsoft file system just to share files between mac and linux.

So just plug the drive into the Mac and let it format itself with the journaled HFS+?

Sounds like a fun filled day of moving data from one external drive to another drive, format external drive, then back to the external drive and then to another entirely separate external drive (which I keep locked away)... 

Will someone at least make me some pancakes when I'm done... sounds so exhausting, like I'm doing a triathlon 

[And thank you for the help :) ]

---

### Post by srs5694 on 2010-09-19
By default, Linux won't write to a *journaled* HFS+ volume, so you should set it up *without the journal.* Once that's done, you'll be able to use it for read/write access. Of course, without the journal, you'll have longer disk check times when you experience system crashes, power failures, or other such events; but that's probably an acceptable price to pay. I believe there's a way to get Linux to mount journaled HFS+ with read/write access, but I don't recall the details.

Another option would be to use ext2fs or ext3fs; there are OS X drivers for these. I can't say I've ever used them, though, so I don't know how well they work. Try Googling "ext2fs MacOS" or something similar to find them. If you go this route, I'd be careful not to give OS X access to the Linux root (/) filesystem, just to the shared-data partition, or /home if you've got a separate /home partition and decide to use it for that purpose.

Overall, I'd say that non-journaled HFS+ is probably the best way to go.

One extra comment: Both OS X and Linux use the same Unix-style permissions and ownership. The result is that you're likely to find that ownership seems to shift when you reboot your OS. You can set up permissions so that they're lax on files on the shared volume (giving full read/write access to everybody) or you can adjust the user ID (UID) values in one OS so they match those used by the other one. The former will be an ongoing nuisance, whereas the latter will require use of moderately advanced system administration tools (such as usermod and chown or GUI equivalents) on a one-time basis.

---

### Post by fantastic on 2010-09-19
> **srs5694 said:**
> By default, Linux won't write to a *journaled* HFS+ volume, so you should set it up *without the journal.* Once that's done, you'll be able to use it for read/write access. Of course, without the journal, you'll have longer disk check times when you experience system crashes, power failures, or other such events; but that's probably an acceptable price to pay. I believe there's a way to get Linux to mount journaled HFS+ with read/write access, but I don't recall the details.

Another option would be to use ext2fs or ext3fs; there are OS X drivers for these. I can't say I've ever used them, though, so I don't know how well they work. Try Googling "ext2fs MacOS" or something similar to find them. If you go this route, I'd be careful not to give OS X access to the Linux root (/) filesystem, just to the shared-data partition, or /home if you've got a separate /home partition and decide to use it for that purpose.

Overall, I'd say that non-journaled HFS+ is probably the best way to go.

One extra comment: Both OS X and Linux use the same Unix-style permissions and ownership. The result is that you're likely to find that ownership seems to shift when you reboot your OS. You can set up permissions so that they're lax on files on the shared volume (giving full read/write access to everybody) or you can adjust the user ID (UID) values in one OS so they match those used by the other one. The former will be an ongoing nuisance, whereas the latter will require use of moderately advanced system administration tools (such as usermod and chown or GUI equivalents) on a one-time basis.

Woops. I already did it as journaled HFS+. Can I still mount this as read/write? Right now it mounts as read.

---

### Post by srs5694 on 2010-09-19
It's possible to disable the journal on HFS+. [Here's](http://blog.julipedia.org/2007/04/how-to-disable-journaling-on-hfs-volume.html) one Web page with an OS X command that's supposed to do it. I've not tested this, though. If it doesn't work for you, try a Web search on "disable HFS+ journal" or something similar.

---

### Post by fantastic on 2010-09-19
> **srs5694 said:**
> It's possible to disable the journal on HFS+. [Here's](http://blog.julipedia.org/2007/04/how-to-disable-journaling-on-hfs-volume.html) one Web page with an OS X command that's supposed to do it. I've not tested this, though. If it doesn't work for you, try a Web search on "disable HFS+ journal" or something similar.

SRS, thanks for the help but I'm giving up today...

I tried various things. I did get it to write once when mounted to Ubuntu, but then had problems mounting in Mac. 

I haven't really investigated that MacFUSE for the ext3fs...

At this point I'm thinking just leave on NTFS so I can write large files in both Mac and Linux and then another drive in FAT for bantam little files to write in Mac, Linux and Windows. It then defeats my purpose of having two separate external hard drives backing up data....

Grrrr... what a frustrating day.

---

### Post by srs5694 on 2010-09-19
*Do not* use NTFS on a drive that's used only on Linux and Mac OS X! Neither Linux nor (AFAIK) OS X provides disk maintenance tools for NTFS that do much more than just flag the filesystem as needing an automatic check in Windows. When you suffer a power failure, system crash, accidental cable removal, or similar problem, the drive will become unmountable in both Linux and OS X until you can check it with Windows. Depending on the sort of drive, your computers, and your access to Windows, this could be a nuissance or a very serious problem. Murphy's Law says it'll happen at the least convenient possible time, too -- say, when your Windows installation has died or when you're travelling and don't have access to the Windows desktop system you'd planned to use for this sort of thing.

HFS+ *can* be made to work in Linux. I've done it. Just for giggles, I even used it as my /boot partition filesystem on one computer and it was fine for that. I don't believe I've ever disabled the journal, though; when I used it for Linux/OS X data exchange, I made sure to create it with the journal disabled from the start.

---

### Post by uselpa on 2010-09-20
Being a backup maniac, I still recommend **against** using HFS+ in this case.

If you really want to go that way, make sure that you run a test such as Backup Bouncer for the Mac ([http://www.n8gray.org/code/backup-bouncer/](http://www.n8gray.org/code/backup-bouncer/)), and something equivalent for ext4.

Just to make sure that you will not have any surprises should you have to restore from your backup.

---

### Post by srs5694 on 2010-09-20
> **uselpa said:**
> Being a backup maniac, I still recommend **against** using HFS+ in this case.

As I see it, there are very few options. The OP specified as requirements the ability to read and write in both OS X and in Linux and the ability to hold files larger than 4 GB. The large-files requirement rules out FAT, which might otherwise be a good choice. It also eliminates the old (non-Plus) HFS, which tops out at a 2 GB file size, according to Wikipedia. AFAIK, only three filesystems fit the bill:


[list]
[*]**HFS+** -- accessible with standard tools in both OSes, provided the journal is disabled. Supports Unix-style ownership and permissions, as used in both OSes.
[*]**Ext2fs/ext3fs** -- Linux support is as good as it gets, of course. Mac support relies on free driver packages, but I don't know how good those drivers are.
[*]**NTFS** -- Supported for read/write using NTFS-3g in both OSes; however, the lack of filesystem check tools makes it a poor choice, IMHO. NTFS also uses different ownership and permission systems than either OS X or Linux, which could be a plus or a minus.
[/list]


Of those three, I personally would pick HFS+; however, if I knew more about the state of ext2fs/ext3fs support in OS X, I might be more willing to go with it. If the OS X drivers support the ext3fs journal, that would certainly be a point in its favor. NTFS is just a bad choice.

I really don't see what backups have to do with it. Whether the choice is HFS+ or ext2fs/ext3fs, a native filesystem backup tool can be used from the filesystem's native OS, or something filesystem-neutral (like tar) can be used from either OS. I doubt if exotic file types will be an issue, since the partition will house user data, not device nodes or whatnot.

---

### Post by Sharpie1 on 2010-11-24
I formatted a 1TB external USB drive on a friends Mac, in non-journalled HFS+, in order to share files between Mac and Ubuntu. I used a program called Krusader, in Root mode, to copy the files from Ubuntu over to the drive, because if I tried to drag and drop, I got a message saying I had insufficient permissions.
I have some questions for the savvy:
Is there a simple (ish) way to permanently alter the "ownership" of the entire drive, so that both mac and Ubuntu can access it ? 
Or a way of fooling the mac and Ubuntu systems into thinking they are the same user, so they can share the data (not at the same time - moving from one separate computer to another)
Also if I start Krusader as root, it complains "Error: "/var/tmp/kdecache-[myusername]" is owned by uid 1000 instead of uid 0"
And if I try to make md5 checksums on the files on the drive, so that I can then compare them with the originals, (all large video files around 2GB) Krusader puts up a progress bar that say 50% -80% -50% -30% indefinitely.
I used a similar program in Windows called Total Commander that copied files from one window to another, and when asked to confirm Copy ? would give you the option of verify, and after copying, would check one file against the other. If anyone knows of a simple or elegant way of doing this, with Krusader or Double Commander, Id be very grateful !
sorry for the long list of questions !

Sharpie1

---

