---
title: "Removable drive problem."
date: 2006-04-01
forum: General Help
---

### Post by elder68 on 2006-04-01
When I was using Kubuntu 5.04 it would recognize my Jumpdrive without any problem as it booted. I used it all the time to move files back and forth between another Windows machine and Kubuntu. In kubuntu 5.10 it shows the drive is present, on the screen, after it has booted but when I try to use it I am told that it does not know what the file system is and so can't mount it.

The same problem applies with my digital camera. I usually download the images by inserting the card into a removeable USB drive (Microdia Flash Mover.) Again Kubuntu 5.04 recognized it right away and I was able to downloa images. Now I get the same result as above with the Jumpdrive with K. 5.10.

Hmmm, should have stayed with 5.04!! Any help with the above would be really appreciated.

---

### Post by Barrakketh on 2006-04-01
Make sure that there isn't an entry in your fstab for your jumpdrive or CF adaptor (for your digital camera).  They may keep the devices from properly automounting.

---

### Post by elder68 on 2006-04-01
[QUOTE=Barrakketh]Make sure that there isn't an entry in your fstab for your jumpdrive or CF adaptor (for your digital camera).  They may keep the devices from properly automounting.[/QUOTE]

Thank you for the above. Here is my fstab. I am roughly familiar with such things but before I do anything at all, here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

---

### Post by Barrakketh on 2006-04-02
Comment out this line:
```
/dev/sda /media/usb0 auto rw,user,noauto 0 0
```

---

### Post by wcks48 on 2006-04-02
i'm not sure bout this, but after i first time mounted and accessed to my pendrive and took it out, now, everytime i need access it by kubuntu, after i put it on the usb port, i check from the /media/ directly. then i could save and load files from it. but of course, must i got extra 2 page which saying can't mount to the drive via Konqueror. 

is this msg helps? anyway, i hope so.

---

### Post by elder68 on 2006-04-02
[QUOTE=Barrakketh]Comment out this line:
```
/dev/sda /media/usb0 auto rw,user,noauto 0 0
```[/QUOTE]

Thank  you for the above. Quoting out the line stopped everything and nothing worked concerning the Jumpdrive.  The drive seems to be mounted OK but is looking for a "filesystem" .

---

### Post by elder68 on 2006-04-02
[QUOTE=elder68]Thank  you for the above. Quoting out the line stopped everything and nothing worked concerning the Jumpdrive.  The drive seems to be mounted OK but is looking for a "filesystem" .[/QUOTE]

Things are starting to work but in a rather convoluted way. Your suggestion about commenting out that line in /etc/fstab is what eventually led to the solution for me. 

Reading some of the posts I learned about "automount" so I pulled the jumpdrive and re-inserted it. Konqueror came up and said that it could not find the directory, "An error occurred while loading media:/sda1:
The file or folder media:/sda1 does not exist." However, however the directory did exist. So I went into the Terminal and hunted up /media/sda1 and there were all my files. Its a bit of a nuisance having to automount all the time but at least it was there.

In a side comment I have found Kubuntu 5.10 more of a problem the 5.04. None of this was a problem with that edition. If 6.0 does not improve things I might be heading back to Suse.

As I prefer a GUI interface I installed Nautilus and it finds the files without any problem.

Thank you for your help.

---

