---
title: "Find attached USB with their Device names?"
date: 2010-03-01
forum: General Help
---

### Post by ma1 on 2010-03-01
[FONT=Courier New]**Is there any way to find the attached USB devices with their device name(s).**

For Example; Suppose a usb is attached to system...i want to know what is its device name(/dev/sdb /dev/sdc etc).

I tried lot of commands but didn't find the right information. 

For Example:

**lsusb **just tells the devices attached to usb ports but no device name?

sample lsusb output 

$lsusb

```
Bus 001 Device 007: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 001 Device 006: ID 0951:1624 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 1b1a:0000  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```also tried the following 

$ cd /sys/block/[/FONT][FONT=Courier New]
$ grep ^ */removable

[/FONT]```
dm-0/removable:0
dm-1/removable:0
dm-2/removable:0
dm-3/removable:0
dm-4/removable:0
dm-5/removable:0
dm-6/removable:0
dm-7/removable:0
dm-8/removable:0
fd0/removable:1
hdc/removable:1
loop0/removable:0
loop1/removable:0
loop2/removable:0
loop3/removable:0
loop4/removable:0
loop5/removable:0
loop6/removable:0
loop7/removable:0
md0/removable:0
md1/removable:0
sda/removable:0
sdb/removable:0
sdc/removable:1

```[FONT=Courier New]

but this will not recognize portable USB Hard Drive as removable. In the above output
/dev/sdb is portable usb hard disk but here it is shown as non removable

**So, Can anyone help me?**

Regards,
[/FONT]

---

### Post by dragonboss on 2010-03-01
Try the device manager or the storage device manger from the software center

---

### Post by ma1 on 2010-03-01
> **dragonboss said:**
> Try the device manager or the storage device manger from the software center

but i need something that i can use from terminal.

---

### Post by dragonboss on 2010-03-02
The closest thing I've found is running sudo lshw -businfo in the terminal.

---

### Post by d3v1150m471c on 2010-03-02
```

cd /media
ls

```

or

```

df -h

```

---

### Post by QLee on 2010-03-02
> **ma1 said:**
> but i need something that i can use from terminal.

You might want to try the command blkid it will list the device node, UUID, LABEL and type for the partitions on your system.

Looking back over your question, I think what you want is to look in the messages log file, it shows where the system attached a removable drive in case you haven't labeled your drives, which makes it somewhat easier.

---

### Post by timZZ on 2010-03-02
To find mounted file systems.
```
mount
```

or

For usb only.
```
lsusb
```

---

### Post by dragonboss on 2010-03-04
The solution is this:

```
sudo blkid
```

---

### Post by dkavraal on 2010-11-25
Later followers might try this: (as **dragonboss** suggests)

> DEVUID="0000000000000000000"

DEVADR=`blkid /dev/sd*  | grep ${DEVUID} | cut -d' ' -f1 | cut -d":" -f1`
DEVPATH_LNFORMAT=`cat /etc/mtab | grep ${DEVADR} | cut -d' ' -f2`
DEVPATH=`printf "${DEVPATH_LNFORMAT}"


In here DEVUID is the id of your device, you can once find it in:
# sudo blkid
UUID=".... here ..."


cheers

---

### Post by sgosnell on 2010-11-25
"sudo blkid" or "df" should give you what you want.  Slightly different formats, but essentially the same information.

---

### Post by joepie91 on 2010-11-25
"fdisk -l" should also give the output you (are anyone else) is looking for.

EDIT: Wait, I'm not sure if this is also the case in *ubuntu.

---

### Post by sgosnell on 2010-11-26
Yes, fdisk is another way to get the device list.  You have to use sudo with it, though.

---

