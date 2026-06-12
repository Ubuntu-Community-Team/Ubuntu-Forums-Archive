---
title: "What is the latest kernel for Karmic?"
date: 2010-05-22
forum: General Help
---

### Post by StuartN on 2010-05-22
Can anyone reccomend which is the safest, most stable mainline kernel for Karmic (from [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D)?](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D)?)

I recently applied kernel 2.6.34 Lucid to fix Ubuntu 10.04 with the freezing issue ([http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)) and it seems absolutely stable and successful.

Now I want to do the same with identical hardware running Ubuntu 9.10 Karmic, but there is not an obviously named version of the kernel as there is for 10.04 Lucid - they all seem to be release candidates, and some have incomplete directories.

---

### Post by inameiname on 2010-05-22
Perhaps check:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

You can download the deb files and install and get the latest Karmic kernel that way.

Or perhaps download kernelcheck and have it compile and install the latest one too.

---

### Post by StuartN on 2010-05-22
> **inameiname said:**
> Perhaps check:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Yes, obviously I have done so and there is not a 2.6.33 (or later) kernel labeled Karmic other than release candidates.

Can anyone recommend a kernel for Ubuntu 9.10 Karmic - perhaps v2.6.33 dated 25-Feb-2010 or v2.6.34-rc3-karmic dated 31-Mar-2010?

EDIT: Actually v2.6.34-rc3-karmic is missing the linux-image files and the architecture headers, while v2.6.34-rc2-karmic dated 06-Apr-2010 looks complete.

---

### Post by StuartN on 2010-05-22
> **StuartN said:**
> perhaps v2.6.33 dated 25-Feb-2010

Kernel 2.6.33 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/) works in Ubuntu 9.10 Karmic, all the 2.6.34 that were not incomplete failed to suspend.

---

