---
title: "No files executable from disks execpt from /home partition"
date: 2010-11-28
forum: General Help
---

### Post by cthlhu1987 on 2010-11-28
Since my upgrade to Ubuntu 10.10 (actually it is a clean new install since the upgrade process snet the network-manager FUBAR) I got the following problem: Ubuntu refuses to execute any script or binary programm file from usb drives or any drive (even the ntfs partitions from my harddrive). Scripts execute only if I explicitly use the resp. shell command (bash, sh etc., e.g. bash foo.script), not if i try to start them the "normal" way  (./foo.script), binary executables donÄt execute at all. Do you know how to solve this problem? How to get the system to execute scripts/binary executables like it was in the good ol times before 10.10?

Thx in advance.

---

### Post by mc4man on 2010-11-29
Assuming you don't wish to use or move files to  a fs that accepts permissions...
As far as scripts, don't see that typing a few extra letters is that big a deal.
If the binaries are .exe's and or .jar's then you don't need to set the bit, just bypass the new security policy (cautious-launcher), easily done 

If the binaries are linux executables then to 'solve' it's most likely an all or nothing for vfat and ntfs, ie. all files will be 'marked' as x. - resolves the script deal also
(this probably qualifies "as the good ol times before 10.10"? 

To do that there are 2 ways ('solves' the script deal also - 

create fstab entries for all affected partitions/drives ect., with mount options that allow
(you'd most likely want to use UUID= or Label=, or possibly better 
/dev/disk/by-uuid/xx or /dev/disk/by-label/xx 
where xx is either the UUID or LABEL

Or rebuild udisks with a couple of small edits to /src/device.c
Thread with various info inc. udisk edits
[http://art.ubuntuforums.org/showthread.php?t=1606193](http://art.ubuntuforums.org/showthread.php?t=1606193)

---

