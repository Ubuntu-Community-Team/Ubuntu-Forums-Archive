---
title: "How to install Ubuntu on Revo 3610"
date: 2010-02-15
forum: General Help
---

### Post by Kwaka on 2010-02-15
Hi.
I have seen the a thread on the Revo 3610 but I wanted to ask some newbie questions not mentioned in there.
I hope this is the right place.

I have just bought an Acer Revo 3610 which comes with Linpus on it. I want to replace that with Ubuntu but I'm unsure exactly which distro I should use to get the 64bit version.
I realise that I need to get the distro on a USB stick and boot from that, but I'm unsure what I then need to do to overwrite the existing Linpus install.
Any advice gratefully received!
Thanks.

---

### Post by jamesisin on 2010-02-15
When you run the installation CD (via USB stick of necessary) there will be a section for choosing appropriate partitioning.  If you are seeking to *replace* the current OS you will want to choose to use the entire hard drive and over-write those contents.

As to versioning, you may need either the Alternate installer or even the Netbook Remix depending upon hardware support for your specific machine (with which I am unfamiliar), but you can get the 64bit regular version and see where that takes you first.

---

### Post by Kwaka on 2010-02-16
> **jamesisin said:**
> When you run the installation CD (via USB stick of necessary) there will be a section for choosing appropriate partitioning.  If you are seeking to *replace* the current OS you will want to choose to use the entire hard drive and over-write those contents.

As to versioning, you may need either the Alternate installer or even the Netbook Remix depending upon hardware support for your specific machine (with which I am unfamiliar), but you can get the 64bit regular version and see where that takes you first.
Thanks.
The bit I'm confused about is what is the 64 bit version? As IntelX86 is listed and AMD64. I want 64bit Intel as my nettop is a dual core Atom.

---

### Post by 3rdalbum on 2010-02-16
> **Kwaka said:**
> Thanks.
The bit I'm confused about is what is the 64 bit version? As IntelX86 is listed and AMD64. I want 64bit Intel as my nettop is a dual core Atom.

AMD64 will also work on Intel 64-bit processors (Intel's processors understand the AMD64 instruction set). It's probably not worth using the 64-bit edition on an Atom though - 64-bit is mainly important for computers with 4 GiB of RAM or more, and Atom CPUs can only address 2 GiB. You may get slightly faster performance on 64-bit if you're gaming or doing video/3D-intensive work, but then I doubt you'd be doing that on an Atom.

---

### Post by Kevbert on 2010-02-24
The R3610 will work with both 9.04 and 9.10 (AMD)64 bit just fine. You may have speed problems if you run Windows 64bit, but Linux runs well (and out of the box in most cases). If you don't have a CDROM drive with it you'll need to install via a USB flash drive.

---

### Post by timgood on 2010-02-24
I have Ubuntu 9.10 64bit installed on my Revo 3610 and it works very well. You can create a bootable USB key by booting the Ubuntu Desktop CD and then going to System/Administration/USB Startup Disk Creator.

Once the key is made, fire up the Revo (you must disable Boot to Linpus in the Bios) with the key inserted and install Ubuntu in the usual way.

You can get a 1Gb memory upgrade for less than £20, so if you are thinking of using it as a media server/streamer, this is well worth it.

Hope this helps.

---

### Post by Kevbert on 2010-02-24
Please take a look at [[COLOR="Red"]my thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1379320") on the R3610. When you boot up you may need to press F12 in order to temporarily set the boot device.

---

