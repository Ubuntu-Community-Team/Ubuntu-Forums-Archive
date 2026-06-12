---
title: "Quick questions about switching over from Windows"
date: 2012-05-02
forum: General Help
---

### Post by Nihilyst on 2012-05-02
The install went very smooth but I can't access my slave drive. I have win7 and ubuntu installed on the same drive.  The slave drive is used for music and some misc programs in windows.  The drive is recognized in ubuntu, but I get an unable to mount error.  Is there any workaround for this aside from reformatting the drive? Also how do you setup network sharing on ubuntu? All the comps on my network are running some variant of windows but the os does not recognize anything atm. 

Thanks in advance.

---

### Post by gordintoronto on 2012-05-02
"The drive is recognized in ubuntu, but I get an unable to mount error...." When do you get this error? 

What version of Ubuntu?

In Ubuntu 12.04, when I start the file manager, there are "nnn GB Filesystem" entries on the top-left of the Nautilus window. When I click on one of them, I can see the contents of the partition.

Similarly, there's an entry for "browse network." I click on it, and it shows computers which have shared folders. I double-click, and I see the folders. Double-click, and I see the content of a folder.

You might need to install samba for this to work.

---

### Post by Nihilyst on 2012-05-03
I'm using 12.04, the error message I get is as follows

[I]Error mounting: mount exited with exit code 12: Failed to read last sector (781413147): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/I]

I have installed samba but the only config tool I can seem to access is the server tool (apparently the client is bundled into the download but I'm not sure how to access it).

---

### Post by pqwoerituytrueiwoq on 2012-05-03
try repairing/checking it with [gparted](apt:gparted) (right click the partation)

---

