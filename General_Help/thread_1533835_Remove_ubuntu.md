---
title: "Remove ubuntu"
date: 2010-07-18
forum: General Help
---

### Post by kawakaze on 2010-07-18
First of all I better point out that im not selling out to windows. Our kid has had our old laptop and wants windows on it (terrible i know). The problem is ubuntu somehow has got a foothold on the harddisk, the windows installer cant even see the disk. I tried to partition it as NTFS in the liveCD but it wouldnt let me continue without installing ubuntu again, so I have been going in circles. Please help, thanks.

---

### Post by bumanie on 2010-07-18
Use the specific [gparted live cd]("http://gparted.sourceforge.net/livecd.php") - it will have more options than the one on the ubuntu live cd. That should work, if not post back and there are other ways to do it, but gparted is probably the easiest if you want a gui program.

---

### Post by lmarmisa on 2010-07-18
Boot your system from a Ubuntu Live CD.

Open System -> Administration -> GParted and define one NTFS partition in your hard drive.

Open a terminal and type:

```

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```I suppose that your hard drive is in /dev/sda. Change this device if neccesary.

Check if you are able to install Windows after these changes.

---

### Post by -kg- on 2010-07-18
The GParted Live CD will do it, but GParted on the Ubuntu Live CD should work for this, as well.  Sounds like you tried to do it through the installer.

In order to use the Live CD, you need to go not through the installer, but boot to the Live CD desktop, then click on "System/Administration/GParted" from the desktop.  From there, you can delete the Ubuntu partitions and the Windows installer should be able to go from there.

You don't need to create a Windows partition under GParted.  All you need to do is delete the Ubuntu partitions and the Windows installer will create its own partition in the free space.

<Edit>  Of course, if you want both on it, things get a bit more complicated.  You will need to resize the root (or /home, if you have one) partition to give free space to Windows to install.

The Windows installer will take over the MBR, of course, being installed after Ubuntu.  You will have to reinstall GRUB in the MBR afterwards.

---

### Post by lmarmisa on 2010-07-18
> **-kg- said:**
> The GParted Live CD will do it, but GParted on the Ubuntu Live CD should work for this, as well.  Sounds like you tried to do it through the installer.

In order to use the Live CD, you need to go not through the installer, but boot to the Live CD desktop, then click on "System/Administration/GParted" from the desktop.  From there, you can delete the Ubuntu partitions and the Windows installer should be able to go from there.

You don't need to create a Windows partition under GParted.  All you need to do is delete the Ubuntu partitions and the Windows installer will create its own partition in the free space.

Some Windows CD installers (for example, XP Pro with SP2) do not recognize the hard drive if its MBR is not written with 100% Microsoft info. So, I recommend to update the MBR loader with the command:

> 
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda


---

