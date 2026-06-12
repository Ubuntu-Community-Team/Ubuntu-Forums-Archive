---
title: "Ubuntu guest in VMWare: Can it access ext3/ext4 drives?"
date: 2010-02-04
forum: General Help
---

### Post by bobtestact on 2010-02-04
I have a Windows7 box and I would like it to run Ubuntu under VMWare.

I also have several ext3 and ext4 drives that I would like to install in the box.

Will the Ubuntu guest be able to access those ext3/ext4 drives?

Clearly, Windows7 will not be able to access the files on those drives, since Windows7 doesn't support ext3/ext4.  But will the Ubuntu guest be able to access the files on those drives?

Would it make a difference if I used Virtualbox instead of VMWare?

---

### Post by snowpine on 2010-02-04
Your question is a little unclear. Are these external USB hard drives? If so, you need the PUEL (non-free) version from the VirtualBox website, in which case, yes, you should be able to access ext3/4.

---

### Post by bobtestact on 2010-02-04
The ext3/ext4 drives are all SATA internal drives.

---

### Post by SecretCode on 2010-02-05
With USB devices you could have assigned the USB to the vm guest.

If they were partitions that the host OS could read, you could have used vmware/vbox shared folders.

But in your case I think you will have to use a 'physical' or 'raw' disk. Both vmware and virtualbox support this, and it works well for data partitions (booting from such partitions is also possible but there's more to consider). However, I have not done this myself. Search the web for 'vmware raw disk' or similar terms (look up virtualbox as well if you are interested in it).

---

