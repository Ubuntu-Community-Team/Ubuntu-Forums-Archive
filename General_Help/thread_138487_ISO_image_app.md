---
title: "ISO image app?"
date: 2006-03-02
forum: General Help
---

### Post by pbransford on 2006-03-02
I'm looking for something that will let me make ISO images of CDs, preferably one that would work with (IE the iso would have it and it would work properly) copy protection schemes. Also something that would let me "mount" these, including said copy protection.

Something kind of like "Alcohol 120%" but for linux.

Anyone know if such a thing exists? It's not critical, just saves me from dragging a disk binder with me when I travel.

---

### Post by akiro.yamamoto on 2006-03-02
you can mount an ISO image in linux with these steps:
First :
sudo modprobe loop
Then do:
sudo mkdir /mnt/ISO
sudo mount /<path_to_iso> /mnt/ISO -t iso9660 -o loop
The iso file should now be visible in Nautilus under the /mnt directory.

To CREATE an ISO image (TO YOUR HARD DRIVE) , of a CD (That you already HAVE).
Insert the CD then right click and select Copy Disk.
When the "Write to Disk" dialog comes up. Choose "File Image" instead of your
CD/DVD Burner drive, then say "Write" and select where you want the ISO file to be created. ;)

To BURN a CD from an ISO image that you HAVE on your Hard Drive.
Right Click on the ISO image file and select "Write To Disk" insert a blank CD/DVD and select "Write".
It can take anywhere from 3 - 15 mins to complete depending on the Size of the file and the Speed
of your CD/DVD Burner.

Post Edited for Clarity ;)

---

### Post by hw-tph on 2006-03-02
...and to create an image from a CD, just use dd.


Håkan

---

### Post by pbransford on 2006-03-02
If I use dd, can I mount the resulting file as shown above?

Also, can dd skip over read errors (like bad sectors) and will it rip subcode data as well?

I should mention I'm looking for an archival-quality means of ripping.

---

### Post by krokodil on 2006-03-13
[QUOTE=akiro.yamamoto]
Insert the CD then right click and select Copy Disk.
When the "Write to Disk" dialog comes up. Choose "File Image" instead of your
CD/DVD Burner drive, then say "Write" and select where you want the ISO file to be created. ;)

To BURN a CD from an ISO image that you HAVE on your Hard Drive.
Right Click on the ISO image file and select "Write To Disk" insert a blank CD/DVD and select "Write".
[/QUOTE]

I've tried this with an audio CD, the Copy Disk creates 2 files: image.iso and image.iso.toc.

When I try to burn the .iso onto CD it says that it is invalid.

Any ideas?

---

### Post by tom56 on 2006-05-28
[QUOTE=krokodil]I've tried this with an audio CD, the Copy Disk creates 2 files: image.iso and image.iso.toc.

When I try to burn the .iso onto CD it says that it is invalid.

Any ideas?[/QUOTE]

Sorry to dig up an old thread but I've got the same problem! Any one know the solution?

---

### Post by hw-tph on 2006-05-30
For an audio CD you need to use cdrdao. **cdrdao read-cd mydisk.toc** will create a cue file named mydisk.toc and a data file called data.bin (change that file name with the --datafile option).


Håkan

---

