---
title: "Virtualbox &amp; GParted"
date: 2012-04-06
forum: General Help
---

### Post by asearle on 2012-04-06
I am trying to resize a Virtualbox Virtual Machine and am following the following instructions ...

[http://www.modhul.com/2008/10/21/re-sizing-a-virtualbox-virtual-disk-image-file/](http://www.modhul.com/2008/10/21/re-sizing-a-virtualbox-virtual-disk-image-file/)

... which seem to be very clear.

Part of the resizing is done by using GParted (as attached ISO image in the Virtualbox VM) to copy the smaller partition to the larger (new) partition.

However, when I tried to paste the partition into it's new location this operation failed with GParted telling me that it could not read my NTFS partition because the following programme was missing ...

ntfsprog / ntfs-3g

Can anyone help me with this?

Can I fix/adjust GParted to carry out the copy-paste operation correctly?

Or does anyone else have other instructions/methods for enlarging a Virtualbox disk?

Any help with this would be greatly appreciated.

Regards and many thanks,
Alan Searle

---

### Post by Paddy Landau on 2012-04-06
> **asearle said:**
> ... the following programme was missing ...

ntfsprog / ntfs-3g
Open Ubuntu Software Centre and install [FONT=Lucida Console]ntfsprogs[/FONT] and [FONT=Lucida Console]ntfs-3g[/FONT].

---

### Post by wildmanne39 on 2012-04-06
Hi, when you create disks in virtualbox in the future if you choose dynamic disk and make the partition large it will only take up the space that is actually installed but as you add more packages it will grow until it reaches the size that you made the partition.
Thanks

---

### Post by Mark Phelps on 2012-04-06
Last time I tried to install ntfs-3g in 11.10, it told me that it conflicted with ntyfsprogs -- and I had to remove this.

Don't know if that's till the case (it's been a while), but if given a choice between the two, I would choose ntfs-3g.

---

### Post by Morbius1 on 2012-04-06
You are correct sir. From synaptic when you try to install ntfsprogs in a system that already has ntfs-3g installed:

---

### Post by asearle on 2012-04-07
Hi Everyone,

I managed to work out this problem:

It wasn't an issue with Gparted but rather with my NTFS partition.  Yes, the partition had some corrupted sectors so I needed to run chkdsk /f  (including the /f flag).  That fixed the problem and then Gparted stopped complaining.  Bravo to Gparted for picking this up.

Then I found even better instructions for resizing a VirtualBox drive ...

[http://myotragusbalearicus.wordpress.com/2011/10/03/how-to-resize-a-disk-in-virtualbox-4-1-ubuntu-hostwindows-xp-guest/](http://myotragusbalearicus.wordpress.com/2011/10/03/how-to-resize-a-disk-in-virtualbox-4-1-ubuntu-hostwindows-xp-guest/)

... which included information about a simple resizing tool provided by VirtualBox.  Bravo to VirtualBox!

Once the drive is resized under VirtualBox all you do is boot the drive with the Gparted ISO attached as a virtual CD and use GParted to expand the partition.

Many thanks to those providing the tutorials.

Regards,
Alan Searle

---

### Post by Paddy Landau on 2012-04-07
> **asearle said:**
> Then I found even better instructions for resizing a VirtualBox drive ...

[http://myotragusbalearicus.wordpress.com/2011/10/03/how-to-resize-a-disk-in-virtualbox-4-1-ubuntu-hostwindows-xp-guest/](http://myotragusbalearicus.wordpress.com/2011/10/03/how-to-resize-a-disk-in-virtualbox-4-1-ubuntu-hostwindows-xp-guest/)
Thank you for posting the link.

---

### Post by Morbius1 on 2012-04-07
I went through that link and there is one mistake in it although it doesn't detract from the howto itself:
> Now, in the newer version of VirtualBox we have no “Create new virtual disk” option in the virtual device manager.That is not the case and it does provide an alternative to resizing the existing disk - just create a second disk:

Select the guest in VBox and go to Settings > Storage > Click on the "+" at the bottom of the list > Add Hard Disk > Create New Disk. The guest will see it as a new physical HDD so it will have to be formatted and partitioned as necessary.

---

