---
title: "Problems making ISO with mkisofs"
date: 2011-01-20
forum: General Help
---

### Post by gramirez2012 on 2011-01-20
I have been following a guide to make my own custom install CD of Ubuntu. Everything has worked fine so far, up until making the ISO. As per the instructions, I used the following command:

```
$ cd ~/livecd/cd
$ sudo mkisofs -r -V "Ubuntu-Live-Custom" -b isolinux/isolinux.bin -c  isolinux/boot.cat -cache-inodes -J -l -no-emul-boot -boot-load-size 4  -boot-info-table -o ../custom.iso
```When I do this, it comes back with:

```
root@gil-EVO:~/livecd/cd# sudo mkisofs -r -V "Ubuntu-Live-Custom" -b isolinux/isolinux.bin -c isolinux/boot.cat -cache-inodes -J -l -no-emul-boot -boot-load-size 4 -boot-info-table -o ../custom.iso 
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...

Use genisoimage -help
to get a list of valid options.

Report problems to [EMAIL="debburn-devel@lists.alioth.debian.org"]debburn-devel@lists.alioth.debian.org[/EMAIL].
```

I took "Missing pathspec" to mean that it had a problem saving the file in that location. I tried saving it on the desktop and in other locations and got the same result. Any ideas?

Thanks

---

