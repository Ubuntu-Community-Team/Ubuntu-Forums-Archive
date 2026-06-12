---
title: "default mounting behavior changed after Maverick upgrade"
date: 2010-10-19
forum: General Help
---

### Post by allium culpa on 2010-10-19
Hello all-- I'm obviously new to these forums; I apologize if I'm posting in the wrong place. I'll try to be as straightforward about this problem as I can.

I develop cross-platform applications and have a pretty standard dual-boot setup. Because I also use a cross-platform IDE the most convenient setup for me is to have all my project files and binaries in the same place, on an NTFS partition I have access to on both systems. Before upgrading from Lucid to Maverick, I never had any issues running my binaries on the NTFS partition, but now it seems I no longer have permission to. I realize I cannot set executable permissions for individual files on NTFS (indeed, in an effort to humor myself, I checked Properities > Permissions > Execute, and it unchecked itself immediately), and that the drive must be mounted with that permission. 

I don't have (and never have had) an fstab entry for my NTFS partitions-- I have always simply mounted them from the "Places" menu. When mounting my NTFS volume as usual, my mtab has this to say about it:

```
/dev/sda5 /media/foo fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
```After booting up a Lucid live CD, I can confirm that mounting drives in this manner most certainly gives me permission to execute programs by default, although the mtab says exactly the same thing. Neither "exec" nor "noexec" is listed as an option, so my hypothesis is that in the upgrade to Maverick, intentional or unintentional, direct or indirect, the default permissions was somehow changed.

I have no issues mounting -manually- and issuing the "exec" option. That is, using, say,

```
$ sudo mount /dev/sda5 /media/foo -o defaults,exec
```In that case, I have to create /media/foo myself, but I can run my binaries without issue. I guess I could even create a launcher to do this, so at least I don't have to rework my development setup in the meantime-- but I would very much prefer to be able to mount normally from my "Places" menu. I thought fstab would be a good place to start, so I tried:

```
/dev/sda5 /media/foo ntfs defaults,exec 0 0
```When I try mounting foo from the "Places" menu, I get:

> Unable to mount foo

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda5 on /media/fooSo, I tried:

```
/dev/sda5 /media/foo ntfs defaults,user,exec 0 0
```This time, when I try to mount from the "Places" menu, I get:

> 
"Unable to mount foo

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)I've fooled around with the fstab, and it seems that -any- options, even just "defaults", yields the "only root can mount" error (this includes the above excerpt from my mtab!), while appending "user" or "users" to the options yields the above error message. Additionally, it complains if I don't create the mount directory myself.

All I want is the exact behavior currently exhibited when mounting volumes from the "Places" menu, plus executable permission. One would think this a trivial task-- evidently, my NTFS volumes -used- to mount with executable permissions (I confirmed this behavior with the Lucid live CD), but a marathon of scouring the web for answers has not helped. Editing fstab is getting me nowhere, but I admit I have never fooled with it before now, and I could be doing something wrong. However, this is starting to feel like a bug.

As a side note, this is related to the matters being discussed _[here]("http://ubuntuforums.org/showthread.php?t=1596666")_ and _[here]("http://ubuntuforums.org/showthread.php?t=1599667")_, which I will be monitoring, but I feel this issue is more specific and merits its own thread.

So, if anyone could do any of the following:

[LIST]
[*] Offer a complete solution
[*]Reprimand me for doing something foolish, and then correct my mistakes
[*] Give me a nudge in the right direction
[*] Confirm I have encountered a bug, and in what (Maverick, NTFS-3G, FUSE)
[*] Explain why the mounting behavior seems to have changed since 10.04
[/LIST]
 he/she would have my undying appreciation.

Thank you for reading and for your time; I hope someone here can help me out.

---

### Post by dcstar on 2010-10-20
> **allium culpa said:**
> 
.........
```
/dev/sda5 /media/foo ntfs defaults,exec 0 0
```When I try mounting foo from the "Places" menu, I get:
........
[LIST=1]
[*]Do not "quote" information, "quote" is for previous postings.
[*]Do not manually mount thins in System folders, /media is a System folder exclusively for the system to dynamically mount removable devices. You do not have permissions to mount things there.
[/LIST]

---

### Post by allium culpa on 2010-10-20
> **dcstar said:**
> 
[LIST=1]
[*]Do not "quote" information, "quote" is for previous postings.
[*]Do not manually mount thins in System folders, /media is a System folder exclusively for the system to dynamically mount removable devices. You do not have permissions to mount things there.
[/LIST]


My apologies. I had wanted to offset the error messages in a box for readability, and felt quotation would be appropriate in this case.

I do realize /media is a system folder. In fiddling with fstab, I had hoped to alter the behavior of the Places menu so that it would behave in much the same way (plus executable privileges), which, of course, mounts dynamically in /media. When that did not work, I mounted manually via shell, but this was purely for diagnostic purposes.

Or did you mean to say I should also not mount there through fstab? In that case, how can I change the arguments the Places menu mounts with so that it continues to mount in /media, without fstab? I cannot find an intuitive (indeed, *any*) way to configure it.

Thank you for your reply, and best regards.

---

### Post by Morbius1 on 2010-10-20
There does seem to be a change in the default way that Ubuntu mounts ntfs partitions "on the fly" through Places if it's not in fstab. It takes the executable bit off the contained files. If you think about it that's the correct way to do it. I need to inestigate this a bit more.

Anyway, your original line in fstab should have corrected this issue:
```
 /dev/sda5 /media/foo ntfs defaults,exec 0 0
```[COLOR=Blue]*Note: the exec option is redundant in that it's already in the defaults but it's not harming anything.*[/COLOR]

You did create /media/foo first right? Something like this:
```
sudo mkdir /media/foo
```If you currently have sda5 mounted then unmount it and run the following command and post any errors:
```
sudo mount -a
```Come to think of it why not post your entire fstab:
```
cat /etc/fstab
```[COLOR=Blue]EDIT: and the output of this command as well:[/COLOR]
```
mount
```

---

### Post by allium culpa on 2010-10-20
> **Morbius1 said:**
> 
You did create /media/foo first right? Something like this:
```
sudo mkdir /media/foo
```
I did indeed. It seems like I shouldn't have to, since mounting from Places dynamically creates and destroys the directory, but it doesn't want to when there's an fstab entry for it-- maybe there's a good reason for this, but I don't know.

> **Morbius1 said:**
> 
If you currently have sda5 mounted then unmount it and run the following command and post any errors:
```
sudo mount -a
```Come to think of it why not post your entire fstab:
```
cat /etc/fstab
```[COLOR=Blue]EDIT: and the output of this command as well:[/COLOR]
```
mount
```

Certainly! Here goes. (NOTE: I've been using 'foo' shorthand for convenience; I'll begin using the actual volume name 'CAPRICORN' for consistency with any fdisk/fstab/etc output and with the native mounting behavior)

After manually creating the directory,```
/dev/sda5 /media/CAPRICORN ntfs defaults,exec 0 0
``````
sudo mount -a
``` yields.. no output! CAPRICORN mounts as it should. It won't let me right click > Unmount it, although I can sudo umount it. After unmounting, clicking it under Places yields the "only root can mount" error, as mentioned above (this is why I attempted to add the "user" option before, but I admit I don't fully understand it).

```
cat /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda4 :
UUID=cec4d223-19ae-47c6-a563-0cc9a8a93d2e	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda6 :
UUID=f4e21347-8e81-4552-8f9f-d808d60add78	none	swap	sw	0	0
#Entry for /dev/sda5, added manually
/dev/sda5 /media/CAPRICORN ntfs defaults,exec 0 0

```
Executables, of course, run fine. Again, the last entry was only added recently, by myself. Previously there was no fstab entry for /dev/sda5.

While /dev/sda5 is still mounted,
```
mount
```
```
/dev/sda4 on / type ext4 (rw,errors=remount-ro,commit=0)
/dev/sda4 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/christopher/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=christopher)
/dev/sda5 on /media/CAPRICORN type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

Sorry for the size of this, I didn't want to snip out any potentially relevant pieces. Thanks for replying, I hope this output is useful.

---

### Post by Morbius1 on 2010-10-20
You've confused me. First:
> I did indeed. It seems like I shouldn't have to, since mounting from  Places dynamically creates and destroys the directory, but it doesn't  want to when there's an fstab entry for it-- maybe there's a good reason  for this, but I don't know.When you go through Places Ubuntu by default will dynamically create a mountpoint at /media/"LABEL of the partition that is being mounted" If you create an fstab entry for that partition then that mechanism is removed.
> CAPRICORN mounts as it should. It won't let me right click > Unmount  it, although I can sudo umount it. After unmounting, clicking it under  Places yields the "only root can mount" error, as mentioned above (this  is why I attempted to add the "user" option before, but I admit I don't  fully understand it).The "user" option is a completely misunderstood option. Rather than bore you think of it this way. At the moment fstab is read and executed during boot there is only one user and that's root. You are not root so you can't unmount it.

This is whats confusing me:
> Executables, of course, run fine.Then what's the issue.

It does appear that the default "mount on the fly" mechanism is different than it used to be, but adding an fstab entry fixes it.

If the problem is you want to unmount it as a normal user you have to ask yourself why? What's wrong with having it permanently mounted?

---

### Post by allium culpa on 2010-10-20
> **Morbius1 said:**
> You've confused me. First:
When you go through Places Ubuntu by default will dynamically create a mountpoint at /media/"LABEL of the partition that is being mounted" If you create an fstab entry for that partition then that mechanism is removed.

That was what was confusing *me*-- I didn't realize creating an fstab entry for a partition would *by design* disable on-the-fly mounting from Places. I think a little  bit of that confusion may have been a result of the 'noauto' fstab option. Its existence gave me the impression that it would not auto-mount the volume at boot, and as such would *require* (and by extension, allow) the user to mount/unmount it manually. It also may have been an incorrect assumption that when the Places default mounting behavior was changed in this upgrade, it could be reverted (I thought perhaps fstab could do this).

> **Morbius1 said:**
> 
If the problem is you want to unmount it as a normal user you have to ask yourself why? What's wrong with having it permanently mounted?

Well, when I think about it, there really *isn't* anything *wrong* with that at all. I suppose it's simply that I've grown used to the behavior.

Let me just make sure this is correct. Creating an fstab entry, by design, will disable the on-the-fly mounting/unmounting mechanism. So, *if* there is a way to get the (exact) old behavior out of the Places menu, it isn't in fstab. If I understand this correctly, then that's fine-- I can live with automount. I guess I'm just stubborn :P

I'd venture a guess that the behavior was changed for security reasons, and I can respect that. On a practical level it's really only a minor inflexibility and a minor irritation, so I guess there's no harm done (in my case) and I shouldn't complain. I do wonder how many other people this might confuse after upgrading, though?

If there is a way to revert the behavior normally, I would still like to know, if only for the sake of knowing the *proper* way of doing it. But I think I understand the situation better now, and I greatly appreciate your help in that.

(Should I go back and mark the thread solved? Technically we haven't established how to revert to pre-10.10 on-the-fly mounting/unmounting behavior, but I can be satisfied with the enlightenment I got)

---

### Post by Morbius1 on 2010-10-20
> Creating an fstab entry, by design, will disable the on-the-fly mounting/unmounting mechanism.Correct
> I think a little  bit of that confusion may have been a result of the  'noauto' fstab option. Its existence gave me the impression that it  would not auto-mount the volume at boot, and as such would *require* (and by extension, allow) the user to mount/unmount it manually.This may confuse you more but.... The "user" / "noatuo" option combination ( really the only time the user option makes sense in fstab ) can be used just as you described for everything other than NTFS. With NTFS it's a fuse / ntfs-3g driver thing. Modifications would have to be made to the linux internals to make that happen and that's beyond my pay grade. :wink:

The "on the fly" mechanism of mounting an ntfs partition though places is exactly as it has always been. What has changed is the resulting default permissions that are placed on it. Now the mount point and all directories have permissions of 0700 ( no change from previous ) and all files have permissions of 0600 ( the execute bit having been removed - and this is new behavior ). This is the third ( or maybe second - I'm loosing track ) time in a row that this has happened and I agree it's becoming quite annoying.

---

### Post by allium culpa on 2010-10-20
> **Morbius1 said:**
> Correct
This may confuse you more but.... The "user" / "noatuo" option combination ( really the only time the user option makes sense in fstab ) can be used just as you described for everything other than NTFS. With NTFS it's a fuse / ntfs-3g driver thing. Modifications would have to be made to the linux internals to make that happen and that's beyond my pay grade. :wink:


On the contrary, while I don't understand *why* that is so, it does go a long way to explaining the matter, and why the "user" option threw a cryptic error about fuse / ntfs-3g on me instead of behaving as I had hoped.

> 
The "on the fly" mechanism of mounting an ntfs partition though places is exactly as it has always been. What has changed is the resulting default permissions that are placed on it. Now the mount point and all directories have permissions of 0700 ( no change from previous ) and all files have permissions of 0600 ( the execute bit having been removed - and this is new behavior ). This is the third ( or maybe second - I'm loosing track ) time in a row that this has happened and I agree it's becoming quite annoying.

That makes even more sense. I had my suspicions it may have been something like that, but I don't know enough about that to be sure. The matter is vaguely reminiscent of the gnome sound preferences dialog (or whatever it's called, logged into a kde distro atm) that mysteriously and frustratingly transformed every upgrade. :wink: But I'll forgive Meerkat just this once, as I'm too happy about finally having working ACPI (patch in recent kernel) to hold a grudge. But next time? You watch out, Natty Narwhal! :twisted:

I'll mark this as solved, then, since the mystery seems to be cleared up. Thanks again for your help and for your patience! Hopefully this will be of some use to the next poor soul who encounters the same. Best regards!

---

