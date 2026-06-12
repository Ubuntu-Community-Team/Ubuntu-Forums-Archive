---
title: "&quot;Unsupported WMI interface&quot; on boot causes distorted splash screen, terminal windows"
date: 2010-07-04
forum: General Help
---

### Post by auh2o on 2010-07-04
I installed Ubuntu 10.04 on an Acer Aspire 1350 laptop. It has crappy, integrated VIA KM400/KN400/P4M800 graphics and as such will use the Openchrome driver.

Everything went fine, except I get the following message on bootup:

```
Unsupported WMI interface, unable to load
```This has apparently caused the bootup process to freeze for some people, but for me it will boot just fine anyway, except for that the splash screen is heavily distorted.

Booting with Grub command line options

```
nomodeset
``` (to disable KMS)

or

```
i915.modeset=1
```and/or removing the splash screen, does nothing to rectify the situation.

If the only problem was distorted graphics during bootup, then I could live with that. However, it also messes up my tty terminals (Ctrl-Alt-F1 etc.). If I go into any of these terminal windows, the whole screen is just one big mishmash of distorted blocks of color, and no text is visible.

Any suggestions on what I could do?

Here is some further info: [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/566379)

But none of the solutions has worked for me. (I have not tried to upgrade the kernel, and would rather not want to.)

---

### Post by clrg on 2010-07-04
If you can manage to boot into single user mode, does the problem go away? You could then do diagnostic work.

---

### Post by auh2o on 2010-07-04
Well, I can boot into Recovery, but it doesn't do much good. See attachments to find out what it looks like.

Also, the red picture is how it looks like going into tty1 from the desktop.

Basically anything outside of gdm is unviewable.

---

### Post by clrg on 2010-07-04
Gorgeous.

Does the problem with the distorted terminals also occur when you use the live CD? 

Also, check whether you have the latest version of the driver you are using (not from the repositories, from source). If not, try to compile & install the latest one.

And out of curiosity, why wouldn't you want to update the kernel?

---

### Post by dcstar on 2010-07-04
> **auh2o said:**
> Well, I can boot into Recovery, but it doesn't do much good. See attachments to find out what it looks like.

Also, the red picture is how it looks like going into tty1 from the desktop.

Basically anything outside of gdm is unviewable.

Select a basic resolution in the /etc/default/grub file.

---

### Post by nerdy_kid on 2010-07-04
that would be a framebuffer issue?
i dont really know what im talking about, but i *think* that if you disable the framebuffer driver that the openchrome driver provides and use the vga one then it could fix the issue for you.  or maybe vice versa.

---

### Post by auh2o on 2010-07-04
> **clrg said:**
> Gorgeous.

Does the problem with the distorted terminals also occur when you use the live CD? 

Also, check whether you have the latest version of the driver you are using (not from the repositories, from source). If not, try to compile & install the latest one.

And out of curiosity, why wouldn't you want to update the kernel?

I would have to burn a Live CD and check. I installed with the Alternate.

The openChrome driver in the Lucid repositories is the latest version  (0.2.904).

As for the kernel, I want everything to be handled by the official repos. No external repos, installations or kernels. Simplicity is the key, you see, when you're preparing a laptop for your mother. ;)

Besides, others have apparently solved this issue while staying on the .32 kernel.

> **dcstar said:**
> Select a basic resolution in the /etc/default/grub  file.

You mean as in setting GRUB_GFXMODE=640x480? Sorry to say that didn't  help.

> **nerdy_kid said:**
> that would be a framebuffer issue?
i dont really know what im talking about, but i think that if you disable the framebuffer driver that the openchrome driver provides and use the vga one then it could fix the issue for you.  or maybe vice versa.

I don't know what you're talking about either, but I'd be glad to give it a shot if someone could explain how!


Or what about generating an xorg.conf file and approach the problem from there? Might that be necessary? Set modelines, for example?

---

