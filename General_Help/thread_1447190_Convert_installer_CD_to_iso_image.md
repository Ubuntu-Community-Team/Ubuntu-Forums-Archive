---
title: "Convert installer CD to iso image"
date: 2010-04-05
forum: General Help
---

### Post by satimis on 2010-04-05
Hi folks,

What will be the easiest way converting Vista installer CD to iso image?  I'll use the image to install VM on VirtualBox.  Google found me many suggestion.

TIA

B.R.
satimis

---

### Post by john newbuntu on 2010-04-05
On Karmic, you should be able to pop in the CD, right click the CD icon on the desktop and select copy.  You then would change the destination to an image and the type to ISO9660, giving it a suitable file name.
If you choose CLI, genisoimage and readom are two options. Please refer the man page for more details.
On WinXP/Vista, you could install isorecorder.

If you have the CD with you, I am guessing virtualbox can read it directly(perhaps you may need some extensions)

---

### Post by satimis on 2010-04-05
> **john newbuntu said:**
> On Karmic, you should be able to pop in the CD, right click the CD icon on the desktop and select copy.  You then would change the destination to an image and the type to ISO9660, giving it a suitable file name.
If you choose CLI, genisoimage and readom are two options. Please refer the man page for more details.
On WinXP/Vista, you could install isorecorder.

Hi john,

Thanks for your advice.

I got it done with the basic command on console

# dd=/dev/sr0 of=/path/to/iso.image

simple and straight forward.  I almost forgot this command.


> 
If you have the CD with you, I am guessing virtualbox can read it directly(perhaps you may need some extensions)

That is my problem here after upgrade to virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_amd64.deb

First vboxdrv can't be detected.  Now VBox can't read CD/DVD. Previously it worked seamlessly.

B.R.
satimis

---

