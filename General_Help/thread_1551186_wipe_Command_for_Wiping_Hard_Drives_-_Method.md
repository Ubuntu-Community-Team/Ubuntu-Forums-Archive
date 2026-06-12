---
title: "wipe Command for Wiping Hard Drives - Method?"
date: 2010-08-12
forum: General Help
---

### Post by deadimp on 2010-08-12
I can't remember if this was on the manpage for wipe or on a website describing wipe, but it stated that if I wanted to wipe a hard drive I should wipe all of the partitions instead of wiping the entire device to preserve the master boot record.
It also said somewhere that wiping a journaling file system, such as ext* or NTFS, amounts to an exercise in futility... But right now I have it wiping my partitions which include these types.

Thing is, I don't really care about preserving the file system itself, I'm going to delete it after it's all said and done. Should I just run wipe on the device?
My thinking is that if it runs it on the partition file system, it does the whole slew of file renaming / truncating / shifting rigamaroo and preserves the system, which would slow it down and might leave the journal intact if it simple instruments access through common file operations.
Does running wipe on the harddrive simple treat the hard drive as one contiguous 'file' (better said 'block device') without the 'rigamaroo'?
If so, that's the option I'd want to take.
And if this happens, is there a way to restore the MBR? Just do it before I restart the computer?

---

### Post by bodhi.zazen on 2010-08-12
What are you wanting to do ?

Most of the time you can simply reformat the drive and move on.

If you wish to remove data, however, you need to over write it.

I suggest using dd

```
dd if=/dev/zero of=/dev/sdxy bs=1M
```

IMO there is no need to use a utility that makes multiple passes as the gutmann theory has been debunked.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

---

### Post by linux18 on 2010-08-12
> **bodhi.zazen said:**
> What are you wanting to do ?

Most of the time you can simply reformat the drive and move on.

If you wish to remove data, however, you need to over write it.

I suggest using dd

```
dd if=/dev/zero of=/dev/sdxy bs=1M
```

IMO there is no need to use a utility that makes multiple passes as the gutmann theory has been debunked.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)
doesn't the ext filesystem creates sparce files when you use dd in that manner. which means the command should be:

```
 dd if=/dev/urandom of=/dev/sda bs=1M 
```

---

### Post by bodhi.zazen on 2010-08-12
> **linux18 said:**
> doesn't the ext filesystem creates sparce files when you use dd in that manner. which means the command should be:

```
 dd if=/dev/urandom of=/dev/sda bs=1M 
```

Not that I know of.

---

### Post by gordintoronto on 2010-08-12
Darik's Boot and Nuke ("DBAN") is a self-contained boot disk that securely wipes the hard disks of most computers. DBAN will automatically and completely delete the contents of any hard disk that it can detect. [http://www.dban.org/](http://www.dban.org/) Be careful when you run it, it will delete the contents of all your hard disks!

---

### Post by philinux on 2010-08-12
> **gordintoronto said:**
> Darik's Boot and Nuke ("DBAN") is a self-contained boot disk that securely wipes the hard disks of most computers. DBAN will automatically and completely delete the contents of any hard disk that it can detect. [http://www.dban.org/](http://www.dban.org/) Be careful when you run it, it will delete the contents of all your hard disks!

Yes but it takes ages. One pass with dd is enough. ```
dd if=/dev/zero of=/dev/sdxy bs=1M
```

[http://www.anti-forensics.com/disk-wiping-one-pass-is-enough](http://www.anti-forensics.com/disk-wiping-one-pass-is-enough)

---

### Post by abitwise on 2011-04-13
I tried this on a 160 GB hard drive. SATA drive, connected with a USB to SATA adapter. This ran 10 hours and then i killed it off. I tried also shred, which ran like 24 hours and did a 94 GB "job" until i killed it. How on earth can u use these? Now i try "wipe" with fast mode, prediction is 30 hours at least. And i have some more disks to go, i think the world needs a better software for deleting, hard drives are not that slow! The speed should be at least 10 MB/s (this would take little over 4 hours). Or am i missing something?

---

### Post by alphaamanitin on 2011-04-13
I up the bs to bs=16 or 32.  Have wiped a 1 terabyte drive over night.  Not sure, if you doing so causes the likelihood of incomplete data deletion to rise though.

AlphaA

---

### Post by ottosykora on 2011-04-13
ok, google for killdisk

small util, might help you, but

consider that our file systems have some problem, they try to note any changes to a 'directory' to be able to 'find it later' which is not useful in this case. But it is so. The low level overwriting which was posible with drives some 20 years ago is not possible any more as we can talk just to the controller and this one does what it thinks is right and not what we think it should do.
Yes, we need to overwrite the disk only once, tis is true, but I remamber that members of pgp usenet group did find few times that using wipe function with 8 passes still left some data on the disk as it was all doing nice wipe ops in the buffer of the drive and not actually on the magnetic surface itself.

Today manipulating the actual surface of the disks is getting more and more difficult, as we little controll over what the firmware of the drive is doing.

And when it comes to solid state devices, we are lost completely, as any overwriting from the user side will still leave some 30% of data on the chips.

---

