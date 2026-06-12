---
title: "mkisofs / genisoimage help"
date: 2009-10-05
forum: General Help
---

### Post by morpheus063 on 2009-10-05
Hi All, 

I am trying to follow the following URL for making a live CD/DVD from harddisk installation

```
http://ubuntuforums.org/showthread.php?t=688872
```However, at step E.1. (Build the CD/DVD), when I issue the following command:
```

sudo mkisofs -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -V "Custom Live CD" -cache-inodes -r -J -l -o ~/live-cd.iso $CD
```I am getting the following error:

```
linux ~ # sudo mkisofs -b boot/grub/stage2_eltorito \
> -no-emul-boot -boot-load-size 4 -boot-info-table \
> -V "Custom Live CD" -cache-inodes -r -J -l \
> -o ~/live-cd.iso $CD
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...

Use genisoimage -help
to get a list of valid options.

Report problems to debburn-devel@lists.alioth.debian.org.
linux ~ #
```I am stuck up - kindly guide me 

Thanks

---

### Post by loneowais on 2009-11-27
I'm stuck at the same step too. The last step](*,)](*,)](*,)](*,)](*,)

---

### Post by stunder on 2010-02-15
I found this answer on another forum here.
[URL="http://www.linuxforums.org/forum/misc/120970-mkisofs-issue.html"]
http://www.linuxforums.org/forum/misc/120970-mkisofs-issue.html[/URL]

Pretty much the guy just adds a . at the end of his string to specify the current directory.  It worked for me too.

---

