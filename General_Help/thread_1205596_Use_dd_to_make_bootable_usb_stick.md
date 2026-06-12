---
title: "Use dd to make bootable usb stick?"
date: 2009-07-06
forum: General Help
---

### Post by t0p on 2009-07-06
Can I make a bootable usb stick by using dd to transfer an .iso image to the stick?  Can someone help me with the syntax of the command, if the image is at /home/user/image.iso and the stick is at /media/sdb? (or is it /dev/sdb?  Heck, look! I don't even know what I'm talking about!)

What else would I need to do to make this bootable stick? ie use gparted to set the 'boot' flag?

---

### Post by nothingspecial on 2009-07-06
Personally I`d use unetbootin

I`ve only ever made bootable sticks with dd using .img files (Moblin and Arch)

Something like dd if=/path/to/.img of=/path/to/usb/stick/

I know you have to umount it first.

Other than that I don`t really know what I`m talking about either.

---

### Post by Mighty_Joe on 2009-07-06
I don't think it's that easy.  Have a look at the various tutorials on [pendrivelinux]("http://www.pendrivelinux.com/") or the [Ubuntu Community Documentation]("https://help.ubuntu.com/community/Installation/FromUSBStick").  
[This topic]("http://ubuntuforums.org/showthread.php?t=1193680") is a pretty good summary of all the ways to install Ubuntu on a flash drive (including my personal favorite).

---

### Post by whole.grains on 2009-07-06
You may already be aware of this, but 9.04 has this feature built-in. System >Administration>USB Startup Disk Creator

---

### Post by t0p on 2009-07-06
Oh, I know all about UNetbootin, pendrivelinux and the start-up usb maker in jaunty.  But I was reading about the old hack of putting OSX onto a pc with dd, and wondered if it would work for linux on a stick.  The gui-based solutions are all well and good, but dd is a good honest command-line utility, as old as unix I expect, and I like using the "traditional" methods every now and then.  Also I've got a dog called DD (an American bulldog, she's a real sweetheart!  Look at the attachment!)

So is that the consensus?  dd won't do it?  She'll be most distressed to hear this!  Please, someone give my mutt some hope!!

---

