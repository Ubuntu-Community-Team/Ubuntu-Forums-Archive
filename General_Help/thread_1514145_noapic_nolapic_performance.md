---
title: "noapic nolapic performance"
date: 2010-06-20
forum: General Help
---

### Post by High Roller on 2010-06-20
I have added noapic nolapic to the boot parameters and now only see one CPU instead of four that I would see otherwise.

Are all four cores being grouped into one or am I only using 1/4 of my processor now?

---

### Post by davidmohammed on 2010-06-20
...

[this]("http://ubuntuforums.org/showthread.php?t=1084622") is an old thread but it may have some bearing with your issue.  

What happens if you don't use nolapic to boot with?

---

### Post by High Roller on 2010-06-20
> **davidmohammed said:**
> 
What happens if you don't use nolapic to boot with?

It crashes, as per [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

When I do this it doesn't crash.  But I'm wondering if I'm limiting my computer to just 1 core.  Meaning 1/4th the performance.

I saw that other link.  But I wasn't sure if it applied to multi-core processors.

---

### Post by davidmohammed on 2010-06-20
from what I've read nolapic definitely does affect multicore CPU's - that other thread, that guy used some very weired boot options.  Do they work for you?

---

### Post by High Roller on 2010-06-20
> **davidmohammed said:**
> from what I've read nolapic definitely does affect multicore CPU's - that other thread, that guy used some very weired boot options.  Do they work for you?

They do, but if it's at the cost of only having access to 1/4th the power of my CPU I need to find a better option.

From my estimates, I might be in need of buying a different motherboard or something.  The mobo appears to be the root problem.  I tried to return it and they (ASUS) said it tested fine under windows and sent it back to me.

So I may ditch ASUS and switch to EVGA or something.  I've heard good things about them.

---

### Post by davidmohammed on 2010-06-20
... maybe a longshot - but does installing the latest 2.6.34-lucid kernel fix your issue?

go to this [site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/")

now download the following links:
linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38 675K 
linux-headers-2.6.34-020634_2.6.34-020634_all.deb 17-May-2010 20:27 9.6M 
linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38 30M 

check they have downloaded to your Downloads folder

then

cd Downloads
ls *.deb --> should list the 3 files above
sudo dpkg -i *.deb --> this will install all three deb files

if you see any errors being reported then the install hasn't worked.

reboot

---

### Post by High Roller on 2010-06-20
> **davidmohammed said:**
> ... maybe a longshot - but does installing the latest 2.6.34-lucid kernel fix your issue?

go to this [site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/")

now download the following links:
linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38 675K 
linux-headers-2.6.34-020634_2.6.34-020634_all.deb 17-May-2010 20:27 9.6M 
linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38 30M 

check they have downloaded to your Downloads folder

then

cd Downloads
ls *.deb --> should list the 3 files above
sudo dpkg -i *.deb --> this will install all three deb files

if you see any errors being reported then the install hasn't worked.

reboot

Tried that.  Even the older RT kernel in the Lucid repo isn't stable on this board.  The only way to stop the problem is to set noapic nolapic.

Thanks for your help though!

---

### Post by davidmohammed on 2010-06-21
Its worth checking in your BIOS for your various ACPI settings.  Some combinations and settings can cause issues like yours.

---

