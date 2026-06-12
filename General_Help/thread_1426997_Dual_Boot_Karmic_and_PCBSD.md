---
title: "Dual Boot Karmic and PCBSD?"
date: 2010-03-11
forum: General Help
---

### Post by woodmaster on 2010-03-11
Ok. so I searched for this and got sent to documentation on PCBSD's forums that say I need to manually edit /boot/grub/menu.lst to get Grub to load BSD.  sudo update-grub didn't see BSD partition and there is no menu.lst???  Furthermore, I can't mount my BSD partition.  I get this error
```
Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
```
dmesg | tail
[14127.602295] You didn't specify the type of your ufs filesystem
[14127.602298] 
[14127.602299] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
[14127.602301] 
[14127.602302] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[14127.603749] ufs_read_super: bad magic number
[14637.434606] ufs was compiled with read-only support, can't be mounted as read-write
[14659.430753] ufs was compiled with read-only support, can't be mounted as read-write
[14673.102535] ufs was compiled with read-only support, can't be mounted as read-write
[15374.675222] ufs was compiled with read-only support, can't be mounted as read-write

```

So what gives?  What am I missing here?  I know this should be able to be done.  Using GRUB1.97 beta BTW(I refuse to call it 2.0 if it's not-IDK why it is commonly called that?)  Thank-you for any help.  I'd really like to try BSD.

---

