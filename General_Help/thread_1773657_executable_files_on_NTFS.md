---
title: "executable files on NTFS?"
date: 2011-06-02
forum: General Help
---

### Post by m4lte on 2011-06-02
Hi there,

I have a shell script that is located on an NTFS partition.
However, I can't get the script to run from the NTFS partition. I suppose this has to do with the fact that permissions and the executable don't exist on NTFS.

Is there a way how I can execute a file that is saved on NTFS file system?

cheers!

---

### Post by JCM_Pico on 2011-06-02
NTFS doesn't support permissions, but if you check the file permission, you will notice that it should have read write and execute permission for all... So you are able to run the script there.
Probably the problem is within the script. Can you run the script in a filesystem that support permissions?

---

### Post by m4lte on 2011-06-02
I can run the script on an ext4 partition without problems.
I also believe that it used to run on the NTFS partition (though I'm not 100% sure). Probably the problems lies in something else ...

---

### Post by JCM_Pico on 2011-06-02
I tested a script in an NTSF partition and worked just fine...
Are you considering some paths that are not valid, or some file not present in your NTSF?

---

### Post by coffeecat on 2011-06-02
Linux read-write and executable permissions don't exists on NTFS filesystems it is true, but they can be set globally with mount options - as can ownership. How are you mounting the partition - automounting from the places menu, or with an entry in /etc/fstab? If the latter, try using the 'exec' option. The problem with that is that everything on the partition will be executable, which is irritating when you double-click on a simple text file in order to read it.

---

### Post by debd on 2011-06-02
As I have a very similar situation, I'm posting my problem right in this thread.

same story..cant make files xecutable on ntfs partitions.
so I edited my /etc/fstab and added the following line to have the files in the drive executable:
```
/dev/sda5 /media/books.docs.fun ntfs-3g noauto,users,rw,exec,suid,uid=1000,gid=1000,umask=002 0 0
```
Trying to mount this partition gives an error:
```
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```
I looked in synaptic, all ntfs-3g related  packages are installed and up-to-date.

Far from letting me mount the partition as the logged in user (uid 1000), mount is asking for root permissions, and the ownership of the files too belongs to root after mounting with su.
what's wrong with the line in fstab?

Thanks for any help.

---

### Post by debd on 2011-06-04
no replies after two days??

---

### Post by coffeecat on 2011-06-04
You have added a line to /etc/fstab to mount /dev/sda5 to /media/books.docs.fun when you boot up. So why are trying to mount it from the command line as well?

---

### Post by mc4man on 2011-06-04
> **coffeecat said:**
> You have added a line to /etc/fstab to mount /dev/sda5 to /media/books.docs.fun when you boot up. So why are trying to mount it from the command line as well?
He's using a noauto option
If you want to allow automount then you could simplify your fstab line quite a bit, though I think it's just as easy to move scripts to a fs where you can set permissions (or vfat where an end around exists

If you don't want to automount the I'd forget the fstab entry and just rebuild udisks with the old ntfs mount option and mount as normal from Places or Computer
In src/device.c around line 5875 remove red
```
/* ---------------------- ntfs -------------------- */
/* this is assuming that ntfs-3g is used */

static const char *ntfs_defaults[] = { "uid=", "gid=", "dmask=0077", [COLOR="Red"]"fmask=0177",[/COLOR] NULL };
static const char *ntfs_allow[] = { "umask=", "dmask=", "fmask=", NULL };
static const char *ntfs_allow_uid_self[] = { "uid=", NULL };
static const char *ntfs_allow_gid_self[] = { "gid=", NULL };
```

---

### Post by debd on 2011-06-04
Thanks for the replies.
mc4man, I'll try that when get back to my home PC.

---

### Post by jamesisin on 2011-06-04
Just as a best practice I would ***NOT*** mount a drive as globally executable.

Why store a script for Linux on a Windows drive?

---

