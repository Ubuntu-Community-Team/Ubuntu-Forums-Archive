---
title: "/etc/fstab line is bad"
date: 2010-04-16
forum: General Help
---

### Post by toyoracer on 2010-04-16
Good day. Running Karmic. I have been trying to auto-mount a new partition in /etc/fstab have been following these posts

[http://ubuntuforums.org/showpost.php?p=9072693&postcount=17](http://ubuntuforums.org/showpost.php?p=9072693&postcount=17)

 [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

This is what I have so far;

craig@craig-desktop:~$ sudo cp /etc/fstab /etc/fstab.bak01
craig@craig-desktop:~$ sudo blkid
/dev/sda1: UUID="0CC88198C88180A6" TYPE="ntfs" 
/dev/sdb1: UUID="5b6dbdda-f40c-414e-8bc8-ae103dd901aa" TYPE="ext4" 
/dev/sdb3: LABEL="/home*" UUID="0517fe33-f8d8-4a4f-bad5-2cb2eab502f2" TYPE="ext4" 
/dev/sdb4: LABEL="PicTunes" UUID="86e8b026-f84c-47a7-9bab-0f77c66940b3" TYPE="ext4" 
/dev/sdb5: UUID="52ad0587-c741-42d3-96a0-c8b8d34e0584" TYPE="swap" 
craig@craig-desktop:~$ gksu gedit /etc/fstab
craig@craig-desktop:~$ sudo mount -a
[mntent]: line 17 in /etc/fstab is bad
craig@craig-desktop:~$ gksu gedit /etc/fstab
craig@craig-desktop:~$ sudo mount -a
[mntent]: line 17 in /etc/fstab is bad
craig@craig-desktop:~$ 


craig@craig-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=5b6dbdda-f40c-414e-8bc8-ae103dd901aa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=52ad0587-c741-42d3-96a0-c8b8d34e0584 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 /media/WindowsXP ntfs-3g users,defaults 0 0
/dev/sdb3 /home ext4 users,defaults 0 0
craig@craig-desktop:~$ 

Help please, maybe typo I am not sure.

---

### Post by toyoracer on 2010-04-17
Any ideas on what is wrong in the line 

/dev/sdb4: LABEL="PicTunes" UUID="86e8b026-f84c-47a7-9bab-0f77c66940b3" TYPE="ext4" 

sudo mount -a

says line bad?

---

### Post by perham on 2010-04-17
> **toyoracer said:**
> Any ideas on what is wrong in the line 

/dev/sdb4: LABEL="PicTunes" UUID="86e8b026-f84c-47a7-9bab-0f77c66940b3" TYPE="ext4" 

sudo mount -a

says line bad?

in fstab? well, it's bad because it's not in the fstab format.

it should be something like this:

```
/dev/sdb4   /media/[your desired mount point] ext4 defaults 0 0

```

OR

```
UUID=86e8b026-f84c-47a7-9bab-0f77c66940b3   /media/[your desired mount point] ext4 defaults 0 0

```

---

### Post by toyoracer on 2010-04-17
> **perham said:**
> in fstab? well, it's bad because it's not in the fstab format.

it should be something like this:

```
/dev/sdb4   /media/[your desired mount point] ext4 defaults 0 0

```OR

```
UUID=86e8b026-f84c-47a7-9bab-0f77c66940b3   /media/[your desired mount point] ext4 defaults 0 0

```

So I combined them?

Okay changed to  /dev/sdb4 /media/PicTunes ext4 defaults 0 0

then sudo mount -a
so that should do it, I looked and could not see.  Thank you

---

### Post by toyoracer on 2010-04-17
That worked.

Questions: /media/...  goes on desktop?
                 permissions ... could not be determined?

I need full access music and picture files.

---

### Post by perham on 2010-04-17
> **toyoracer said:**
> That worked.

Questions: /media/...  goes on desktop?

[COLOR="Red"]yup[/COLOR]


permissions ... could not be determined?

[COLOR="Red"]they can be determined.[/COLOR]

I need full access music and picture files.

[COLOR="Red"]the "defaults" option should give you read write access. is it not?[/COLOR]


my answers in red.

---

### Post by toyoracer on 2010-04-17
Yes everything seems to work thank you    perham

---

### Post by perham on 2010-04-17
> **toyoracer said:**
> Yes everything seems to work thank you    perham

glad I could help. ;)

---

