---
title: "Using Testdisk Help!"
date: 2012-01-04
forum: General Help
---

### Post by mblack3nd on 2012-01-04
Hello All,

I was recently attempting to re-partition my hard drive as I was finally updating to 11.10. While using Gparted to accomplish this, it froze and now my partition (which was re-sizing) has a big error sign. I am attempting to use testdisk and, through a deeper search, I can see that partition (Media) and see the files and all that. But when I try to rewrite the table, it doesn't seem to be write as when I restart it, the same error shows.

If it helps, I think the original layout was 
P - Me (NTFS)
E
   L - Linux Swap
   L - Media (NTFS)
P - / (ext 4)
P - /home (ext 4)

Now of course I cannot make an extended partition in testdisk so I wonder if that is not part of the issue. Idk, I feel lost with all these, let me know what I can do to get my files back. Thanks for your help!

---

### Post by mblack3nd on 2012-01-04
here are the results of the "deeper search"...Media is the one giving me issues and I can list the files so it seems some what intact...the second entry gives an error of the filesystem being unreadable

---

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  4607 254 55   74027449 [ME]
D HPFS - NTFS           1977  63  7 19457  21 20  280813568
D Linux Swap            4608   0  1  5117 254 41    8193128
D Linux Swap            4608  24 25  5117 228 23    8189936
D HPFS - NTFS           4608  56 57 16223  55 49  186594905 [Media]
D Linux                16733   0  1 18799 203 41   33203120
D Linux                18799 232 58 19457  53 52   10559488

---

### Post by mblack3nd on 2012-01-04
Lookint at this closer...I am not quite sure what is going on with that second entry but it seems to claim to cover all the rest of the entries/partitions????

---

### Post by mblack3nd on 2012-01-04
Im afraid to move at this point without any guidance so Ill just wait until somebody gives some advice...I would hate to screw it up if I can actually salvage the partition.:-\"

---

### Post by mblack3nd on 2012-01-05
My battery died out...when i re-ran test disk, this error showed up

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63

The harddisk (160 GB / 149 GiB) seems too small! (< 161 GB / 150 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                17549   0  1 19615 203 41   33203120

---

after accepting, the rest as was posted above...plz help!!!

---

### Post by mblack3nd on 2012-01-05
Back again...I cannot sleep until I (well not really me since I don't know what I am doing) get this fixed. I just don't understand how to access my files!!!!!!!!!!

In Gparted, the error is:

Failed to mount '/dev/sda5': Input/output error. NTFS is inconsistent. Run chkdsk /f on Windows then reboot it twice! The usage of the /f parameter is very IMPORTANT! No modification was made to NTFS by this software.....

I do not have Windows or access to windows.....

PLEASE PLEASE PLEASE SOMEBODY OUT THERE HELP ME :'(

---

### Post by dandnsmith on 2012-01-05
The HDD positions look a bit odd, but I guess that depends on how that utility presents them.
The 2nd partition, as you depict in your remembered layout, is an extended partition - and the position and extent of that is sufficient to encompass all the logical partitions (at least).
I don't understand why the utility offers 7 partitions, where you show 6, but perhaps this is something to to with the reason why 2 swap partitions are shown.
The comment about the apparent size being too small may have something to do with a particular area in the HDD first block (if this is an MBR layout HDD) where, following Microsoft practice, a record of the disk size is kept - which linux usually ignores, getting the sizes from the BIOS.

I don't know if any of this helps, but here's hoping you can sort it.

Added: Lack of access to Windows is rather unfortunate. The advice corresponds to the NTFS being a proprietary format, with Microsoft being the owners and final reference source. What might seem a reasonable solution to the linux tools may well result in a file system unusable by Windows - so you have to make your decision based on that. I commiserate.

---

### Post by mblack3nd on 2012-01-05
Thanks Dan...that certainly clears up what I had been concluding on my own...still unsure where to go from here...at the very least I want to mount the partition so I can move my files over somewhere else...I have an external hard drive up at school which I won't have access to for a while and since I was just installing a new one completely, if I can get the files off, I can just format and start over you know?

---

### Post by mblack3nd on 2012-01-05
I recently ran 

```
sudo ntfsfix /dev/sda5
```with the following result:

 ntfs_mst_post_read_fixup: magic: 0xfe4e0914  size: 1024  usa_ofs: 11579  usa_count: 33714: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x7be5fa4f  size: 1024  usa_ofs: 55894  usa_count: 45733: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x8a43428a  size: 1024  usa_ofs: 19222  usa_count: 6813: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x98b7e6ff  size: 1024  usa_ofs: 56959  usa_count: 3203: Invalid argument
$MFTMirr error: Invalid mft record for '$MFT'.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... ntfs_mst_post_read_fixup: magic: 0xfe4e0914  size: 1024  usa_ofs: 11579  usa_count: 33714: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x7be5fa4f  size: 1024  usa_ofs: 55894  usa_count: 45733: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x8a43428a  size: 1024  usa_ofs: 19222  usa_count: 6813: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x98b7e6ff  size: 1024  usa_ofs: 56959  usa_count: 3203: Invalid argument
OK
Comparing $MFTMirr to $MFT... FAILED
$MFTMirr error: Invalid mft record for $MFT.

---

### Post by imachavel on 2012-01-05
> **mblack3nd said:**
> Hello All,

I was recently attempting to re-partition my hard drive as I was finally updating to 11.10. While using Gparted to accomplish this, it froze and now my partition (which was re-sizing) has a big error sign. I am attempting to use testdisk and, through a deeper search, I can see that partition (Media) and see the files and all that. But when I try to rewrite the table, it doesn't seem to be write as when I restart it, the same error shows.

If it helps, I think the original layout was 
P - Me (NTFS)
E
   L - Linux Swap
   L - Media (NTFS)
P - / (ext 4)
P - /home (ext 4)

Now of course I cannot make an extended partition in testdisk so I wonder if that is not part of the issue. Idk, I feel lost with all these, let me know what I can do to get my files back. Thanks for your help!

Are your files backed up? Every time I've used gparted to partition my disk, I boot to it, instead of using it from the desk top once the OS is already loaded. I've haven't had a problem using gparted to resize a disk where files were lost. Only one where I got a message saying partition could not be resized. From what I know, this is because of partitions needing to be contiguous. Now, I hope you backed up your files, resizing partitions is always a risk. Did you try shrinking your partition? If your files filled up most of the space left on the partition, to shrink the partition, files would be lost. My assumption is that you tried to enlarge the partition.

Always be cautious with these tasks.

---

### Post by imachavel on 2012-01-05
> **mblack3nd said:**
> Thanks Dan...that certainly clears up what I had been concluding on my own...still unsure where to go from here...at the very least I want to mount the partition so I can move my files over somewhere else...I have an external hard drive up at school which I won't have access to for a while and since I was just installing a new one completely, if I can get the files off, I can just format and start over you know?

ok I've never used test disk or gotten ultimate boot cd to work. My knowledge of disk error fixing lies with chkdsk(windows) fsck(linux) which I haven't mastered too well. Best idea to get your files off, remove the hard drive, obtain a sata or ide to usb transfer device, hook up your hard drive to a friends computer, copy and paste the files. Sorry I'm not a data recovery disk expert. If any files still exist, they will be shown. help at all?

---

### Post by mblack3nd on 2012-01-05
I haven't backed up the files in about a year and there is a copy of my book that I need and of course...my files are really important for me.

I want to think that they are mostly salvageable since I can seem them while running test disk.

Yes I was enlarging and that is when it froze up...it was going to "move left" and "grow" to essentially fill up the whole of the extended partition

---

### Post by mblack3nd on 2012-01-05
> **imachavel said:**
> ok I've never used test disk or gotten ultimate boot cd to work. My knowledge of disk error fixing lies with chkdsk(windows) fsck(linux) which I haven't mastered too well. Best idea to get your files off, remove the hard drive, obtain a sata or ide to usb transfer device, hook up your hard drive to a friends computer, copy and paste the files. Sorry I'm not a data recovery disk expert. If any files still exist, they will be shown. help at all?
 
Yeah, that helps I just need to figure out how to do that I guess haha

---

### Post by imachavel on 2012-01-05
[http://www.youtube.com/watch?v=WCx3GOcRMIk&feature=related](http://www.youtube.com/watch?v=WCx3GOcRMIk&feature=related)

---

### Post by alphaamanitin on 2012-01-05
You could also email the creator for advice.  I have only used TestDisk once, to restore an NTFS partitions after a complete reformatting (quick formatting) to FAT32.  Worked like a charm.  

AlphaA

---

### Post by mblack3nd on 2012-01-05
Thinking about this more I was wondering...in order to run windows check disk on my drive, is there a way to do it over the internet...I am connected to the same router that my parents computer (which runs XP) runs on

---

### Post by dandnsmith on 2012-01-06
As far as I know, chkdsk addresses 'Windows' drive letters - so you'd need it mounted. I've never tried it on partitions which weren't on a drive belonging to the PC in question, so have not idea whether this is even a remote possibility - I think it unlikely, and that the drive will be addressed directly, using the BIOS. No harm in trying, 'tho.

---

