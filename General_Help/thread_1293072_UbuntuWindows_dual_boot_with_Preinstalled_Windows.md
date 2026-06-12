---
title: "Ubuntu/Windows dual boot with Preinstalled Windows"
date: 2009-10-16
forum: General Help
---

### Post by delbooh on 2009-10-16
Is it possible to set up a dual boot if windows was preinstalled and I don't have any installation discs? Can I set up partitions after windows is already installed?

---

### Post by tpjk on 2009-10-16
> **delbooh said:**
> Is it possible to set up a dual boot if windows was preinstalled and I don't have any installation discs? Can I set up partitions after windows is already installed?

first of all - yes, you can partition your harddrive even after windows has already been installed. you can either do that during the installation of ubuntu or using the partition editor that comes with the ubuntu live cd. if you want to install ubuntu, you are going to need one of those (or, alternatively, a bootable usb stick). if you're planning to leave your windows installation alone you won't necessarily need a windows installation disk.

there are a lot of howtos and tutorials about dual booting windows and ubuntu; even though the ubuntu installation process is pretty straightforward in general i strongly suggest you do some reading before attempting to set up a dual boot. which version of windows are you running?

---

### Post by BQAggie2006 on 2009-10-16
Yes, it is possible to perform a dual-boot installation because you already have Windows installed and won't need a Windows installation CD.

Here are a few guides on how to perform a dual-boot:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/9.04/switching/dualboot.html](https://help.ubuntu.com/9.04/switching/dualboot.html)

If you aren't comfortable with either of those documents, try looking into Wubi for now. It will install Ubuntu on a virtual partition within Windows and then create a quasi-dual boot environment. If you don't like it or want to move to a true dual-boot, you can uninstall it through Windows Add/Remove Programs.

Another option would be to run Ubuntu within a VirtualBox virtual machine within Windows as well.

Let us know if you need help with any of these and if you have any more questions.

---

### Post by tpjk on 2009-10-16
here are some more links that should help get you started:

[http://members.iinet.net.au/~herman546/index.html]("http://members.iinet.net.au/%7Eherman546/index.html")

[http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu](http://gwos.org/udsf/doku.php/core:dualbooting:ubuntu)

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
(excellent site for ubuntu beginners! it's also got help on burning .iso-images which is what you'll have to do if you want to create your own live cd [instead of ordering it].)

---

### Post by delbooh on 2009-10-17
Thank you for the links, they are very helpful. There are a couple issues I'm still having though: I shrunk the windows partition using the disc manager in Vista, but it would only shrink to 256 GB (out of 350) even though it is a new computer with very little on it and I had defragged just prior. Not sure why it won't let me go smaller.  I wanted to make the Ubuntu partition the larger one since I plan to use it as my primary OS.

The other issue I'm having is during setup of Ubuntu. I wanted to install Ubuntu Studio (for AMD 64) but it doesn't seem to want to install into my unallocated space. It wants to install into the windows partition and when I manually change it, it says the unallocated space is unusable.

---

### Post by tpjk on 2009-10-17
> **delbooh said:**
> Thank you for the links, they are very helpful. There are a couple issues I'm still having though: I shrunk the windows partition using the disc manager in Vista, but it would only shrink to 256 GB (out of 350) even though it is a new computer with very little on it and I had defragged just prior. Not sure why it won't let me go smaller.  I wanted to make the Ubuntu partition the larger one since I plan to use it as my primary OS.

The other issue I'm having is during setup of Ubuntu. I wanted to install Ubuntu Studio (for AMD 64) but it doesn't seem to want to install into my unallocated space. It wants to install into the windows partition and when I manually change it, it says the unallocated space is unusable.


you don't have to use the disc manager in vista to shrink your vista partition - people usually recommend that over using the gnome partition editor because it's supposed to get the job done faster; just boot into your live cd, go to System -> Administration -> Partition Editor and shrink your windoze partition from there.

as far as installing ubuntu goes, it won't work unless you format your unallocated space to ext3 first. for that you can also use the partition editor.

---

### Post by tpjk on 2009-10-17
if you want to learn more about using the gnome partition editor and partitioning in general go here:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

and before i forget ;] ---> always backup your data.

---

### Post by oldfred on 2009-10-17
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

The following article by the How-To Geek contains useful information regarding resizing your Vista partition, and getting it to boot again.
Using GParted to Resize Your Windows Vista Partition 
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)


Just in case you want to reinstall the Vista boot I would have a copy of this:
Try this recovery CD
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
and from Microsoft for Vista but should work for Win 7 too.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

