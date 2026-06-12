---
title: "How To Install Kernel Patch?"
date: 2010-10-13
forum: General Help
---

### Post by karmila on 2010-10-13
Hi All,

I need to install mainline kernel to make my notebook working and I have downloaded the kernel and patches from this link [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.36-rc7-maverick/")

The kernel is in deb format so that is no problem on installing. But how to apply the patches? I need assistance because this is my first time meet kernel patch.

Thanks.

---

### Post by karmila on 2010-10-13
Bump...

---

### Post by karmila on 2010-10-15
More bump :KS

---

### Post by Ayuthia on 2010-10-15
It looks like they have the linux-image and linux-header files built from that link.  I think all you need to do is install the two packages.  The linux-image usually contains the the compiled kernel and the kernel modules.  The linux-header usually contains the header files for compiling other kernel modules when needed.

---

### Post by karmila on 2010-10-15
> **Ayuthia said:**
> It looks like they have the linux-image and linux-header files built from that link.  I think all you need to do is install the two packages.  The linux-image usually contains the the compiled kernel and the kernel modules.  The linux-header usually contains the header files for compiling other kernel modules when needed.

Thank you, 

But how can I apply/install the patches too? Is it automatically installed or I still need do something manually?

---

### Post by Ayuthia on 2010-10-15
> **karmila said:**
> Thank you, 

But how can I apply/install the patches too? Is it automatically installed or I still need do something manually?

Since they provided the image and header, I am fairly confident that there is anything else left to do.  Once the linux-image has been built, you cannot patch it unless they provided the source.  I don't think that they would go through the trouble of compiling and packaging the kernel without patching it.

If you need more confirming, you might help let us know what notebook you have and what you are trying to fix.  And if you have the link that brought you to the .deb page, that would be helpful too.

---

### Post by psusi on 2010-10-15
What patches?

---

### Post by karmila on 2010-10-15
> **Ayuthia said:**
> Since they provided the image and header, I am fairly confident that there is anything else left to do.  Once the linux-image has been built, you cannot patch it unless they provided the source.  I don't think that they would go through the trouble of compiling and packaging the kernel without patching it.

If you need more confirming, you might help let us know what notebook you have and what you are trying to fix.  And if you have the link that brought you to the .deb page, that would be helpful too.

My notebook won't boot to X

Here is the link [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

@ #82 post.

---

### Post by karmila on 2010-10-15
> **psusi said:**
> What patches?

You can see at link on the 1st post. There is patches available with the kernel.

---

### Post by psusi on 2010-10-15
You need to get the source code, apply the patch, and compile the kernel.

---

### Post by Ayuthia on 2010-10-15
I looked at those patches and I am still thinking that the linux-image and linux-headers .deb files are all you need.  The patches that were in your link are not the actual patches that fix the kernel.  They update the .config file for the kernel and update some other files but they are actual fixes to the source.

You just need to grab the correct 32 or 64 bit version that you need and install them.

---

### Post by karmila on 2010-10-16
> **Ayuthia said:**
> I looked at those patches and I am still thinking that the linux-image and linux-headers .deb files are all you need.  The patches that were in your link are not the actual patches that fix the kernel.  They update the .config file for the kernel and update some other files but they are actual fixes to the source.

You just need to grab the correct 32 or 64 bit version that you need and install them.

OK, I'll go install them and report here for result. Thanks.

---

### Post by karmila on 2010-10-16
> **psusi said:**
> You need to get the source code, apply the patch, and compile the kernel.

If that so, it is out of my ability :(

---

### Post by karmila on 2010-10-16
Ayuthia, thanks. It works!

Haha, now my notebook singing Ubuntu again :guitar:

---

### Post by bladerunner6 on 2010-10-16
i see the patches you mention, i have installed the debs and they work without patches

---

