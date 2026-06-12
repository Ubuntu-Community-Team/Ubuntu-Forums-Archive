---
title: "How to manipulate options for executing fsck on boot?"
date: 2011-07-14
forum: General Help
---

### Post by szal on 2011-07-14
Hi folks,

We all know that every now and then hard drive partitions get a full check-up on booting the system. Nothing against that, just to say.

But what I wonder is: Where in the init process is *fsck* called to execute? I want to change an option: as it looks, it is set to *--quiet* by default, i.e. showing nothing but which partition is being fsck-ed and a message that a check is in progress and may take a while. But I want to pass *-C*, i.e. showing progress bars, instead. Where do I do that?

Any help will be appreciated.

Kind regards

szal

---

### Post by szal on 2011-07-15
Bump…

---

### Post by dino99 on 2011-07-15
[http://manpages.ubuntu.com/manpages/natty/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/natty/man8/fsck.8.html)

---

### Post by szal on 2011-07-15
dino99: I don’t see where the fsck manpage describes where it is called up in the boot process. Can you point me to it?

---

### Post by szal on 2011-07-16
Bump again…

---

### Post by bodhi.zazen on 2011-07-16
actually, see the man tune2fs

[http://manpages.ubuntu.com/manpages/natty/man8/tune2fs.8.html](http://manpages.ubuntu.com/manpages/natty/man8/tune2fs.8.html)

in particular the "-c" option as well as fstab ;)

---

### Post by szal on 2011-07-16
Sorry guys, but I’m getting the feeling that you’re turning this into a guessing game… I asked neither about changing when filesystems are to be fsck’d (tune2fs) nor about whether they should be fsck’d at all (fstab). I asked about how to change the VERBOSITY of the output of fsck being executed when the machine boots up…

---

### Post by bodhi.zazen on 2011-07-16
That is probably in your initramfs ;)

IMO easiest method would be to extract the initrd, add the option(s) you want, and then compress it again.

---

### Post by dino99 on 2011-07-16
as said previously, this is driven by the kernel. You can follow the man pages to tweak the default settings.

---

### Post by szal on 2011-07-16
> **dino99 said:**
> as said previously, this is driven by the kernel. You can follow the man pages to tweak the default settings.
As asked previously: Please bang my nose on it! I fail to see where there is described what I want to achieve…

bodhi.zazen: Thanks for the suggestion, I’ll have a look.

---

### Post by szal on 2011-07-16
> **bodhi.zazen said:**
> IMO easiest method would be to extract the initrd, add the option(s) you want, and then compress it again.
Ummm, no. It’s hard to grasp what *$INITRD/lib/plymouth/themes/kubuntu-logo/kubuntu-logo.script* does, but as far as I can see it regulates how to display in the bootsplash when fsck is run—and I can’t find a single line there actually calling fsck; the initramdisk doesn’t even contain a fsck binary. Besides, this is not what I want since I’m starting the machine up without a bootsplash. Other than that, there is no occurrence of ‘fsck’ outside of code comments anywhere in the initramdisk.

---

### Post by bodhi.zazen on 2011-07-16
> **szal said:**
> Ummm, no. It’s hard to grasp what *$INITRD/lib/plymouth/themes/kubuntu-logo/kubuntu-logo.script* does, but as far as I can see it regulates how to display in the bootsplash when fsck is run—and I can’t find a single line there actually calling fsck; the initramdisk doesn’t even contain a fsck binary. Besides, this is not what I want since I’m starting the machine up without a bootsplash. Other than that, there is no occurrence of ‘fsck’ outside of code comments anywhere in the initramdisk.

See the init script in the initrd

---

### Post by szal on 2011-07-17
> **bodhi.zazen said:**
> See the init script in the initrd
Which one exactly?

---

### Post by bodhi.zazen on 2011-07-17
> **szal said:**
> Which one exactly?

This is how to extract the initrd

[https://help.ubuntu.com/community/LiveCDCustomization#Advanced%20Customizations](https://help.ubuntu.com/community/LiveCDCustomization#Advanced%20Customizations)

From there search for fsck, I used grep and found it in this script :

lib/plymouth/themes/kubuntu-logo/kubuntu-logo.script

You will have to re-write the functions (fun) in that script, or at least modify the fsck options, and then make a new initrd.

The origional script is in lib/plymouth/themes/kubuntu-logo/kubuntu-logo.script

You can modify the script and then use the system tools to build your custom initrd, which is covered in the link I gave you as well.

---

### Post by szal on 2011-07-17
> **bodhi.zazen said:**
> This is how to extract the initrd

[https://help.ubuntu.com/community/LiveCDCustomization#Advanced%20Customizations](https://help.ubuntu.com/community/LiveCDCustomization#Advanced%20Customizations)

From there search for fsck, I used grep and found it in this script :

lib/plymouth/themes/kubuntu-logo/kubuntu-logo.script
If you had actually read my post #11, you’d have seen that I was already as far as this. But thanks for the link; it’s good to know that at least some information on this general topic exists. :)

> **bodhi.zazen said:**
> You will have to re-write the functions (fun) in that script, or at least _**modify the fsck options**_, and then make a new initrd.
*(Emphasis in the quotation by me)*

THIS is EXACTLY what I want to know HOW TO ACTUALLY DO! Any pointer in the right direction will be appreciated. Also a resource to the script language used (I don’t even know what language that is) won’t hurt. :)

---

