---
title: "Is it possible to run another live cd from ubuntu?"
date: 2010-12-16
forum: General Help
---

### Post by wah fun on 2010-12-16
I am new to linux and even though I am pleased with ubuntu 10.04, I would like to try other distro's without having to burn cd's and boot from them. I was able to do this with a program called MobaliveCD from Windows. Is there an equivalent program for linux? Google search hasn't turned up anything.

thx

---

### Post by Megaptera on 2010-12-16
I think Virtualbox might be what you're looking for?

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by wah fun on 2010-12-16
thx. I know this works but was trying to avoid having to install another program.

For example, MobaliveCD required to intallation. Just open it, click on the iso file and voila, the image runs! I have found numerous ways to mount the iso image but that just displays the files, you can actually run the iso - which is what I want to do.

I will keep looking.

---

### Post by Megaptera on 2010-12-16
Sorry 'bout that, happy hunting.

---

### Post by K.J. on 2010-12-16
VirtualBox is definitely what you're looking for. It's not much to install. Otherwise, the only thing you could do is dd the iso to a thumb drive and boot from that.

---

### Post by oldfred on 2010-12-16
You can use grub2 to loop mount an ISO directly from the harddrive. Do know a way to run it from Ubuntu.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by Megaptera on 2010-12-17
oldfred, thanks - as ever great info from you!

---

### Post by ronnielsen1 on 2010-12-17
> I know this works but was trying to avoid having to install another program.

Why? Are you out of hard drive space or are you worried that your computer will slow down?

---

