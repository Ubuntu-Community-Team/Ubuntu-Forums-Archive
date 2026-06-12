---
title: "Keyboard and mouse no response when chroot to Ubuntu 9.04"
date: 2009-10-16
forum: General Help
---

### Post by maytime on 2009-10-16
Dear all,

I am trying to remaster a liveCD. I met a curious problem and can not find a solution after googled around. My OS environment is Ubuntu 9.04 and I follow with [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

When I "chroot" to another Ubuntu 9.04(which was extracted from a Ubuntu-9.04-desktop-iso), and startx, my mouse and keyboard seems to be with no response (The OS did not hang however and I could make commands with console with ssh login). Because I need to make configurations with some GUI applications, I can't do that with only the console. So please give me some suggestions.

The concrete steps are as follows:
1.Copy the iso content to 'newiso'

[B]sudo mkdir oldiso newiso 
sudo mount ubuntu-9.04-desktop-i386.iso oldiso -o loop 
sudo cp -a oldiso/. newiso/
sudo umount oldiso  [/B]

2.extract the content from the iso

**sudo unsquashfs newiso/casper/filesystem.squashfs**

will generate a squashfs-root directory.

3.change to the chroot environment.

[B]sudo mount --bind /dev/ squashfs-root/dev
sudo chroot squashfs-root
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts

export HOME=/root
export LC_ALL=C[/B]

After that everything seemed OK. But when I startx, the mouse and keyboard seemed no response. I remember it was Ok when I did those steps with Ubuntu 8.04 months ago. So what should I do? Any suggestions would be much apreciated.

Thanks for your patient again!

---

