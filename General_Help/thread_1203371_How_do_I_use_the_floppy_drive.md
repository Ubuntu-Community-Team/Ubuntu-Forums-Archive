---
title: "How do I use the floppy drive?"
date: 2009-07-03
forum: General Help
---

### Post by Lingonet on 2009-07-03
Hello, Ubuntuforumers!

I have a little problem:

I just installed a floppy drive on my Ubuntu computer. I enabled it in BIOS and started up Ubuntu. Unfortunately nothing was any different when it started up. No new directories, nothing. So I searched a little bit on the web and found this guide: [http://www.alwanza.com/howto/linux/floppy.html](http://www.alwanza.com/howto/linux/floppy.html) which explained the problem I had. Unforunately again, this couldn't help me. I have tried to mount the drive but then the terminal says: "Mount point does not exist". When I look in my fstab it looks like this:

```
# /etc/fstab: static file system information.
#
# The following is an example. Please see fstab(5) for further details.
# Please refer to mount(1) for a complete description of mount options.
#
# Format:
#  <file system>         <mount point>   <type>  <options>	<dump>	<pass>
#
# dump(8) uses the <dump> field to determine which file systems need
# to be dumped. fsck(8) uses the <pass> column to determine which file
# systems need to be checked--the root file system should have a 1 in
# this field, other file systems a 2, and any file systems that should
# not be checked (such as MS-DOS or NFS file systems) a 0.
#
# The `sw' option indicates that the swap partition is to be activated
# with `swapon -a'.
/dev/hda2	none		swap	sw				0 0

# The `bsdgroups' option indicates that the file system is to be mounted
# with BSD semantics (files inherit the group ownership of the directory
# in which they live). `ro' can be used to mount a file system read-only.
/dev/hda3	/		ext2	defaults			0 1
/dev/hda5	/home		ext2	defaults			0 2
/dev/hda6	/var		ext2	defaults			0 2
/dev/hda7	/usr		ext2	defaults,ro			0 2
/dev/hda8	/usr/local	ext2	defaults,bsdgroups		0 2

# The `noauto' option indicates that the file system should not be mounted
# with `mount -a'. `user' indicates that normal users are allowed to mount
# the file system.
/dev/cdrom	/cdrom		iso9660	defaults,noauto,ro,user		0 0
/dev/fd0	/floppy		minix	defaults,noauto,user		0 0
/dev/fd1	/floppy		minix	defaults,noauto,user		0 0

# NFS file systems:
server:/export/usr	/usr	nfs	defaults			0 0

# proc file system:
proc		/proc		proc	defaults			0 0

```

On the /dev/fd0 and fd1 directory, it doesn't say mnt/floppy like the guide says, it says only /floppy. It doesn't say "auto" either but "minix".

It would be great if someone with some Linux experience could help me with this, cause I really need my floppy drive to work!

Thank you in advance!

-Lingonet

---

### Post by Inventech on 2009-07-03
[LIST]
[*]Make sure that you installed the floppy drive correctly
[*]If you are dual-booting on this PC, see if the other OS detects the floppy drive, in order to confirm that it is properly installed.
[/LIST]

---

### Post by Lingonet on 2009-07-03
> **Inventech said:**
> [LIST]
[*]Make sure that you installed the floppy drive correctly
[*]If you are dual-booting on this PC, see if the other OS detects the floppy drive, in order to confirm that it is properly installed.
[/LIST]

It is correctly installed, the green light was flashing just when I started the computer.

I'm not dual-booting another operating system so I can't do that.

Can't I just change the directory from ```
/floppy
``` to ```
mnt/floppy
```?

Thanks for your reply?

-Lingonet

---

### Post by muteXe on 2009-07-03
Did you actually create a folder called "mnt" before doing any of that web page?

Forget your fstab for the moment.  Let's just see if you can do a "one-off" mount.  If your floppy drive is at /dev/fd0 then create a folder called eg "floppy" in your root. then try:
```

sudo mount /dev/fdo /floppy

```
if that dont work try:
```

sudo mount /dev/fdo /floppy -t vfat

```

---

### Post by drdob on 2009-07-03
):P I had the same problem and it was solved like this:  

To load the driver in a terminal
Code:

sudo modprobe floppy


And to load it for every re-boot
Code:

gksudo gedit /etc/modules

and add the word floppy on a newline.

If you are not confident editing system files,make a backup copy first
Code:

sudo cp /etc/modules /etc/modules.backup   

it came from this forum not me, but it works!!!     ;) Dr Dob

---

### Post by Lingonet on 2009-07-03
> **drdob said:**
> ):P I had the same problem and it was solved like this:  

To load the driver in a terminal
Code:

sudo modprobe floppy


And to load it for every re-boot
Code:

gksudo gedit /etc/modules

and add the word floppy on a newline.

If you are not confident editing system files,make a backup copy first
Code:

sudo cp /etc/modules /etc/modules.backup   

it came from this forum not me, but it works!!!     ;) Dr Dob

Thank you so much! This worked awesome!

But what do you mean with adding the word floppy on a new line? Like this:

gksudo gedit /etc/modules
floppy

?

Thanks!

-Lingonet

---

### Post by rbc on 2009-07-03
gedit is like notepad or wordpad in Windows, just a word processor. "gksu" opens that file as superuser (it's sudo for GUI stuff) I'm sure someone else can explain that better than I. Once gedit opens the /etc/modules file, add the word floppy under whatever the last entry is. Save, then close.

---

