---
title: "How can I check USB-HD for errors?"
date: 2011-12-04
forum: General Help
---

### Post by ohnonot on 2011-12-04
Hello!
It seems a simple enough task but I can't get it done.
and there's something weird going on...

It's a Maxtor 300GB USB-Disk, getting old now and sometimes during startup i get a message: device is not ready to mount, press S to skip or M for manual recovery. Pressing S just hangs the boot process, so i reboot 1-2 times and everything is fine. 
I *think *this always happens after i've been doing something concerning usb (dongle, printer...) 
However my media player sometimes skips files with an error message like file cannot read from disk.

plenty of reason to check the disk for errors.

I tried the disk utility, but it wouldn't let me check a mounted drive and it wouldn't let me unmount (only root can).
so i tried another program called pysdm (storage device manager) - that would let me unmount but i noticed something weird: the program shows that both drives are mounted as ntfs at the same mount point, which is in reality the mount point for the usb drive. my first hd is mounted at /.

i uninstalled pysdm, i find it highly suspicious.

so, now i'm back to the disk utility, drive is unmounted, i press "check filesystem" ---- and get a success message *immediately*  -  no errors - but obviously nothing has happened.

can anybody make sense out of this? any help would be appreciated. thanks.

---

### Post by CharlesA on 2011-12-04
Run fsck from a livecd and see if it gives you any errors.

---

### Post by ohnonot on 2011-12-04
i ran it 3 ways from a live cd - but first i had to find out which is the dongle and which is the hard drive. found out that sdb was the dongle by unplugging it - so i was left with sdc.
though when booting normally i think the usb-hd is sdb.

anyway here's what the terminal gave me:

```
sudo fsck /dev/sdc
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in suber-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt and you might try running
  e2fsck -b 8193 <device>
``````
sudo e2fsck -b 8193 /dev/sdc
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Bad magic number in suber-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2  filesystem. If the device is valid and it really contains an ext2  filesystem (and not swap or ufs or something else), then the superblock  is corrupt and you might try running
  e2fsck -b 8193 <device>
``````
sudo fsck.nfs /dev/sdc
/dev/sdc: NFS file system.

```running the same commands after booting normally:

```
sudo fsck /dev/sdb
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?

``````
sudo e2fsck -b 8193 /dev/sdb
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?

``````
sudo fsck.nfs /dev/sdb
/dev/sdb: NFS file system.
```

---

### Post by CharlesA on 2011-12-04
What file system is that drive running?

---

### Post by ohnonot on 2011-12-04
> **CharlesA said:**
> What file system is that drive running?
:oops:
oops, i completely forgot to mention that. i think it's ntfs (that's the same as nfs, right?)
and i've been using it under windows for years before i changed to linux.

---

### Post by idoitprone on 2011-12-04
> **ohnonot said:**
> :oops:
oops, i completely forgot to mention that. i think it's ntfs (that's the same as nfs, right?)
and i've been using it under windows for years before i changed to linux.

If you do not know then 
try

```
blkid
```if you need root permissions

```
sudo blkid
```It is a utility that will tell both the uid and file system type
If it is ntfs, then dont use fsck. Please use windows tool because microsoft changed ntfs filesystem  over the years.

---

### Post by CharlesA on 2011-12-04
> **ohnonot said:**
> :oops:
oops, i completely forgot to mention that. i think it's ntfs (that's the same as nfs, right?)
and i've been using it under windows for years before i changed to linux.

If it's NTFS, you'd need to use a Windows box to check it, not fsck.

---

### Post by ohnonot on 2011-12-04
yes, it is definitely ntfs.
so nothing doing with linux? do i have to use wine + some windows tool?
i suppose it's not possible to change the fs without formatting the whole disk?

but thanks anyway!

---

### Post by CharlesA on 2011-12-04
There is no NTFS tool for Linux, so you are going to have to get a Windows cd to run the chkdsk on it.

---

### Post by ohnonot on 2011-12-06
right. what a hassle.
i have difficulty finding the right bootable cd - to check, repair and defrag the disk -
could someone point me in the right direction?
thanks anyway.

---

### Post by Mark Phelps on 2011-12-07
If you want to create your own CD, you can try downloading and burning Hiren's Boot CD.  I believe it has a bunch of disk utilities on it -- any of which can be used to check the drive.

Apart from that, you will need a Windows disk that is bootable -- and runs something once started.  XP Win7 disks can be booted into safe mode or a command line to do that.

---

### Post by dcstar on 2011-12-08
> **ohnonot said:**
> :oops:
oops, i completely forgot to mention that. i think it's ntfs (that's the same as nfs, right?)


NTFS has absolutely nothing to do with "NFS".

---

### Post by ohnonot on 2011-12-10
> **dcstar said:**
> NTFS has absolutely nothing to do with "NFS".but they are both file systems, right?
would you care to elaborate?

and thanks to mark phelps, i'm checking out hiren's boot cd.
also, taking the drive out of fstab so it won't be mounted at startup really helped.
meaning it doesn't hang the boot process anymore.
as soon as i checked with the cd i'll mark this as solved.
and thanks again.

---

### Post by killermist on 2011-12-10
> **ohnonot said:**
> but they are both file systems, right?
would you care to elaborate?

and thanks to mark phelps, i'm checking out hiren's boot cd.
also, taking the drive out of fstab so it won't be mounted at startup really helped.
meaning it doesn't hang the boot process anymore.
as soon as i checked with the cd i'll mark this as solved.
and thanks again.

NFS is the Network File System used to communicate file trees between machines over a network.  It has no on-disk format because it is used for sharing file trees between network-connected machines. Linux, Unix, BSD, Minix, and Solaris (possibly others) have workable compatible interfaces to use it.

NTFS is (or was) the NT (like Windows NT) File System.  It is a disk storage filesystem.  Being designed by Microsoft, it has some "quirks" (few of them good).

---

### Post by ohnonot on 2011-12-14
i tried falcon4's boot cd (based on hiren's).
chkdsk aborted with an "unspecified error" (sic).
(i also tried chkdsk it with another disc where it got stuck at 50%)
i tried another tool that just tests the disk and it shows some bad blocks but also got stuck after a while. very weird. i mean, the program just got stuck, no error message, no cpu usage, nuffink.
is there any program that is able to repair (marking bad sectors as unusable) the disk? besides chkdsk?

i am aware that this is totally not about ubuntu anymore but since we started the discussion, mayb someone has sth to add?

@killermist: thanks for the explanation. very much appreciated.

---

