---
title: "A questions from an Ubuntu newbie"
date: 2006-03-01
forum: General Help
---

### Post by flarkit on 2006-03-01
Hi

I installed 5.10 today and got it to dual-boot with Win XP Pro, with XP on my primary 120Gb and Ubuntu on my 60Gb slave. I had to reinstall, due to my hope that I could set up GRUB on the 60Gb and add an entry to XP's boot menu. It wouldn't boot, so I resorted to reinstalling and loading GRUB on the primary's MBR.

Now the following issues are baffling me:

1) How do I improve the bootup speed and overall responsiveness of the OS? I'm sure the default installation runs unnecessary tests and drivers, causing it to take longer to boot than necessary. Once logged in, the basic applications just feel quite sluggish, compared to the WinXP installation.

2) How do I automount my NTFS and FAT32 partitions? I'd like to be able to access my music and data files from Ubuntu.

3) Is it necessary to install NVidia's Linux drivers for OpenGL to work on my PCI-e 6800GT? Also, what's the easiest way to check that the card is indeed handling the 3D functions?

Those are the first mysteries that I've found so far.

Thanks!

---

### Post by kaamos on 2006-03-01
1) You could try [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

2) [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs) (the guide is for 5.04, but most of the stuff works fine in 5.10)

3) open a terminal (Applications->Accessories->Terminal) and type
```
glxgears -printfps
```
a score of over 1000 would mean that you have 3d acceleration. You can also check the output of "glxinfo"

---

### Post by Ramses de Norre on 2006-03-01
1) I haven't got that sluggish feeling, one thing I know: ```
gconf-editor /apps/metacity/general
``` and check the reduced_resources box.
Maybe there are other things I don't know about.

2) ```
/dev/hda1       /mnt/windowsk  vfat iocharset=utf8,umask=000 0 0
/dev/hda2       /media/windowsc  ntfs    nls=utf8,umask=0222 0       0

```
add similar lines to your /etc/fstab file. Change it to the right partition number and mountpoint. Partitions under /media show up on your desktop.

3) Sorry, I haven't used nvidia yet.

---

### Post by flarkit on 2006-03-01
Thanks for the info, kaamos and Ramses.

1) I foresee spending quite a bit of time researching the performance/responsiveness point

2) I should've remembered that, thanks!

3) I'll read the NVidia guide on these forums

:D

---

