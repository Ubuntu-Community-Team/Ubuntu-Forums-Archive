---
title: "Error encounterd whilst mounting /home"
date: 2010-05-11
forum: General Help
---

### Post by dowtish on 2010-05-11
After installing some updates on  10.04

I get the message error encountered whilst mounting /home (on start-up)!

Press S to cancel or M to mount manually!

Unsure what is going on but noticed on a previous post that the following info was made available to solve problem!

# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=7ecaaaa6-e3e1-4d73-91ee-41197059ca9a /               ext4     errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=480d4318-fd0a-44ae-9d5e-4a9dc715e33e none            swap    sw               0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0        0
# DazukoFS ...
# Example of mounting one dir onto dazukofs (directory to be protected  by AVIRA Guard)
#/home/shared /home/shared dazukofs
/home    /home    dazukofs
# ... DazukoFS

sudo blkid output:

/dev/sda1: LABEL="System" UUID="01C4BC7CA8C0F100" TYPE="ntfs" 
/dev/sda5: LABEL="Audio" UUID="01C4BC86F52FB300" TYPE="ntfs" 
/dev/sda6: LABEL="Dowloads" UUID="01C4BC7FB54B5CA0" TYPE="ntfs" 
/dev/sda7: LABEL="Backup" UUID="01C4BC75CC8CEDC0" TYPE="ntfs" 
/dev/sdb1: UUID="7ecaaaa6-e3e1-4d73-91ee-41197059ca9a" TYPE="ext4" 
/dev/sdb5: UUID="480d4318-fd0a-44ae-9d5e-4a9dc715e33e" TYPE="swap" 
/dev/sdc1: UUID="BC084EE3084E9C70" TYPE="ntfs" 

Any feedback appreciated!

---

### Post by oldfred on 2010-05-11
You do not have a separate /home but the issue is mounting your shared into home on start-up. 

this is not a way to mount in fstab:
/home    /home    dazukofs

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

This is my entry for a shared NTFS partition:
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

Of course you have to use your UUID and have created the correct mount point first.

Always test your changes to fstab with this. If it just returns it is ok or else it will give errror messages:

```
sudo mount -a
```

---

### Post by dowtish on 2010-05-11
I've got Ubuntu 10.4 & Windows XP installed on separate hard disks... when booting the grub gives me the option to boot into:

Ubuntu Linux 2.6.32.22
Ubuntu Linux 2.6.32.22 recovery
Ubuntu Linux 2.6.32.21
Ubuntu Linux 2.6.32.21 recovery
memory test
memory test
Windows XP

It's only when I boot into Ubuntu Linux 2.6.32.22 that I get the error message!

If I boot into Ubuntu Linux 2.6.32.21 the problem doesn't appear!
   
I don't understand what Dazukofs is .... when I installed Avira Antivirus it was automatically set up!

I think my knowledge is too basic to be able to change anything!

Cheers anyway!

---

### Post by oldfred on 2010-05-11
I do not know what Avira Antivirus did. Perhaps it modified the rest of the system so it works with -21 but then the update to -22 was not modified.

If you put a # at the front it becomes a comment and is not used.

gksudo gedit /etc/fstab

Just to check that there are no typos

sudo mount -a

if it just comes back to terminal it is ok, or it will give errors.

---

### Post by Shobuz99 on 2010-05-12
> **oldfred said:**
> You do not have a separate /home but the issue is mounting your shared into home on start-up. 

this is not a way to mount in fstab:
/home    /home    dazukofs

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

This is my entry for a shared NTFS partition:
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

Of course you have to use your UUID and have created the correct mount point first.

Always test your changes to fstab with this. If it just returns it is ok or else it will give errror messages:

```
sudo mount -a
```

hi oldfred,

My problem is similar. I apologize for jumping in on this thread, but I got lost trying to understand your solution for 'dowtish'

I get the same error that 'dowtish' gets except it is 

"an error occurred while mounting /media/floppy0

Press S to cancel or M to mount manually"

I ran 'sudo blkid' and got the following:

/dev/sda1: UUID="60200DA2200D7FF0" TYPE="ntfs" 
/dev/sdb1: UUID="8bb89afd-e18e-4e91-8a66-2394af41fb39" TYPE="ext3" 
/dev/sdb5: UUID="2c971fda-b03b-46a2-8df4-5fbdcdad5b68" TYPE="swap" 
/dev/sdc: UUID="189C-D46B" TYPE="vfat" 
/dev/sdd1: UUID="DC2098942098776C" TYPE="ntfs" 

I also ran  "sudo mount -a"
and got the following:

mount: unknown filesystem type 'utf8'

What do I need to change and where do I change it?

Thank you for your help with this.

Shobuz99

---

### Post by oldfred on 2010-05-12
Shobuz99 need to see fstab, but normally floppies are not permanently mounted as part of fstab. There have been some errors I thought with grub and floppies but maybe it is in startup. One user did turn off the floppy in BIOS and got it to boot but that is not a permanent solution if you use the floppy. If you do not have a floppy that may be the problem also.

---

### Post by Shobuz99 on 2010-05-12
> **oldfred said:**
> Shobuz99 need to see fstab, but normally floppies are not permanently mounted as part of fstab. There have been some errors I thought with grub and floppies but maybe it is in startup. One user did turn off the floppy in BIOS and got it to boot but that is not a permanent solution if you use the floppy. If you do not have a floppy that may be the problem also.

Ok. I do have a floppy...and once I select "S" to cancel, the process continues and then the floppy drive light comes on. 
This means to me that Ubuntu eventually 'picks' the floppy and verifies it is there. 
What I don't understand is how to get that to work prior.

I will relook at my GRUB and see; but I'm not sure that enabling or checking for floppy drives is part of GRUB. 
If it is in "Startup", what file and location would that be? What would I change there?
Also, what about the error when I run "sudo mount -a":
"mount: unknown filesystem type 'utf8'"

What should I do about that? I have no idea.

Thanks again for your help. I appreciate it.

Shobuz99

---

### Post by dowtish on 2010-05-12
Uninstalled & Reinstalled Avira problem solved! :)
 
fstab file:
 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdb1 during installation
UUID=7ecaaaa6-e3e1-4d73-91ee-41197059ca9a / ext4 errors=remount-ro 0 1
# swap was on /dev/sdb5 during installation
UUID=480d4318-fd0a-44ae-9d5e-4a9dc715e33e none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
# DazukoFS ...
# Example of mounting one dir onto dazukofs (directory to be protected by AVIRA Guard)
#/home/shared /home/shared dazukofs
/home /home dazukofs
# ... DazukoFS
 
sudo blkid output:
 
/dev/sda1: LABEL="System" UUID="01C4BC7CA8C0F100" TYPE="ntfs" 
/dev/sda5: LABEL="Audio" UUID="01C4BC86F52FB300" TYPE="ntfs" 
/dev/sda6: LABEL="Dowloads" UUID="01C4BC7FB54B5CA0" TYPE="ntfs" 
/dev/sda7: LABEL="Backup" UUID="01C4BC75CC8CEDC0" TYPE="ntfs" 
/dev/sdb1: UUID="7ecaaaa6-e3e1-4d73-91ee-41197059ca9a" TYPE="ext4" 
/dev/sdb5: UUID="480d4318-fd0a-44ae-9d5e-4a9dc715e33e" TYPE="swap" 
/dev/sdc1: UUID="BC084EE3084E9C70" TYPE="ntfs"
 
sudo mount -a:
 
No problems! :)

---

### Post by Shobuz99 on 2010-05-12
Well.. I fixed it, by experimentation.
Here's how: I edited etc/fstab at the line for the floppy:

it was:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
**/dev/fd0     /media/floppy0  auto,rw,user,noauto,exec 0       0**

Which would fail and cause the mounting error...

and I changed it to the line in an older backup of fstab:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
**/dev/fd0 /media/floppy0  auto,umsdos,vfat,ext2 rw,user,noauto,exec,utf8 0       0**

This eliminates the error and Ubuntu then 'picks' the floppy drive
when it's finished loading.

I don't know if anyone can use this, but feel free to.

Do you see any future problems for me, by doing this?

Thanks for all your help and steering me in the right direction
This is solved, for me.

Shobuz99

---

### Post by dowtish on 2010-05-12
I love Ubuntu but it is a bit like an episode of Lost!
 
What the hell :twisted: is going on here????
 
Regards
 
Dowtish The Thick Windows User!

---

