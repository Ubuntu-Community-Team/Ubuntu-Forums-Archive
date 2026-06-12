---
title: "Unable to mount external hard drive"
date: 2011-05-26
forum: General Help
---

### Post by admtuku on 2011-05-26
Hi, I'm new with ubuntu. today i connected a portable hard drive and successfully transferred some files to it from my local drive. then i unplugged the external drive. After some minutes i connected the drive again, but this time it shows an error. here it is:



[B]Unable to mount drive_name
Error mounting: mount exited with exit code 13:
ntfs_atlr_pread_i: ntfs_pread failed : Input/output error
Failed to read vcn 0x 1 :Input/output error
Failed to mount '/dev/sdd1':nput/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID  hardware. In the first case run chkdsk /f on Windows
then reboot into windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/directory,(e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.[/B]



I simply connected the drive with a windows 7, but it was not appeared in 'my computer'.
I simply remover the drive safely and then again connected it to ubuntu, but whenever i click on the drive name from 'places'  it shows the error message.

Any help,please?

---

### Post by ajgreeny on 2011-05-26
Did you unmount the USB drive before you unplugged it from Ubuntu?  It sounds as if you didn't from your description of what you did and the symptoms of your current situation.  It appears that it is formatted as ntfs, which is flagged up as in use by the linux file system, and if you don't remove it properly, it will still be in use to any linux system into which you plug it.

It is usually possible to overcome this problem by simply plugging it into a windows system, which you have tried without success.  I fear from that happening, that the filesystem on the USB disk may be corrupted, possibly because it was still writing to the disk as you unplugged it.  If that is the case, you may need to reformat the disk with gparted from the Ubuntu live CD/USB or with one of the Windows programs that are available.

Wait and see if anyone else has any ideas about mounting the disk and restoring the files from it it before you do anything, unless, of course, there is nothing on the disk that is not backed up or available elsewhere, in which case you probably have nothing to lose.

Just remember to _**ALWAYS**_ _**UNMOUNT**_ disks before unplugging them, most easily done in the file manager by right clicking on its icon in the left hand pane and choosing **unmount**, **eject**, or **remove safely** depending on the disk and your version of Ubuntu.

---

### Post by 741Baus on 2011-05-26
Hi I'm guessing that your external drive is formatted to ntfs open up Gparted and see if your external drive is listed if so it will be sdxy with xy being the name of your external drive then open up a terminal and enter this code

```
sudo apt-get install ntfsfix
```

then run this code in terminal
 
```
sudo ntfsfix /dev/sdxy
```

change xy to correspond with the name given by Gparted .

 I had to do this when a two year old child pulled a 1TB external dive that was file transferring of the desk crashing to the floor and bouncing a few times it wouldn't mount at all running these two codes fixed that I hope this helps

---

### Post by admtuku on 2011-05-27
trying the codes..

If i format the drive from any windows machine, will it work in ubuntu (after formatting) ?

---

### Post by 741Baus on 2011-05-27
Ubuntu will recognize a drive formated by Windows .

---

