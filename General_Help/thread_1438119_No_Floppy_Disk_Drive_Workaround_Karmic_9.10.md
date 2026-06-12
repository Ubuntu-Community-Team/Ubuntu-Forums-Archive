---
title: "No Floppy Disk Drive Workaround Karmic 9.10"
date: 2010-03-24
forum: General Help
---

### Post by RT236 on 2010-03-24
OS Karmic 9.10

**Note:**  The below example assumes you already have your floppy disk drive defined in fstab located in etc/fstab

The line in your fstab file would be:

/dev/fd0  /media/floppy0  auto    rw,user,noauto,exec,utf8 0   0

Since a recent update approx. today, 03/24/2010, I have had to start using  <devkit-disks --mount /dev/fd0>  to mount a floppy disk rather than  <mount /media/floppy> 

Once mounted, a floppy disk icon should appear on your desktop.  Clicking on the icon will popup a screen with the contents in </media/floppy0>  You should be able to drag/drop files without being root.

When finished, a right mouse click on the same floppy disk icon on your desktop should allow you to do an umount.

A desktop launcher can be created if desired, the command is:  devkit-disks --mount /dev/fd0

This is necessary for convenience, because "Floppy Drive" under "Places" does not open the floppy disk drive.

This has already been filed as a bug sometime ago.  Some of us for a multitude of reasons must still use floppy disks.  Bug ID: 441835 on Launchpad.

**NOTE:  FYI if formatting a 1.44mb floppy.**  mformat is the only formatting app I have found that is currently working OK.  With the floppy drive unmounted and if your floppy is defined, for example, as a: in your system, you should be able to format a floppy disk by <mformat -f 1440 a:>  If more details are wanted do <man mformat> in a terminal window (without the <>, of course.)

If mformat is not already on your system, it can be installed from Synaptic Package Manager.

To make it handy, a desktop launcher can be created with the command being mformat -f 1440 a:

---

### Post by mhampson on 2010-03-26
I'm not sure what this thread is for: it's called "No Floppy Disk Drive Workaround" and then it seems to describe a workaround.

I've solved all Floppy Disk problems with this simple one-liner that people might like to try instead:

sudo nautilus

---

### Post by coffeecat on 2010-03-26
> **mhampson said:**
> I'm not sure what this thread is for: it's called "No Floppy Disk Drive Workaround" and then it seems to describe a workaround.

It's a punctuation blooper. :) The thread title, as it stands, is ambiguous.

> **RT236 said:**
> No Floppy Disk Drive Workaround Karmic 9.10

Does the 'no' refer to 'floppy disc drive' or to 'workaround'? I guess the OP meant for it to refer to 'floppy disc drive', in which case the title should have been:

> No Floppy Disk Drive - Workaround Karmic 9.10

---

### Post by RT236 on 2010-03-26
> **coffeecat said:**
> It's a punctuation blooper. :) The thread title, as it stands, is ambiguous.



Does the 'no' refer to 'floppy disc drive' or to 'workaround'? I guess the OP meant for it to refer to 'floppy disc drive', in which case the title should have been:

Thanks, yep, a real punctuation blooper and ambiguous. I just fixed it (I think).  Thanks again.

---

### Post by RT236 on 2010-03-26
> **mhampson said:**
> I'm not sure what this thread is for: it's called "No Floppy Disk Drive Workaround" and then it seems to describe a workaround.

I've solved all Floppy Disk problems with this simple one-liner that people might like to try instead:

sudo nautilus

Yep, it was poorly written by me.  Too late at night.  I just rewrote what I had said...  If you use the command I gave it should work for you and does not require using nautilus as root.  There is already a bug for this opened under bug ID: 441835 on Launchpad.

---

