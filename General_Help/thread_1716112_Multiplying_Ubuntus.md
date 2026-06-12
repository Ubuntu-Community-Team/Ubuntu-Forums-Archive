---
title: "Multiplying Ubuntus?"
date: 2011-03-28
forum: General Help
---

### Post by 42f87d89 on 2011-03-28
I have a dualbooted acer aspire 7738, and from time to time there is a new option in the boot up to choose Ubuntu. I currently have 4 options in my boot menu which consist only of Ubuntu. They don't appear to be separate from one another, as in, if I change anything in one it also changes in the other, so I believe my problem lies only in the boot menu.

---

### Post by idoitprone on 2011-03-28
Sound like your system is piling kernels updates. Just go to the synaptic and uninstall older kernels. This way it does not pile your boot menu. All those ubuntu do point to the same ubuntu, but one only difference is that you are using a different kernel which mean you may have special feature that will cause problem for some apps such as powertop 1.97 which need the 2.6.37 kernel

---

### Post by mcduck on 2011-03-28
Idoitprone is right, when you get a kernel update the new kernel version doesn't replace the old one, but is installed alongside it instead. This allows you to test the new kernel to make sure it works correctly on your computer, and leaves you with the option of booting with the old version instead if the new one doesn't work for you.

You can simply uninstall the old kernel version packages using Synaptic Package Manager, and the menu entries will be removed automatically.

---

### Post by hawthornso23 on 2011-03-28
The duck is correct. I'd like to add however that extra kernels take up very little disk space. So apart from the cluttered Grub menu, there is no problem with having a bunch of them.

---

### Post by mcduck on 2011-03-28
> **hawthornso23 said:**
> The duck is correct. I'd like to add however that extra kernels take up very little disk space. So apart from the cluttered Grub menu, there is no problem with having a bunch of them.

I suppose that depends on what you count as taking much space... ;)

A single kernel version together with it's header files (and possible other module packages) will take around 300MB of space. That's not much, but considering the OP has three older kernels they are actually taking about a gigabyte's worth of drive space.

So, having a single extra kernel indeed doesn't take much space, but you still wouldn't want to leave every kernel version installed.

---

### Post by 42f87d89 on 2011-03-28
Thankyou everyone, as you can guess I'm new to Linux/GNU so I was really confused.

---

### Post by 42f87d89 on 2011-03-28
Can anyone point me out on how to uninstall the right kernel? Or give me a link?

---

### Post by plucky on 2011-03-28
Post output from a terminal of ```
ls -l /boot
```

I use **Synaptic Package Manager** and search for **linux-image** and I mark the older packages for complete removal taking care to leave the latest kernel and the previous one,just in case there is a problem with the newest one.

Also I search for **linux-headers** and remove the corresponding ones to the kernels I marked for removal.

Then select **Apply**, and it will remove the kernels and headers and clean up grub.cfg.

Good Luck

---

### Post by drs305 on 2011-03-28
I recommend a GUI app called Ubuntu-Tweak. It is about as painless as it can be for removing older kernels, and it performs many other routine operations as well.

Here's a thread I created about removing older kernels. Instructions on how to install and use Ubuntu Tweak are included therein:
[HOWTO: Remove Older Kernels via GUI (or CLI)]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by TBABill on 2011-03-28
Just a side note on this topic. I usually tell people to keep one old kernel plus their current one. As long as that older one works perfectly you have a backup in case a new update that is kernel related borks your system. Many people experience issues like that with wireless, sound and other peripheral devices that previously worked and get borked on an update. If it's an app that updates, this won't help at all, but if it affects the kernel then you could find yourself able to boot into the old one till you figure out what went wrong.

---

### Post by 42f87d89 on 2011-03-28
How do I change it to solved? I'm very sorry, I'm a big newbie.

---

### Post by drs305 on 2011-03-28
> **42f87d89 said:**
> How do I change it to solved? I'm very sorry, I'm a big newbie.

Glad it's solved. Use the 'Thread Tools' link near the top right of the first post. And thanks for marking it solved - it allows the helpers to concentrate on unresolved issues.  :-)

---

### Post by 42f87d89 on 2011-03-28
> **drs305 said:**
> Glad it's solved. Use the 'Thread Tools' link near the top right of the first post. And thanks for marking it solved - it allows the helpers to concentrate on unresolved issues.  :-)
Thanks.:D

---

