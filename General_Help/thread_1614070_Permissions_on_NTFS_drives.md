---
title: "Permissions on NTFS drives"
date: 2010-11-05
forum: General Help
---

### Post by ptrxyz on 2010-11-05
After the upgrade to Maverick it is no longer possible to change the file permissions on NTFS partitions.
Actually I can't remember how it was before and I do not know what exactly changed, but this is my scenario:

- I am keeping my music files on an external USB HDD on an NTFS partition (to be able to listen to my music on Windows systems)
- I made a bash script to organize my music collection. Before Maverick I was able to start the script directly (I made it executable using chmod. I had to do this only once, the execution bit was always present when I mounted the drive)
- Now I can not set the bit anymore and I have to start my script using "bash scriptname.sh", which is very annoying.
- I am NOT mounting the drive by hand, I let gnome (gvfs-fuse) do this for me. This is the desired behaviour, I don't want any new entries in fstab or do manual mounting.

I already googeled a bit and found out that there where some changes to NTFS-3G (renaming "default_permissions" paramter to "permissions" for example). I do not know if that might be related to this stuff.
Anyways, I would like to have the old behaviour back. This means, I want to be able to execute the script directly and I do now want that EVERY file is executable (like it would be if you set the default permission to 0700).
The best thing would be, if I could restore the old behaviour like it was at ubuntu 10.04 for example.

Does anyone know something about this? Thanks in advance!

BTW:
Yes, I know that posix permissions are not supported by NTFS file systems and yes i know that this might be a bit tricky or something. So please no spamming telling me this would not work. As I said, I do not want anything impossible, I just want the "old" behaviour back... =(

BTW2:
mount gives me:
...(other drives here)...
/dev/sdb1 on /media/Satellite type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by ptrxyz on 2010-11-05
Bump.

Does noone know something about this? Or is some information missing?

---

### Post by QLee on 2010-11-05
Have a look at this and see if there is anything helpful there.

Ownership and permissions of vfat / ntfs are set at the time of mounting.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by coffeecat on 2010-11-05
As you clearly understand, because NTFS doesn't support Unix permissions, permissions have to be applied through the mount options. Previous to Maverick, people were complaining of the exact opposite to you, that when they double-clicked on a text file, instead of it simply opening in a text editor, they were prompted whether to run it or not. The answer to that was to mount with the 'noexec' option which, of course, is what you do not want.

I guess, but don't know, that there has been a change in the default automount options so that it now includes noexec. I don't see noexec in your mount output, but I wonder if this is included in 'default_permissions'. Perhaps it is an upstream ntfs-3g change.

Whatever the devs do they're going to annoy half of the users. Some want the files executable, others not. The simple fact is that you cannot do fine-grained permissions control with NTFS. As far as I can see, you would need to edit the gvfs-fuse mount options, add a fstab entry, or use an external drive formatted with a Linux filesystem, none of which would seem to be feasible or acceptable for you.

I do, though, have a suggestion. Make sure your external drive partition has a unique partition label so that it is always mounted to the same mountpoint. Then you could keep your script in your home folder. You would obviously need to edit the paths to the music files in it.

---

### Post by mc4man on 2010-11-05
This was previous for ntfs in udisks source for defaults
> /* ---------------------- ntfs -------------------- */
/* this is assuming that ntfs-3g is used */

static const char *ntfs_defaults[] = { "uid=", "gid=", "dmask=0077", NULL };
static const char *ntfs_allow[] = { "umask=", "dmask=", "fmask=", NULL };
static const char *ntfs_allow_uid_self[] = { "uid=", NULL };
static const char *ntfs_allow_gid_self[] = { "gid=", NULL };


The current in mav. (red added
> /* ---------------------- ntfs -------------------- */
/* this is assuming that ntfs-3g is used */

static const char *ntfs_defaults[] = { "uid=", "gid=", "dmask=0077", [COLOR="Red"]"fmask=0770",[/COLOR] NULL };
static const char *ntfs_allow[] = { "umask=", "dmask=", "fmask=", NULL };
static const char *ntfs_allow_uid_self[] = { "uid=", NULL };
static const char *ntfs_allow_gid_self[] = { "gid=", NULL };

(vfat added a "showexec",  - to effect same

---

