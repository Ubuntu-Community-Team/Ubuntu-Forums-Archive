---
title: "Problem with FS-cache in PXE-booted environment"
date: 2011-01-28
forum: General Help
---

### Post by meanderix on 2011-01-28
I've installed a diskless Ubuntu system with the latest 64-bit Maverick kernel, by following the instructions found here:

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

However, the clients are not diskless and I want to take advantage of this by using a local cache of the nfs-mounted filesystem. I'm using fs-cache and the cachefilesd package for this purpose. Of course I want to cache the whole root file system and in order for that to work, the filesystem must be mounted with the "fsc" mount option.

Hence, in my fstab I have the following entry:
```

/dev/nfs	/               nfs	fsc		1       1
```

However, I can easily verify that the fsc mount option is not being used when mounting the root system:
```

# cat /proc/fs/nfsfs/volumes 
NV SERVER   PORT DEV     FSID              FSC
v3 81102339  801 0:17    562aac732e56f8ac  no 
```
If I mount an nfs share manually after booting then it will use the fsc flag without any problems. However, I'd rather not try to remount the root file system, even if that might work.

I also learned that there's a special kernel option called "rootflags" that specifies the mount options for the root file system, so I tested modifying the kernel boot parameters as follows:
```

append root=/dev/nfs rootflags=fsc initrd=ubuntu-boot/initrd.img-2.6.35-24-generic nfsroot=11.22.33.44:/data/nfsroot ip=dhcp rw
```
However, the root file system is still mounted without the fsc option.

What do I need to do to enable the fsc mount option so that fs-cache will work?


Update:

According to the manpage for [initramfs-tools](http://manpages.ubuntu.com/manpages/maverick/en/man8/initramfs-tools.8.html), you should be able to specify the NFS mount options as a kernel parameter using NFSSERVER:NFSPATH:NFSOPTS, but I suspect this is not correct -- when I test it only works if I use the format NFSSERVER:NFSPATH,NFSOPTS. Perhaps the manpage needs to be updated?

The following manpage for NFS does not list **fsc** as one of the options:
[INDENT][http://manpages.ubuntu.com/manpages/maverick/en/man5/nfs.5.html](http://manpages.ubuntu.com/manpages/maverick/en/man5/nfs.5.html)[/INDENT]
However, the following does:
[INDENT][http://linux.die.net/man/5/nfs](http://linux.die.net/man/5/nfs)[/INDENT]

Is this because it's two different versions?

When I try to use the fsc option, I get the following error:
```
nfsmount: bad option 'fsc'
```

---

### Post by xris_xcess on 2011-03-04
Hi...

(sorry, slightly off topic)...

I use to run a diskless system (server-clients) with 9.04 and then 9.10, with no problems. I decided to upgrade to 10.10 on the server and clients (and over to nfs4 while I was at it)... and for the life of me I can't get it to work anymore!!!

I've looked everywhere for some hint or solution, but nothing.

I get as far as trying to mount the nfs share to root (/dev/nfs) and it just stalls and doesn't mount the /home directories (also on nfs).

Did you run into any problems at all? I really is driving me insane not being able to pin it down!!! Any pointers as to how to track the fault down (i've checked most of the logs on the server and on the client...).

thanks

---

### Post by Piotr Mazur on 2011-07-08
I'm struglling with the same problem at the moment, using diskless natty release.
So far i have everyting working, but it seems enabling nfs cache is not possible when using root nfs mount.
In kernel options you can only select NFS caching when you have NFS client compiled as a module. Root NFS requires setting NFC client as a compiled-in option which in turn disables NFS caching option. 
So far i havnt found any explanation to why you cannot enable these two simultanousely. 
I think this is why you cannot enable caching when using root nfs.

Or maybe anyone can shed some more light on this situation? Combining root nfs with fscache would be great.

---

### Post by MiscDebris on 2012-02-02
I'm working on this right now.  I had it working for Lucid.  I'm posting to remind me to post once I get it working.

---

