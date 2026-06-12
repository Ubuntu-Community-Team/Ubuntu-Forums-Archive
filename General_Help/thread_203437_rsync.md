---
title: "rsync"
date: 2006-06-25
forum: General Help
---

### Post by cssutto on 2006-06-25
I have been running Ubuntu for about two months without any backup and it is making me nervous.

I have tried several backup packages with no luck, although rsync seems to be the most promising.

However, I have the huge problem that I can not figure out how to name my external Maxtor drive in an rsync command.

Ubuntu named my drives with some weird names which I can not get rsync to recognize.

My df results are:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              9614148   5371588   3754184  59% /
varrun                  387744       100    387644   1% /var/run
varlock                 387744         4    387740   1% /var/lock
udev                    387744       208    387536   1% /dev
devshm                  387744         0    387744   0% /dev/shm
lrm                     387744     18856    368888   5% /lib/modules/2.6.15-25-386/volatile
/dev/hda1             12284968   8899292   3385676  73% /media/hda1
/dev/hda2             23042876   6272216  16770660  28% /media/hda2
/dev/hda6             13473320    618256  12855064   5% /media/hda6
/dev/sdb7             29492180    471204  29020976   2% /media/Local Disk
/dev/sdb1             22410640   6017296  16393344  27% /media/H:
/dev/sdb6             66332352  43238056  23094296  66% /media/Local Disk-1

I can not even cd /media/Local Disk.  That results in the so such directory message.

When I cd /media and ls, I get the following:

/media$ ls
cdrom   floppy0  hda2        Local Disk-1  usbdisk    usbdisk-3
cdrom0  H:       hda6        usb           usbdisk-1  usbdisk-4
floppy  hda1     Local Disk  usb0          usbdisk-2  usbdisk-5

It would appear from all of the above that there is a valid Local Disk and Local Disk-1.

I know that there is because clicking the icon that is on the Desktop when the Maxtor external drive is operating, I get the contents of this partition.

I forgot to mention that Local Disk and Local Disk-1 are partitions on the Maxtor drive.

File Browser will take me to these Maxtor partitions and allow me to look at files as well as open files by whatever means, including wine.

File Browser uses the names Local Disk and Local Disk-1 and they are in the media directory.

So how do I get to Local Disk or Local Disk-1 with the command line?

CSSJR

---

### Post by GarlicFish on 2006-06-25
Have you tried using quotes? e.g.
cd "/media/Local Disk"

or have you tried using tab completion in bash and escape the spaces with \ ? e.g. 
cd /media/Local\ [hit tab] and fill in anything it doesnt automatically find.

if these work, you can use the quotes or escape methods with rsync e.g.

rsync -a /home/blah /media/Local\ Disk/backup

---

### Post by cssutto on 2006-06-25
Thank you for the prompt reply.

I am into something else right now and it might be Tuesday before I get to try all of these suggestions.

I will post the results.

Thanks again.

CSSJR

---

### Post by cssutto on 2006-06-25
[I decided to give the tab suggestion a try and it worked.

Thank you.

CSSJR

---

