---
title: "NTFS fsck freezes boot process"
date: 2006-06-17
forum: General Help
---

### Post by supreme_geek_overlord on 2006-06-17
Hi all,

I just switched to Ubuntu from a long-time Gentoo install because despite how much I love that much control, I simply can't keep up with everything while still having to use Windows.

Anyway, my problem has come while trying to set up access to my Windows partitions. I configured everything basically how it was on my old system -- the Windows boot partition is r/o with the built-in NTFS drivers, while my secondary HD with video projects is r/w with Captive NTFS. Here's my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hda2       /mnt/windows    ntfs    ro,nls=utf8,user,exec,umask=0222       0
/dev/hdb1       /mnt/secondary  captive-ntfs    user,exec,umask=0222    0      0
```

The problem now is that when I boot up, the initscripts get so far as "Checking all filesystems..." (or however it's worded) and the system simply stops. No disk activity or miscellaneous clickings whatsoever. Then, of course, I have to switch off the power strip with the entire house's networking equipment, which is somewhat of a pain to get working again.

Nonetheless, if I remove the last two lines from fstab, everything works fine and dandy, but I have to open a terminal and "sudo mount" them, which is a pain as well. When I decided to boot into recovery mode, it did the same thing (of course), but the extra output seems to suggest that it hangs on the first (non-Captive) filesystem check.

IIRC, ntfs-tools' fsck is not completed, am I right? Could this have anything to do with it? Other than that, I'm fresh out of ideas.

I can't seem to find anything about this on these forums or the net in general, so any help would be appreciated. Thanks in advance!

Tim


P.S.: There is, in fact, a zero under the "pass" column in the /dev/hda2 fstab entry, but I can't seem to get it to show in the forum. :s

P.S.S.: One thing that I hadn't noticed before is that the system aparantly hangs *after* the filesystem checks. The "ok" is there, but it doesn't proceed to the next item unless you press Ctrl+C. [shrug]

---

### Post by supreme_geek_overlord on 2006-06-20
[bump]

Anybody? [sigh] I must admit, Gentoo *did* have great forums. Nonetheless, I'm sure I'll get an answer soon. ;)

---

### Post by ercork on 2006-06-21
I had a similar problem - a very long delay on the checking filesystems part of the bootup. I changed the "pass" argument for my FAT32 partition from "2" to "0" and that fixed it. Yours is already at "0" so I don't know what the problem is.
As a short term fix, I would suggest removing the last two lines from your fstab so that they aren't mounted during boot. Then make a small little script which mounts the two drives and put that script in the System/Preferences/Sessions/Startup dialog. This will save you from personally mounting them each time. It's not the most elegant solution in the world, but hopefully it will be of some help to you.

---

### Post by supreme_geek_overlord on 2006-06-30
Thanks for the idea, ercork. If I can't find any other solutions, I'll try that.

---

### Post by caserio on 2006-06-30
Hi,

 *I would suggest removing the last two lines from your fstab so that they aren't mounted during boot*
Other possibility: add option noauto

Did you try changing  /mnt/windows (...) to /media/windows ? 
My windoze partition in fstab=

 /dev/hdb1 /media/hdb1 ntfs
nls=utf8,umask=007,uid=0,gid=46,noauto,ro,nouser 0 0

---

### Post by supreme_geek_overlord on 2006-07-01
[quote=caserio]
Other possibility: add option noauto[/quote]

I know I should test this out before I shoot my mouth off, but IIRC, I can't mount the partitions without opening a terminal and sudoing. I wanted it to mount at boot so that I wouldn't have to go through that process which, as I said in my first post, is a big pain. (This also presents a problem for ercork's suggestion, since I would have to sudo in the script, which would cause me to have to enter my password *twice* when I log in.)

Still, it might have just been the Captive NTFS partition that was giving me pain with that. I'll have to check it out and get back to you. If that *is* the case, perhaps I can "noauto" the plain ol' NTFS partition only and be able to mount the Captive one at boot without a problem. [ponders] We'll see.

[quote=caserio]
Did you try changing  /mnt/windows (...) to /media/windows ? 
My windoze partition in fstab=

 /dev/hdb1 /media/hdb1 ntfs
nls=utf8,umask=007,uid=0,gid=46,noauto,ro,nouser 0 0[/quote]

Like I said, I'm new to Ubuntu (as well as Gnome)... So what difference does it make whether it's in /mnt/ or /media/? I haven't quite figured out how Gnome handles all the automounting/vfs/blah stuff, and I haven't had time to read any manuals yet.

EDIT: Hmm... wait caserio, you're using Kubuntu. Well, disregard all that Gnome stuff -- I still don't know what you're talking about. :)

---

### Post by supreme_geek_overlord on 2006-07-01
Aha...

Well, it was in fact only Captive NTFS that needs me to be root. Now I'll try that previously mentioned solution and reboot to see if it works [crossing fingers]. Right now, I'm not going to worry about it though. ;)

Thanks for the help everybody.

---

