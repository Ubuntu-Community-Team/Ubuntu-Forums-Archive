---
title: "Unable to mount windows shares"
date: 2010-12-09
forum: General Help
---

### Post by bcyork on 2010-12-09
Ubuntu v10.10 on laptop dual boot with windows 7

Hi, 
I have installed Ubuntu on my laptop for the first time. I used slackware for several years back around version 8 - 10. At any rate I tried the live CD and everything worked great. Now once it is installed I can't mount windows shares either through Nautilus, fstab or mount command. Natulus tells me it can't find it and mount gives me this 

"mount: wrong fs type, bad option, bad superblock on //by-desktop1/2010$,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

I can ping the machine's ipaddress with the shares and I even tried switching back to windows on the laptop to see if I could access the shares via windows which worked. I'm not sure why they now won't mount once ubuntu is installed any ideas?

Thanks

---

### Post by bcyork on 2010-12-09
Figured it out. 

$sudo apt-get install smbfs

also installed nfs-common

---

