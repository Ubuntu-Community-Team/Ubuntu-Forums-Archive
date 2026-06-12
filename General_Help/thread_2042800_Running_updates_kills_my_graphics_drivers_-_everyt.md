---
title: "Running updates kills my graphics drivers - everytime!"
date: 2012-08-15
forum: General Help
---

### Post by pdr2esmolbra on 2012-08-15
Hello there, 

I am having trouble with compatibility between the automatic ubuntu updates and my graphics drivers.  Every single time (this is my 3rd consecutive time) I run the updates, I reboot my machine to find either slow, bad icon-size/switcher-screwed-up desktops or today a completely unfunctional X-org system.

I have installed the proprietary drivers of my grahics card:  ATI Cedar Pro, Radeon HP 5450 through the catalyst application from AMD.  Everytime my graphics go bad I just re-run the graphics installer and everything starts working again.

What should I do to solve this problem? IS there a specific type of update I shouldn't get? I cannot do without the catalyst centre because without it all the desktop effects and some openGL stuff don't really run properly.

Help! I don't want to have to run the catalyst installer everytime I run apt-get update!

Thanks everyone, 

Pedro

---

### Post by wheeze on 2012-08-15
Since I've never used the ATI drivers, my comp uses nVidia video, take this with a teaspoon of sugar :D I'm guessing the ATI drivers use kernel modules like nVidia does.

Do you have dkms installed? If not you should give that a try. It will rebuild kernel modules automatically when you upgrade the kernel. Not sure it that's part of the problems you're having, but it couldn't hurt.

---

### Post by QIII on 2012-08-15
If you are installing from the AMD website using the .run file and the wizard this is expected behavior.

If you install from the repo this will not occur.

---

### Post by Wim Sturkenboom on 2012-08-15
> **pdr2esmolbra said:**
> What should I do to solve this problem? IS there a specific type of update I shouldn't get? I cannot do without the catalyst centre because without it all the desktop effects and some openGL stuff don't really run properly.
Don't upgrade the kernel ;) Although it would be silly not to do so.

> **pdr2esmolbra said:**
> I don't want to have to run the catalyst installer everytime I run apt-get update!
A small price to pay to have a working system :D I know your apin as I go through the same one with a nVidia card. Nor nouveau nor the recommended driver work properly, so I have to use a driver from the nVidia site.

---

### Post by pdr2esmolbra on 2012-08-21
> **QIII said:**
> If you are installing from the AMD website using the .run file and the wizard this is expected behavior.

If you install from the repo this will not occur.


Thanks everyone for their answers!

I have installed DKMS, sounds like should help, I shall let you know!

@ QIII : <noobie question warning!> how do I install from 'repo'? I went to the AMD's website and all I found were various versions of the *.run installer... any names of packages you know I should install by hand (cmd or synaptic?)

I'll risk updating again just to see what happens and will post results...


Cheers, 
Pdp

---

### Post by efflandt on 2012-08-21
If you installed 12.04 on that system, it should have automatically installed ATI video drivers for Radeon HD video, or at least it did for my tablet PC (the only computer I have with non-legacy ATI graphics).  Otherwise you would use **Additional Drivers** in Ubuntu to look for hardware drivers, which would usually recommend a suitable package.  That would have kept any video updates coordinated with kernel updates.

Manually running a script to install video drivers made automatic updates of video drivers dysfunctional.  Not sure how to fix that short of reinstalling Ubuntu.

---

### Post by QIII on 2012-08-21
To avoid common problems, recommend using the "Using the Ubuntu repositories (alternate command line method)" section of the ATI driver wiki in my signature.

---

### Post by Wim Sturkenboom on 2012-08-22
> **QIII said:**
> To avoid common problems, recommend using the "Using the Ubuntu repositories (alternate command line method)" section of the ATI driver wiki in my signature.The problem is that they might not work. Not sure for ATI, but I never managed to get the nVidia drivers from the repo working with a 8400GS card. So sometimes we're forced to use stuff outside the repository.

---

### Post by mcduck on 2012-08-22
> **Wim Sturkenboom said:**
> The problem is that they might not work. Not sure for ATI, but I never managed to get the nVidia drivers from the repo working with a 8400GS card. So sometimes we're forced to use stuff outside the repository.

In that case the only solution is to reinstall the third-party driver after every kernel update.

Both AMD and nVidia driver installers build a kernel module specific to the kernel version you are runing at the moment. Using the drivers from Ubuntu's repositories would automatically update that as well when necessary, but of course there's no way to do that f you are using graphics drivers not from the repositories so you need to do it yourself.

(anyway, if you install the updates regulary then every update definitely shouldn't cause you any troubles, only the kernel updates should do that...)

---

### Post by Linuxisfast on 2012-08-22
Actually building a precise package as directed in ccchtml works fine with dkms but bear in mind, new ATI 12.8 has many issues with kernels and dual graphic laptops so be prepared to boot into black, for now best method is command line install via repos, later on when they update the xswat repos, add the ppa, if you need it now, add the xorg-edgers ppa which has matching kernel for the driver.

---

### Post by pdr2esmolbra on 2012-08-24
Thanks everyone for their input!

So I updated 12.04 yesterday, in what didn't even include a new kernel but simply some updates to OpenGL drivers and the graphics broke down again!

The DKMS patch didn't work.

Then I looked for ATI packages in synaptic and turns out I was missing the fglrx package. ( the *.run wouldn't work if fglrx was installed which is why I uninstalled it on the first place) I installed it and everything seemed to be working except for one problem: I couldn't get 2 screens to work!  The specific bug relates to the maximum size of the virtual screen. When I tried to activate two screens an error would come up: "CRTC 148 is outside allowed position limit: pos= (my_numbers)... max  (1920, 1920). Two screens at 800x600 did work  :) but nothing else higher resolution.

SO! For some bizarre reason these problem was not present in the 'catalyst' gui that comes once you install the *.run form AMD. I activated the two screens from there and voila! everything working!

I have yet to try the "Using the Ubuntu repositories (alternate command line method)" which I will do in the next update if I have any more problems. I will keep you updated!

Thanks a lot for your support!
Pedro

---

