---
title: "Download Ubuntu ati-drivers?"
date: 2010-08-30
forum: General Help
---

### Post by AudioDef on 2010-08-30
Is it possible to download the open-source ati-drivers that Ubuntu uses  for the Radeon X300? Ubuntu allows this card to work for me, but Ubuntu  isn't the only Linux distro I use for this card. I figure someone must  have patched these drivers and I'd like to take a look at them.

---

### Post by lukeiamyourfather on 2010-08-30
The drivers in Ubuntu are packaged for Ubuntu and might not work like you want them to in other distributions. What distribution are you using that doesn't already have drivers for your ATI card?

---

### Post by bdentremont on 2010-08-30
Some more information from a fellow X300 user:

I believe that default support for the X300 in Ubuntu comes from the kernel module "Radeon", the source code for which comes from x.org. This source code is the generic option for any linux distro that you are asking for, but as you can see from the compile instructions is not trivial to install from this form.

[http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)

ATI has also released closed-source Linux drivers for this card in the past (see "flgrx" or "Catalyst") which you can find on ATI's website.  However, these are incompatible with the current X server, so if you are using a recent Linux distro, within the last year or two, including Ubuntu, **this download probably won't help you at all**.  The following links are a discussion of this issue.  See red warning box in the cchtml.com page.

[http://ubuntuforums.org/showthread.php?t=1523014&page=2](http://ubuntuforums.org/showthread.php?t=1523014&page=2)
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

In short, I agree with lukeiamyourfather that you probably should be looking for support from your distro, rather than a download.

---

