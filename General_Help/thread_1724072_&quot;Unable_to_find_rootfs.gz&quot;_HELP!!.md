---
title: "&quot;Unable to find: rootfs.gz&quot; HELP!!"
date: 2011-04-07
forum: General Help
---

### Post by linuxuser12345 on 2011-04-07
If any of you have been keeping up with my posts, I found a perfect OS for a little 2GB SSD netbook: SliTaz!

I just need a little help installing it... When I go and click "install", it checks the disks and everything, then an error message comes up, saying this: "Unable to find: rootfs.gz". I don't know what to do now. Can somebody help me??

---

### Post by ArielSonique on 2011-04-27
Hey,

I had the same issue while installing Slitaz. Are you trying to install to your harddrive from a USB (i.e. liveUSB?) If you notice, the Slitaz installer tries to search for rootfs.gz from /media/cdrom. You need to fool the installer and mount your usb as a cdrom. Boot the liveUSB. Go to Gparted. Make a note of what your USB key is called. Mine was /dev/sda (you can recognize it by the size. Mine was 4.0 GB)

Now boot up the Xterminal and login as root user by typing the following:
```
su
password: root 

```
Mount your USB on /media/cdrom with this command (as a root user):
```
mount /dev/sda /media/cdrom
```

The next time you start the installer, it will be able to locate the rootfs.gz file.

In this day and age, wasting plastic CDs to burn random linux distro images is completely unacceptable. I wish Slitaz and other distro creators realize this and don't make the end user jump through these sort of mounting hoops to install from USBs in future editions.

---

### Post by Rita G. on 2012-03-10
thank you ariel,

you made this fix very simple i needed this info for my garage computer.

---

