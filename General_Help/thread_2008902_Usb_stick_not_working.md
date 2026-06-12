---
title: "Usb stick not working"
date: 2012-06-23
forum: General Help
---

### Post by flunkyou2 on 2012-06-23
hello... im trying to get my 4gb usb stick to work, could anyone tell me how? cheers ):P

---

### Post by sudodus on 2012-06-23
Hello,

I should be seen by and possible to mount via your file browser (Nautilus in Ubuntu).

If you supply more information about your system and the USB stick it will be easier to help. When the stick is connected, run the commands
```
sudo fdisk -lu
```
and
```
df
```
and post the output of the commands in a replay.

Furthermore: Can you mount and read and write on the stick using another computer or with Windows?

---

### Post by flunkyou2 on 2012-06-23
thank you for the help.... heres the copy and pastes:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f26bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   154861567    77429760   83  Linux
/dev/sda2       154863614   156301311      718849    5  Extended
/dev/sda5       154863616   156301311      718848   82  Linux swap / Solaris
gray@gray-AMILO-L7310:~$ 


Second:

fdisk: invalid option -- 'd'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

---

### Post by sudodus on 2012-06-23
The output of the first command shows that your usb stick is not recognized as a storage unit.

You must have missed the second command, it is simply the two letter command line ```
df
``` but since [FONT="Courier New"]fdisk[/FONT] didn't find it in the first place, [FONT="Courier New"]df[/FONT] is not giving any info.

Can you mount and read and write on the stick using another computer or with Windows?

Or can you see any information about the stick running the GUI program ***hardinfo***? Look at Storage!

---

### Post by flunkyou2 on 2012-06-23
i have tried it on another pc and its fine.... i think it may be the usb drivers on this laptop as my webcam dont work on here :(  
there is power going through them

---

### Post by sudodus on 2012-06-23
You can boot a live session 'Try Ubuntu ...' booted from a CD drive. If the USB drivers are bad in the installed system, it should work in the live system unless you have very unusual hardware.

---

### Post by flunkyou2 on 2012-06-23
ok i can live without the usb ports.... could you help me find a way to stream movies via wifi to a xbox 360?

---

### Post by sudodus on 2012-06-23
> **flunkyou2 said:**
> ok i can live without the usb ports.... could you help me find a way to stream movies via wifi to a xbox 360?
I'm no expert on streaming movies, so I can't help you with that.

And I suggest that you start a ***new thread with an informative title***  to attract those who can help with that problem.

---

