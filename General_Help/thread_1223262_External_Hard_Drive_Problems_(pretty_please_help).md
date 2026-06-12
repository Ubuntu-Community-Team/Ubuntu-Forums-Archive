---
title: "External Hard Drive Problems (pretty please help)"
date: 2009-07-25
forum: General Help
---

### Post by Zoey.Marie on 2009-07-25
This is cross posted from the thread in the "Beginners Section" (which, was posted from the Hardware..." section...) Maybe I'll get more help here?

I'm on Jaunty Jackalope, which was installed just a couple days ago. It's a Maxtor something-something (I don't remember) in an I/O Magic Case. It's formatted as NTFS (something I am thinking about changing once I can access my files).

It worked wonderfully on XP (although, IMO, XP didn't work wonderfully for me), and then a few days ago I installed Ubuntu. When I tried hooking up the drive, it said:
>  Unable to mount the volume 'New Volume'.
Details:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error Failed to read NTFS $Bitmap: Input/output error NTFS is either inconsisten, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reeboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details. 
If I left that window open, it would say:
>  DBus error org.freedesktop.DBus.Error.NoReply: Message did not recieve a reply (timeout by message bus) 

I tried to take it to a windows machine, and do the "safely remove" thing--'cause I guess with NTFS that can cause it to not mount correctly.
-- That didn't work, and, in fact, on the Windows machine, even though it showed up in MyComputer and in the Device Manager everything was working fine, it didn't read like there was ANY information on there (like, it didn't even say the size of the disk). Plus, it said that the filesystem was "RAW". No clue what any of that means.

So now, I am back on my computer--Ubuntu 9.4--and it's still giving me the same error messages above.

Other stuff:
lsusb shows it.
sudo fdisk -l shows it, AND shows how big it is and that it is NFTS...
sudo mount -t ntfs-3g /dev/sdb1 /mnt/ntfs does nothing but give me the same error message as when I try and mount it through the GUI
sudo ntfsfix /dev/sdb1  doesn't really do anything either...  it says "pread: Input/Output error
Failed to calculate number of free clusters: Input/Output error.
FAILED
(then it attempts to correct, and everything says OK)"
But then it does the same "pread..... Failed to calculate number of free clusters" thing. Last thing it says is: "Remount failed: Input/output error."
  
Someone reccommended using a LiveCD of "Puppy Linux" and "PartedMagic" to troubleshoot it, I think...  Anyone got any other ideas, or is that the way to go?

Thanks a bunch.
[U]
[/U]

---

### Post by merlinus on 2009-07-26
Did you run chdsk <drive>: /f on windows?

Did you create the mountpoint in linux?  If so, you can try to force mount it:

```
sudo mount -t ntfs /dev/sdb1 /mnt/ntfs -o force
```

---

### Post by Zoey.Marie on 2009-07-26
@merlinus:

Yeah, I did. It gave me the same error message that it did when I tried to mount it without the 'force' thing...

UPDATES: I can access the files running Puppy Linux live (though it spits out the error message first... then mounts it)... But it's SO freaking slow (and I have some big files on the drive). If everything else fails, I can copy my files to my home folder, and then change the permissions on them, right?

Is there an easier way to do it, so I don't have to use the LiveCD (and wait forever and ever and ever?)--Plus, there's less space on my home disk than there is on the drive, so unless I copied stuff to another external (idea!!... still slow though) I would still have to delete stuff...

Any other ideas?

---

### Post by merlinus on 2009-07-26
You can certainly copy the files to /home and then change permissions, but hopefully none of them are corrupted due to whatever problem is stopping linux from force-mounting the partition.

Knoppix might be faster....it's another live cd linux distro, but very good at detecting and mounting drives.

---

### Post by Zoey.Marie on 2009-07-26
@merlinus:

Yeah, I suppose if copying everything to my drive, changing permissions, reformatting the external, and then putting stuff back on there is what I need to do, then I suppose I'll do it--and hopefully Knoppix will be a quicker way to do that than Puppy Linux... 

Sigh.
Is that really the only way that i can do this??

---

### Post by merlinus on 2009-07-26
Clonezilla can create an image of the hdd that then can be restored, but it might also copy whatever problems exist.

It may well be that the hdd has become defective, and/or there are bad blocks.

---

### Post by Zoey.Marie on 2009-07-26
> **merlinus said:**
> Clonezilla can create an image of the hdd that then can be restored, but it might also copy whatever problems exist.

It may well be that the hdd has become defective, and/or there are bad blocks.

Ooh! that could be fun... I might at least try it, I suppose... I don't know if you know (and I certainly don't), but if I copied the image of the hdd, reformatted it, and then restored the data to it... do you think that would work?
-- all my data appeared to be there in Puppy Linux earlier, but I don't know if that necessarily means that it isn't a bad block thing.

Shrugs.

---

### Post by merlinus on 2009-07-26
Clonezilla is used to copy partitions from one hdd to another, so it should work in this case.

---

