---
title: "My files!"
date: 2010-01-20
forum: General Help
---

### Post by linuxdualbooter on 2010-01-20
Right after 9.10 came out, my 9.04 partition crashed and locked me out. I was forced to install a new version of 9.10 but I still have some family photos stuck in the old partition. I can still access the partition, however, when I try to open the profile it will not let me, blocking me from accessing those photos. Is there any solution?

---

### Post by hemimaniac on 2010-01-20
I have had luck in the past using nautilus as root from a live cd.

boot to a live cd go into terminal and do "sudo nautilus"

then you will be able to browse around as root, worth a try?

---

### Post by linuxdualbooter on 2010-02-05
That worked, but it still wont let me see my pictures and files. In fact, the only things that I can see are the folders. If I click on any file, it says :"An error occurred while loading the archive.

(null)
"
And then:"[/media/disk/usr/lib/f-spot/f-spot.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/disk/usr/lib/f-spot/f-spot.exe or
          /media/disk/usr/lib/f-spot/f-spot.exe.zip, and cannot find /media/disk/usr/lib/f-spot/f-spot.exe.ZIP, period.
"
No program really matters, it is just my pictures and documents I want to save, and those are stored on the user account, which is inaccessible.
Plus :"This problem report is damaged and cannot be processed."

---

### Post by linuxdualbooter on 2010-02-23
Is there anyway to open these files?

---

### Post by louieb on 2010-02-23
Try using Gparted. - right click on the partition with problems and select the check option. - this will run fsck on the partition and may fix  any problem it might have. If its mounted you will have unmount it 1st - you can do that from the right click menu too.

Then mount it and see if you can now browse its contents.

---

