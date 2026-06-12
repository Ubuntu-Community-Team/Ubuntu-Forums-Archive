---
title: "unknown filesystem type 'LVM2_member'"
date: 2010-10-02
forum: General Help
---

### Post by jim h on 2010-10-02
(Using 9.10) The cure I found in searching is to install LVM2, but apt-get says lvm2 is already the newest version.  I've never had a problem mounting this partition before, I wonder if a recent update caused a problem???  I just say (as root) mount /dev/sdb2 /F11 as usual, but I now get that message.  Thanks for any suggestions.

---

### Post by srs5694 on 2010-10-02
It sounds like you may have accidentally overwritten the filesystem on /dev/sdb2 with LVM data structures by an inappropriate use of pvcreate.

Please post more details, in particular, the output of "ls /dev/mapper", "sudo fdisk -lu", and "sudo blkid /dev/sdb2". Post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

### Post by jim h on 2010-10-02
Thanks for your response.  I don't know what additional information I can supply except that I have not intentionally used any LVM commands whatsoever on this system - sdb was an F11 system I used until I loaded Ubuntu onto a new (sda) drive.  As I indicated, it's been fine up till now and I'm mystified.

In case it provides anything useful I am also attaching the output of the pvdisplay, vgdisplay, and lvdisplay commands.

Here is the result from the commands you listed, which I ran from a root window:

```

~> ls /dev/mapper
control  VolGroup-lv_root  VolGroup-lv_swap

```


```

~> fdisk -lu

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00056e5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63      409662      204800   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2          409663   625137344   312363841   8e  Linux LVM

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3fda7fe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     1959929      979933+  83  Linux
/dev/sda2         1959930     9767519     3903795   82  Linux swap / Solaris
/dev/sda3         9767520  1465144064   727688272+   5  Extended
/dev/sda5         9767583   791024534   390628476   83  Linux
/dev/sda6       791024598  1465144064   337059733+  83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b0474

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   152521109    76260523+  83  Linux
/dev/sdc2       152521110   156296384     1887637+   5  Extended
/dev/sdc5       152521173   156296384     1887606   82  Linux swap / Solaris

```
 
 
```

~> blkid /dev/sdb2
/dev/sdb2: UUID="hGMFJ9-MoXK-8ASe-OKKr-1Uf6-8E4B-pPpU4m" TYPE="LVM2_member" 

```

---

### Post by srs5694 on 2010-10-03
Fedora makes it easy to set up an LVM system, and in fact I think that's the default with recent versions. Your /dev/mapper output also shows two logical volumes: VolGroup-lv_root and VolGroup-lv_swap. Thus, it appears that you've got a Fedora 11 installation in an LVM. If you've accessed this from Ubuntu before, chances are either it was configured in /etc/fstab or the GNOME automounter was detecting it, but that something (a reinstallation?) has altered this configuration.

Personally, I'd edit /etc/fstab and add something like this:

```

/dev/VolGroup/lv_root  /other/fedora  ext3  defaults       0 0

```

Change the mount point (/other/fedora) to whatever is convenient for you, and change the filesystem type code (ext3) to whatever is indicated by "sudo blkid /dev/VolGroup/lv_root". Create the mount point, then type "sudo mount -a". Your old Fedora system should now be mounted. If you want to access it only occasionally, change "defaults" to "noauto,users" and you'll be able to mount it as an ordinary user, but it won't be mounted all the time.

---

### Post by jim h on 2010-10-03
Don't know what was wrong, but that fixed it.  Thanks !!!!!

---

