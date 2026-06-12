---
title: "WOW.  Awesome.  And a few questions . . ."
date: 2010-01-21
forum: General Help
---

### Post by madmac63 on 2010-01-21
I've been switching between Windows and Ubuntu for a while now - I'd stick in Ubuntu until I hosed it up, and go back to Windows for a while, until I reinstalled the Ubuntu partitions.  

At any rate, I got hooked on Chrome, and I was never really wild about VMware on Debian/Ubuntu (downloading patch files from somewhere in the Czech republic???), and the Wireless support was a nuisance (now it's working fine out of the box), and my AT&T USBconnect Mercury Wireless Broadband adapter was another nuisance (works fine out of the box most of the time, sometimes it doesn't pick up DNS servers, still fiddling), so I ended up in Windows for a while . . . but now I needed a 64-bit platform, and Windows x64 is weak, so I gave 9.10 x64 a shot and WOW.  Awesome.

Everything works.  Almost.  I have a few quick questions/need suggestions.

1.  I need a filesystem for my VMs that is Read/Writeable whether I'm booted into Ubuntu or Windows (at least until I resolve the network throughput issues for VMs running on Ubuntu x64).  What do you suggest?  Is the NTFS support in Ubuntu safe for Writing?  Is there an EXT3 driver for Windows?

2.  Is there a quick HowTo on Grub2?  I just want to change the labels on the boot options, but I gather that now means I need to edit template files in directories, and so on, and I'd rather NOT become a Grub Guru and just follow a quick HowTo.

Kudos to the Ubuntu Development Community.  You guys rock!!!

Doug
[email]madmac63@gmail.com[/email]

---

### Post by dmillerct on 2010-01-21
> **madmac63 said:**
> I've been switching between Windows and Ubuntu for a while now - I'd stick in Ubuntu until I hosed it up, and go back to Windows for a while, until I reinstalled the Ubuntu partitions.  

At any rate, I got hooked on Chrome, and I was never really wild about VMware on Debian/Ubuntu (downloading patch files from somewhere in the Czech republic???), and the Wireless support was a nuisance (now it's working fine out of the box), and my AT&T USBconnect Mercury Wireless Broadband adapter was another nuisance (works fine out of the box most of the time, sometimes it doesn't pick up DNS servers, still fiddling), so I ended up in Windows for a while . . . but now I needed a 64-bit platform, and Windows x64 is weak, so I gave 9.10 x64 a shot and WOW.  Awesome.

Everything works.  Almost.  I have a few quick questions/need suggestions.

1.  I need a filesystem for my VMs that is Read/Writeable whether I'm booted into Ubuntu or Windows (at least until I resolve the network throughput issues for VMs running on Ubuntu x64).  What do you suggest?  Is the NTFS support in Ubuntu safe for Writing?  Is there an EXT3 driver for Windows?

2.  Is there a quick HowTo on Grub2?  I just want to change the labels on the boot options, but I gather that now means I need to edit template files in directories, and so on, and I'd rather NOT become a Grub Guru and just follow a quick HowTo.

Kudos to the Ubuntu Development Community.  You guys rock!!!

Doug
[email]madmac63@gmail.com[/email]

I'm from the Czech Republic. What are you trying to say about our files?

---

### Post by sisco311 on 2010-01-21
> **madmac63 said:**
> 
1.  I need a filesystem for my VMs that is Read/Writeable whether I'm booted into Ubuntu or Windows (at least until I resolve the network throughput issues for VMs running on Ubuntu x64).  What do you suggest?  Is the NTFS support in Ubuntu safe for Writing?  Is there an EXT3 driver for Windows?


NTFS 

There is an ex2 driver for Windows, but the NTFS driver for linux is much better.

> **madmac63 said:**
> 
2.  Is there a quick HowTo on Grub2?  I just want to change the labels on the boot options, but I gather that now means I need to edit template files in directories, and so on, and I'd rather NOT become a Grub Guru and just follow a quick HowTo.


[thread=1287602]**Grub 2 Title Tweaks**[/thread]
[uhelp]community/Grub2[/uhelp]
[thread=1195275]The Grub 2 Guide[/thread]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]

---

### Post by clhsharky on 2010-01-21
HI

Grub2
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I do not recommend any Linux distro to any one not willing learn a new way.

Sharky

---

