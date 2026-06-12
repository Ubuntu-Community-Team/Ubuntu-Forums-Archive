---
title: "Update causes extra copies of Ubuntu in Grub"
date: 2010-03-05
forum: General Help
---

### Post by DomesDKG on 2010-03-05
Sorry if this is already out there, I searched but couldn't find it.

Almost every time I update Ubuntu, it adds another two lines in grub for the new version, and a recovery option.  Is there any way to get rid of the boot options for the old versions?  I've tried updating /boot/grub/grub.cfg but it says it's read only.

My grub looks like this:
2.6.31-20
2.6.31-20 (Recovery)
2.6.31-19
2.6.31-19 (Recovery)
2.6.31-17
2.6.31-17 (Recovery)
2.6.31-14
2.6.31-14 (Recovery)
win7

But I only want to boot 2.6.31-20 and Win7.

---

### Post by northrup on 2010-03-05
The GRUB installer does that automatically, in case you still want to use the old kernels for some reason.  If you don't want those ones to show up, edit grub.cfg or menu.lst (depending on which GRUB you have) and remove the menu entries for those extraneous kernels.  Refer to the GRUB documentation (Google for it, it shouldn't be hard to find) to make sure you delete the right things.

You probably could even delete the old kernels themselves.  Personally, I don't do this, in case one breaks completely (which has happened to me), but if you're sure you don't want them ever again, there are likely guides in the Ubuntu documentation regarding a safe way to do this and what file(s) you have to delete.

---

### Post by 2hot6ft2 on 2010-03-05
> **northrup said:**
> edit grub.cfg or menu.lst
You probably could even delete the old kernels themselves.
You don't edit grub.cfg and there is no menu.list in grub2 see the link in my sig for more info on grub2.

It's generally a good idea to keep the 2 most recent kernels. The others can be removed in synaptic by searching for 

2.6.31-17
and
2.6.31-14
and marking them for complete removal. It will update grub on its own for you.
There are 2 that need removing for each one is image and the other is header.

Or you can do it in a terminal in one line
Applications > Accessories > Terminal
using
```
sudo apt-get remove linux-image-2.6.31-17-generic linux-headers-2.6.31-17 linux-image-2.6.31-14-generic linux-headers-2.6.31-14 

```
Just copy and paste it in and hit enter.

That will make your grub like this
> 2.6.31-20
2.6.31-20 (Recovery)
2.6.31-19
2.6.31-19 (Recovery)
win7
It's really a good idea to kep 2 kernels but if you're determined to just keep 1 then use this (just don't whine if you can't boot sometime because you don't have a backup kernel to fall back to).
```
sudo apt-get remove linux-image-2.6.31-17-generic linux-headers-2.6.31-17 linux-image-2.6.31-14-generic linux-headers-2.6.31-14 linux-image-2.6.31-19-generic linux-headers-2.6.31-19

```
That will make your grub like this
> 2.6.31-20
2.6.31-20 (Recovery)
win7 

---

### Post by hhh on 2010-03-05
Just to elaborate on 2hot6ft2's reply,

The way I remove old kernels in Ubuntu Karmic is...

1) Open Synaptic and Quick search "linux", then click the "Package" tab to put them in alphabetical order.
2) Scroll down to "linux-headers-[version number]" and see which ones are marked green. I currently have 2.6.31-19 and 2.6.31-20 installed (most recent 2, as recommended by many).
3) If I wanted to remove 2.6.31-19 I'd mark 3 packages for complete removal, the 2 header packages (linux-headers-2.6.31-19 and linux-headers-2.6.31-19-generic) and then I'd scroll down to linux-image-2.6.31-19-generic and mark that for complete removal as well.
4) After clicking "Apply" the kernel will be removed and grub2 will update automatically.

Just make sure NOT to remove anything without a version number in the actual package name, meaning linux-generic and linux-headers-generic.

-Edit- DO NOT EDIT grub.cfg !!!! If anything, edit /etc/default/grub . See the Wiki for more info...
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by DomesDKG on 2010-03-10
Synaptic Package manager did the trick.  One question though, you mention grub2, I'm running grub 1.9, how do I update?

---

### Post by eriktheblu on 2010-03-10
Grub 2 is default for Karmic. If you're not using Karmic, probably best to stick with the Grub you have.

---

