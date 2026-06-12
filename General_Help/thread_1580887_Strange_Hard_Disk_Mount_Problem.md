---
title: "Strange Hard Disk Mount Problem"
date: 2010-09-24
forum: General Help
---

### Post by benharvey1985 on 2010-09-24
I have recently added another external USB hard drive to my HTPC running Ubuntu 9.10. all my drives mount fine on startup, but one drive after a few hours seems to unmount itself and throws the following error:

```

Unable To Mount Elements

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /media/Elements
mount failed

```and if i try and click the link to the drive on the desktop it throws this error:

```

Could not open location 'file:///media/Elements'

Error stating file '/media/Elements': Input/output error

```im at my wits end trying to find a solution and was wondering if any of the Ubuntu Gurus on the forums could help.

here is a copy of my fstab if it helps:

```

UUID=FE64540F6453C8D3  /media/Elements  ntfs-3g  defaults  0  0  

UUID=2A8CF7B48CF77921  /media/Maxtor    ntfs-3g  defaults  0  0  

UUID=D27431CF7431B6D7  /media/Iomega    ntfs-3g  defaults  0  0  

```Am i being really stupid and missing something?

Thanks in advance for any help, and for taking the time to read my post at least!

---

### Post by dcstar on 2010-09-24
> **benharvey1985 said:**
> 
............
here is a copy of my fstab if it helps:

```

UUID=FE64540F6453C8D3  **/media/**Elements  ntfs-3g  defaults  0  0  

UUID=2A8CF7B48CF77921  **/media**/Maxtor    ntfs-3g  defaults  0  0  

UUID=D27431CF7431B6D7  **/media/**Iomega    ntfs-3g  defaults  0  0  

```Am i being really stupid and missing something?

Thanks in advance for any help, and for taking the time to read my post at least!

/media is a **system** folder that is used for Removable drives and for the system to control their mounting and unmounting, you should not have any /media entries in your fstab file.

Mount these drives somewhere else - and not in **any** system folders.

---

### Post by benharvey1985 on 2010-09-24
have changed them to mount in the /mnt folder, i hope this is now correct. My fstab now looks like:

```

UUID=FE64540F6453C8D3  /mnt/Elements  ntfs-3g  defaults  0  0  

UUID=2A8CF7B48CF77921  /mnt/Maxtor    ntfs-3g  defaults  0  0  

UUID=D27431CF7431B6D7  /mnt/Iomega    ntfs-3g  defaults  0  0

```

i hope this works better. Thanks again for your time

---

