---
title: "Convert from 32 bit to 64 bit, why not?"
date: 2011-02-24
forum: General Help
---

### Post by dannysauer on 2011-02-24
So, I'm finally upgrading my 1GB RAM P3-800 fileserver by replacing the motherboard, CPU, and RAM in the otherwise good case.  I'm moving to a quad-core AMD-64 CPU and 16GB RAM, and so I figured it'd be worthwhile to switch over to a 64-bit system at the same time (though it'll probably be a little faster either way, which has almost nothing to do with the CPU).  But I hate having to reconfigure everything manually.

I did some searches, and there are several threads that say "no, you can't just convert".  But why not?  This isn't a desktop system, so I don't care about junk like Flash and the latest nVidia drivers.  I'm essentially just replacing libc, programs linked against libc, and the kernel.  Shouldn't this just be a matter of reinstalling all of the existing packages - which is very much the same thing as changing the distro version?  What super mega secret complexity of "larger integers" am I missing?

---

### Post by ender4 on 2011-02-25
I may be wrong, but I think that in theory it is quite possible to upgrade all the existing packages.  But in practice it is much easier to do a clean install, and less likely to accidentally forget to switch a vital library from 32 bit to 64 bit.

---

### Post by dannysauer on 2011-02-25
I don't see why forgetting a dependency should be a concern - this is what the package manager does for a living. :)

---

### Post by dannysauer on 2011-03-07
If I upgrade to the next release using the 64-bit alternate disk, what're the odds of that working? :)

---

### Post by mcduck on 2011-03-07
> **dannysauer said:**
> If I upgrade to the next release using the 64-bit alternate disk, what're the odds of that working? :)

pretty much nonexistent. :D

You really need to make a fresh install if you want to change to different CPU architecture. During the upgrade form 32-bit to 64-bit you'd end with a situation where the current 32-bit system would have to execute 64-bit files, which it can't do...

---

### Post by TBABill on 2011-03-07
Sounds like it *can* be done but most users will not have the skillset to troubleshoot the unknowns because there will likely be little help available since most people never attempt it. This guy got it to work on Fedora, however: [http://www.linux.com/archive/feature/123800](http://www.linux.com/archive/feature/123800)

---

### Post by mcduck on 2011-03-07
> **TBABill said:**
> Sounds like it *can* be done but most users will not have the skillset to troubleshoot the unknowns because there will likely be little help available since most people never attempt it. This guy got it to work on Fedora, however: [http://www.linux.com/archive/feature/123800](http://www.linux.com/archive/feature/123800)

There alwasy sems to be a wway to do impossible things in Linux, at least if you have the skills and are prepared to handle lots of things manually, through some trick or other. Kind of like the tricks for applying kernel updates without rebooting and such.

But any automatic upgrade method would definitely fail. Besides, I'm quite confident that a fresh install would still be less time consuming way to handle such upgrade, at least in most cases.

edit: If you can remember which setting files you have modified, just make a backup of them, and you should have your system back running in just a hour or two even if you do a fresh install instead of upgrading. (this is why I have the habit of documenting any tweaks I make into my system, keeping them in a text file I can refer if I ever need to repeat them. Not that I'd actually ever had to do that, but at least it's nice to know I can easily get everything back to how it was and not have to worry about upgrades... :) )

edit2: Anyway, thanks for the link about the cross-grade. Definitely interesting stuff to read. :)

---

### Post by TBABill on 2011-03-07
I'm in total agreement. I wouldn't waste the time or the energy attempting that which is unsupported and recommended not to do. So much quicker to just do a fresh install and copy back any /home info or just not format the /home partition if it's separate from /.

---

### Post by Kirboosy on 2011-03-07
Agreed. I would say that fresh installing would be faster all the way around. Sure you will have to re-setup a few things but your system will be faster, more stable, and more awesome ;) (I don't know where the last one came from but I'm going with it. haha)

---

### Post by uRock on 2011-03-07
Fresh install for the win.

---

### Post by FoxEWolf on 2011-03-07
concern of a vital file/library not being converted should be enough of a push to do a fresh install but back up /home folder.

---

### Post by 3Miro on 2011-03-07
32 to 64 would require replacing pretty much all packages (with the possible exception of some icon themes). You have nothing to gain from trying anything other than a fresh install.

---

### Post by khelben1979 on 2011-03-07
I totally agree with the above posters saying you should do a fresh install.

---

### Post by dannysauer on 2011-04-03
> **FoxEWolf said:**
> concern of a vital file/library not being converted should be enough of a push to do a fresh install but back up /home folder.

If it's vital, it'll be obvious pretty quickly that it's broken.

There's a number of how-tos on Debian systems. Changing a few version strings around and following the general advice, it's fine on Ubuntu. So, here's a couple of links for everyone who said it's impossible or whatever. ;)

[http://www.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html](http://www.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html)
[http://www.verboom.net/blog/index.html?single=20101023.0](http://www.verboom.net/blog/index.html?single=20101023.0)

"Unsupported."  Bah.  Like Canonical will answer my phone calls normally. :)

The first link also mentions that anyone competent should be using Cfengine and avoid this garbage, which I also happen to agree with.  I really need to be more competent on my personal systems so I can avoid these hassles in the future - Cfengine rocks. :D

And, for the benefit of the person who said "just back up /home", umm, this isn't someone's simple desktop system (it's named humpy after Humpy Wheeler, if you must know). :)

```

sauer@humpy:~$ cat /proc/mounts 
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=4125868k,nr_inodes=193989,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/mapper/raidvol-root / reiserfs rw,noatime,nodiratime,usrquota,grpquota,user_xattr 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
/dev/md0 /boot xfs rw,sync,nosuid,nodev,noatime,nodiratime,wsync,attr2,noquota 0 0
/dev/mapper/raidvol-usr /usr reiserfs rw,noatime,nodiratime,usrquota,grpquota,user_xattr 0 0
/dev/mapper/raidvol-var /var reiserfs rw,noatime,nodiratime,usrquota,grpquota,user_xattr 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
/dev/mapper/idevol-log /var/log reiserfs rw,noatime,nodiratime,usrquota,grpquota,user_xattr 0 0
/dev/mapper/idevol-squid /var/spool/squid reiserfs rw,noexec,noatime,nodiratime,notail 0 0
/dev/mapper/raidvol-homes /mnt/raidvol/homes reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/raidvol-netboot /mnt/raidvol/netboot reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-temps /mnt/idevol/temps reiserfs rw,noatime,nodiratime,usrquota,grpquota,user_xattr 0 0
/dev/mapper/idevol-apt_cache /mnt/idevol/apt_cache reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-midnight /mnt/idevol/midnight reiserfs rw,relatime,user_xattr 0 0
/dev/mapper/idevol-mtdaapd /mnt/idevol/mtdaapd reiserfs rw,relatime,user_xattr 0 0
/dev/mapper/idevol-eucalyptus /mnt/idevol/eucalyptus xfs rw,noatime,nodiratime,attr2,noquota 0 0
/dev/mapper/idevol-vmware /mnt/idevol/vmware reiserfs rw,noatime,nodiratime,user_xattr,notail 0 0
/dev/mapper/idevol-isos /mnt/idevol/isos reiserfs rw,noatime,nodiratime,user_xattr,notail 0 0
/dev/mapper/idevol-vps_backup /mnt/idevol/vps_backup xfs rw,noatime,nodiratime,attr2,noquota 0 0
/dev/mapper/idevol-myth /mnt/idevol/myth reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-music /mnt/idevol/music reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-record /mnt/idevol/record reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-videos /mnt/idevol/videos reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-pictures /mnt/idevol/pictures reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/raidvol-homes /srv/nfs4/homes reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-vmware /srv/nfs4/vmware reiserfs rw,noatime,nodiratime,user_xattr,notail 0 0
/dev/mapper/idevol-isos /srv/nfs4/isos reiserfs rw,noatime,nodiratime,user_xattr,notail 0 0
/dev/mapper/idevol-temps /srv/nfs4/temps reiserfs rw,noatime,nodiratime,usrquota,grpquota,user_xattr 0 0
/dev/mapper/idevol-apt_cache /srv/nfs4/apt_cache reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-music /srv/nfs4/music reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-videos /srv/nfs4/videos reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-myth /srv/nfs4/mythtv reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-music /srv/nfs4/mythtv/music reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-videos /srv/nfs4/mythtv/videos reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-pictures /srv/nfs4/mythtv/pictures reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-record /srv/nfs4/mythtv/recordings reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-myth /var/lib/mythtv reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-music /var/lib/mythtv/music reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-videos /var/lib/mythtv/videos reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-pictures /var/lib/mythtv/pictures reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-record /var/lib/mythtv/recordings reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-apt_cache /var/cache/apt reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-mtdaapd /var/cache/mt-daapd reiserfs rw,relatime,user_xattr 0 0
/dev/mapper/idevol-eucalyptus /var/lib/eucalyptus xfs rw,noatime,nodiratime,attr2,noquota 0 0
/dev/mapper/idevol-eucalyptus /var/lib/image-store-proxy xfs rw,noatime,nodiratime,attr2,noquota 0 0
/dev/mapper/raidvol-netboot /mnt/raidvol/netboot/tftpboot/amd64/boot reiserfs rw,noatime,nodiratime,user_xattr 0 0
/dev/mapper/idevol-temps /tmp reiserfs rw,noatime,nodiratime,usrquota,grpquota,user_xattr 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw,relatime 0 0
nfsd /proc/fs/nfsd nfsd rw,relatime 0 0

```

---

### Post by RedRat on 2011-04-03
Hey, I like this guy. He has guts!!! He will keep the Forum busy for weeks if not months.

Clean install only way to go.

---

### Post by dannysauer on 2011-04-04
> **RedRat said:**
> Hey, I like this guy. He has guts!!! He will keep the Forum busy for weeks if not months.

Clean install only way to go.

I figured it'd be a hassle to reconfigure, or a hassle to do this.  And someone told me I couldn't do this, so, since I'm all about proving that nothing's impossible... ;)

But I've been working with Linux for over 15 years; it's been my job for most of those years.  Noobs - you just ignore the links above.  This process is **not** for the faint of heart. :D  Clean Install really is FTW.

---

