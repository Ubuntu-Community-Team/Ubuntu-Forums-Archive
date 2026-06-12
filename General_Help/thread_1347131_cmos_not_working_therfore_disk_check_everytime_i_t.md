---
title: "cmos not working therfore disk check everytime i turn on"
date: 2009-12-05
forum: General Help
---

### Post by babu38 on 2009-12-05
my old system has a bad cmos beyond repairable ... my problem is every time i restart my system its date becomes changed & old date and manual disk check is being requested every time using fsck and then control + D ... what to do????

---

### Post by mdurham on 2009-12-05
> **babu38 said:**
> my old system has a bad cmos beyond repairable ... my problem is every time i restart my system its date becomes changed & old date and manual disk check is being requested every time using fsck and then control + D ... what to do????
what does you /etc/fstab look like?

---

### Post by paradigm2 on 2009-12-05
I believe there is a way to disable the check based on date and just use the number of boots.  However I'd have to look for it.  Better though would be to fix the CMOS issue.  Are you sure you just don't have a bad battery that needs to be replaced?  I just bought 3 new batteries for my CMOS from Dollar Tree.  $1 for a pack of three.

---

### Post by babu38 on 2009-12-08
> **paradigm2 said:**
> I believe there is a way to disable the check based on date and just use the number of boots.  However I'd have to look for it.  Better though would be to fix the CMOS issue.  Are you sure you just don't have a bad battery that needs to be replaced?  I just bought 3 new batteries for my CMOS from Dollar Tree.  $1 for a pack of three.

No. The CMOS has internal error. So it cant be repaired by changing the battery.

---

### Post by earthpigg on 2009-12-08
> **babu38 said:**
> No. The CMOS has internal error. So it cant be repaired by changing the battery.

sooo, what does your /etc/fstab look like?

```
cat /etc/fstab
```

please make sure to put it in 'code' tags.

```
[ CODE ] bla bla [ /CODE ] 
```

except no space in the middle. [CDOE] and [/CDOE], except spelled correctly.

---

### Post by lisati on 2009-12-08
> **earthpigg said:**
> sooo, what does your /etc/fstab look like?

```
cat /etc/fstab
```

please make sure to put it in 'code' tags.

```
[ CODE ] bla bla [ /CODE ] 
```

except no space in the middle. [CDOE] and [/CDOE], except spelled correctly.

e.g. [noparse]```
 and 
```[/noparse]
The [IMG]http://ubuntuforums.org/images/editor/quote.gif[/IMG] button will also wrap code tags around the selected text.

---

### Post by babu38 on 2009-12-09
> **lisati said:**
> e.g. [noparse]```
 and 
```[/noparse]
The [IMG]http://ubuntuforums.org/images/editor/quote.gif[/IMG] button will also wrap code tags around the selected text.


my fstab is as shown below

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=12b0b356-c8f2-4c45-9419-c86799012305 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=13a26e0d-0eaf-46ea-92c8-b9dabfa1e5fa none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=924f740e-50e1-4ec1-a264-97679fbdfcbe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

---

### Post by mdurham on 2009-12-09
You can change the rightmost '1' in the first active line to '0'

from man fstab:
> The sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time.  The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2.  Filesystems within a drive will be checked  sequentially,  but  filesystems  on different  drives  will  be checked at the same time to utilize parallelism available in the hardware.  **If the sixth field is not present or zero, a value of zero is returned and fsck will assume that the filesystem  does not need to be checked**.


---

### Post by babu38 on 2009-12-10
> **mdurham said:**
> You can change the rightmost '1' in the first active line to '0'

from man fstab:

thank u a lot ///,,,

---

