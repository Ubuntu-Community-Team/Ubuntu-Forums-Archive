---
title: "Wubi installation won't boot or mount"
date: 2010-12-19
forum: General Help
---

### Post by outspaced on 2010-12-19
Hi,
  

As of today, my wubi installation of Ubuntu won't boot (goes straight  to 'minimal bash-like interface) and I am unable to mount it when I  boot straight to Ubuntu.

  If I boot straight into Ubuntu (not using Wubi, not going via  Windows), I am able to mount the Windows partition and see the Wubi  partition there:
  
    sudo mount -t ntfs /dev/sda5 /media/winxp
 
And from there I can see the wubi root disk:
  
    /media/winxp/ubuntu/disks/root.disk
 
But if I try to mount this:
  
    sudo mount -o loop /media/winxp/ubuntu/disks/root.disk /media/wubi
 
I get an error:
  
    /media/winxp/ubuntu/disks/root.disk Input/Output Error
 
If I then try fsck:
  
    sudo fsck /media/winxp/ubuntu/disks/root.disk
 
I get this:     Input/Output Error while trying to open /media/winxp/ubuntu/disks/root.disk 
  The Superblock could not be read or does not describe a correct etx2  filesystem.  If the device is valid and it really contains an ext2  filesystem (and not swap or ufs or something else), then the superblock  is corrupt and you might want to try running e2fsk with an alternate  superblock:
  
    e2fsck -b 8193 <device
 
... this gives me the same result.
  
There is data on this partition that I really need to be able to access, so I can't delete and reinstall.
  
Any help much appreciated.  Thanks.

---

### Post by theasprint on 2010-12-19
You mean you got 3 OS-es?
1. Windows
2. Wubi Ubuntu
3. Non-wubi Ubuntu?

Ok. If you can boot Ubuntu, go and download the Boot Info Script (Link at my signature) and "bash" it and post the results here.

---

### Post by outspaced on 2010-12-19
Hi,

Thanks very much for your reply, and for providing such an easy to use script.

You're right about the 3 operating systems - I plan to eventually remove the Wubi one, but there were a few things that didn't immediately work in the Non-Wubi install that I haven't had time to resolve yet.

Anyway, I've attached the results of the script here.  Please let me know if there's anything else you need.

Thanks,
Alex

---

### Post by bcbc on 2010-12-19
Bootinfoscript doesn't see a root.disk at all. 

Run chkdsk from Windows - My Computer, right click on drive containing Ubuntu, Properties, Tools, Check disk for errors, Automatically fix.
Or,
Look for hidden \FOUND.??? folders under your Windows partition and see if you can locate the root.disk. It might have already been moved if it was corrupted.

That's all I can think of as to why it's just gone missing.

---

### Post by outspaced on 2010-12-20
If I boot into Windows, then the root.disk file is there under:

U:/ubuntu/disks/root.disk

The file is roughly 30GB - the size of the wubi partition.

I'm just backing it up now and will run the disk check afterwards.  I'll post the results here when done.

---

### Post by theasprint on 2010-12-20
Hi,

+1 for chkdsk and corruption scanning.

To bcbc: 
Just for learning purposes, 
The root.disk directory is supposed to appear in "Boot files/dirs" right?
And how did sda7 (I assume its the Non-Wubi install) turn into ext3 filesystem? (not ext4?)

Thanks.

Good Luck :D

---

### Post by outspaced on 2010-12-20
Bizarre.

I did the error scan - it said no errors found.  I thought I'd try booting back into my Wubi installation anyway, just to see if it made a difference and it loaded!

Very weird situation, but I'm just ecstatic to have my work back.  For a while, it was looking like it was going to be a very miserable Christmas of redoing work for me!  Backing up everything now.

Thank you both very much for your help. :KS:KS:KS:KS:KS

---

### Post by theasprint on 2010-12-20
Hi,

Wow, that was really strange. But don't hesitate to report back again if there is a problem.

Enjoy your Ubuntu!

---

