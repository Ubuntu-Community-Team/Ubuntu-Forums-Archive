---
title: "&quot;error occured while mounting /media/....&quot;"
date: 2012-01-17
forum: General Help
---

### Post by oktorockto on 2012-01-17
Still new to Ubunbtu (11.10) and been having a few problems. Whilst trying to share a drive between partitions I seem to have automounted two of my three hard drives into the Media folder and I now get the message above and the press S to skip mounting or M for manual recovery message. Can anyone help me here?

---

### Post by WorMzy on 2012-01-17
Post the contents of your fstab.

```
gedit /etc/fstab
```

---

### Post by oktorockto on 2012-01-18
Hi - thanks. I do know that I can't edit the fstab because I think I have messed up the permissions

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=96388fff-70be-4515-afd5-30ddf136f547  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda5 during installation
UUID=5222e70e-7290-4360-bbd7-c75600f4fdb1  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/New 500  ntfs  nls=iso8859-1,ro,users,umask=000,user  0  0  
/dev/sdb1                                  /media/sdb1     ntfs  defaults                  0  0  
```

---

### Post by WorMzy on 2012-01-18
Ok, the two bottom lines are both for the same partition, the second-from-bottom one is malformed, and it looks like neither is using the ntfs-3g driver (although that could depend on which version of Ubuntu you're using).

You should be able to edit the file if you use
```
gksudo gedit /etc/fstab
```

Run that command from a terminal, and if you get any error messages that prevent you from editing the file, post them here.

If the file opens okay, just comment out (add a hash [#] to the start) the two bottom lines, then save. You shouldn't need the floppy disk line either, but maybe you have you own reasons for having that.

That should get rid of the mount error problem, but it leaves you without your shared partition mounted when you boot. So, post the output of

```
sudo blkid -c /dev/null
```

and let us know which partition is your shared partition (unless it's clearly labelled "shared" or something obvious)

---

### Post by oktorockto on 2012-01-18
Thanks again. I tried that and it did indeed let me comment it out and I managed to save it. Haven't tried re-booting yet however as thought I better paste the error message that also came up in the terminal:

```
pauladmin@paul-indoorPC:~$ gksudo gedit /etc/fstab

(gedit:2206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.7KXF8V': No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9N397V': No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.J85F8V': No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
pauladmin@paul-indoorPC:~$ 

```

My first post on the forum - [here]("http://ubuntuforums.org/showthread.php?t=1910651") explains a little more of my problems.

Back with the results of ```
sudo blkid -c /dev/null 
``` soon

---

### Post by WorMzy on 2012-01-18
> **oktorockto said:**
> Thanks again. I tried that and it did indeed let me comment it out and I managed to save it. Haven't tried re-booting yet however as thought I better paste the error message that also came up in the terminal:

```
pauladmin@paul-indoorPC:~$ gksudo gedit /etc/fstab

(gedit:2206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.7KXF8V': No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9N397V': No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.J85F8V': No such file or directory

(gedit:2206): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
pauladmin@paul-indoorPC:~$ 

```

Don't worry about those, they're just warnings that you get because root doesn't have certain directories in it's home folder, since it doesn't need them.

---

### Post by oktorockto on 2012-01-18
Hello again, I entered ```
sudo blkid -c /dev/null
```

Here is the result

```
/dev/sda1: LABEL="Western500" UUID="3C68A9C468A97CF0" TYPE="ntfs" 
/dev/sdb1: LABEL="Home system" UUID="28844B0B844ADAC8" TYPE="ntfs" 
/dev/sdc1: UUID="96388fff-70be-4515-afd5-30ddf136f547" TYPE="ext4" 
/dev/sdc5: UUID="5222e70e-7290-4360-bbd7-c75600f4fdb1" TYPE="swap" 
```

So my two physical NTFS drives are the Western500 and the Home system. Home System has an XP partition on it. Ubuntu is on a separate 500gb hard drive.

I want to be able to auto-mount and share both NTFS drives between different user accounts - hopefully with some only seeing them as read only - thats what got me into trouble in the first place although I did try to work it our from the forum first.

---

### Post by WorMzy on 2012-01-18
I advise you not to auto mount your Windows partition, for the simple reason that Ubuntu doesn't know and doesn't care what's important to Windows and won't make any attempt to correct you if you (or someone else) try to delete something (accidentally or otherwise) that Windows relies upon to boot/operate correctly.

That said, if you want to run the risk, go ahead. It's your PC and you do what you please.

You've complicated matters by wanting to have certain directories available to certain users, but it's not impossible to do that with ntfs partitions. NTFS (and FAT) partitions don't support UNIX file permissions (which Linux uses to determine who can read, write, and execute what), so you have to tell the mount application to fake one set of permissions for every file and folder on the partition when it mounts. The permissions that the mount utility set cannot be changed, except by remounting the filesystem with a different set of permissions. One mount, one set of permissions.

```
UUID=3C68A9C468A97CF0 /media/Western500 ntfs-3g defaults,uid=pauladmin,gid=pauladmin,umask=000 0 0
```

Adding that line to your fstab, creating the /media/Western500 folder, and making sure that you have the ntfs-3g package installed, will make your shared partition automount under *your* ownership while allowing *anyone* to read, write and execute *anything*. Alternatively,

```
UUID=28844B0B844ADAC8 /media/WinXP ntfs-3g defaults,uid=pauladmin,gid=users,umask=007 0 0
```

will automount the WinXP partition (assuming /media/WinXP yadda yadda, see above) under *your* ownership, will also allow anyone in the "*users*" group to read, write, and execute to anything (as well as yourself), but anyone else will have **no** access to the partition (at least, without the use of sudo or similar tools).

With me so far?

---

### Post by oktorockto on 2012-01-18
Cool,

I'll look at this tomorrow night. Actually, I don't need to share the windows partition at all - I can keep that as a separate boot. I think I get a case of "need access to everything in every permutationitis" sometimes.

So then I could just format the remaining NTFS drive into ext 4 after I have backed everything up?

And then go about sharing it. I now think I understand that when I was trying to set permissions it didnt work because they were NTFS partitions. I'm going to do some serious reading over the next few months and suss it all out so I can free up some forum space.

---

### Post by WorMzy on 2012-01-18
You can format the partition as ext4 if you want to, but then you won't be able to access it from Windows (at least, not without the use of third-party ext drivers, and I can't vouch for those). imo, ntfs is the best filesystem to use for shared partitions.


What I didn't get to in my last post is a way of circumventing the limitations of the ntfs partition through the use of a little-known utility called bindfs.

Sisco's written out a tutorial about it, and I recommend that you read it if you decide to stick with ntfs, but want to have specific ownership/permissions for specific folders.

[http://ubuntuforums.org/showthread.php?t=1460472&highlight=bindfs](http://ubuntuforums.org/showthread.php?t=1460472&highlight=bindfs)

I haven't read it myself, as I have little use for bindfs, but I have tested it with ntfs, and it works perfectly. I suggest mounting the partition itself with uid=root,gid=root,umask=777 (to keep everything protected by default), then using bindfs to bind specific folders as you need them.

---

### Post by oktorockto on 2012-01-19
I tried bindfs. I think thats where I messed things up. I was pretty sure I knew what I was doing with permissions etc but I think I need a better read. Ok, so maybe stay with NTFS for the shared drive and leave the XP drive unshared.

Looking again, I reckon I just tried to share folders on the drives without mounting the partition as a shared partition first. Must stop jumping in headfirst without checking for rocks. Thanks very much for your help.

---

