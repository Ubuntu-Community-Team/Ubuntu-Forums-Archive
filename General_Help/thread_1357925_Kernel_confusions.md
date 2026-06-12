---
title: "Kernel confusions"
date: 2009-12-17
forum: General Help
---

### Post by MKVCrazy on 2009-12-17
I used to run a kernel that was custom compiled by my hosting company so I recompiled my version (mostly standardized) using the 2.6.32.1 form kernel.org. But I was still running 2.6.31-16 headers and my VirtualBox (both versions) won't start. I keep getting the following message.

[IMG]http://i48.tinypic.com/sv2qkn.png[/IMG]

I've got a suggestion from a site moderator on VirtualBox.org that I need to make my headers files to same version as my currently running kernel so I downloaded the 2.6.32 version of the headers, actually I installed the following three yesterday.

linux-headers-2.6.32-020632_2.6.32-020632_all.deb
linux-headers-2.6.32-020632-generic_2.6.32-020632_amd64.deb
linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb

I've changed no settings and restarted after I installed these three but the VirtualBox still doesn't work. Do I need to recompile another version of kernel from kernel.org so that the newly installed headers will be used this time? I am going to install 2.6.32 (not 2.6.32.1) this time if I have to recompile.

By the way what is this, linux-source-2.6.32_2.6.32-020632_all.deb? Is this the one if I download I don't need to get the one from kernel.org? Or this is completely something else? Please advice me how to get both kernel and headers same versions.

EDIT: 

I was suggested to choose that newly installed headers version in GRUB at boot up but I cannot see boot up since I am doing all these on a server. Is there another way to do it?

---

### Post by falconindy on 2009-12-17
Whomever recompiled your kernel included KVM extensions. Hopefully, they were compiled as modules and not built into the kernel. Let's see the output of:
```
lsmod | grep kvm
```
If there's no output, you need to tell those noodle noggins to give you back your old kernel or recompile without forcing the KVM extensions on you.

If there is output and it's something like 'intel_kvm', you'll need to unload it with `sudo modprobe -r intel_kvm`.

---

### Post by MKVCrazy on 2009-12-17
I have tried those kind of commands (testing if KVM installed or not) many times, and there's no outputs.

```
root@XXXXX:~# lsmod | grep kvm
root@XXXXX:~# 
```

Yes, I feel what you're saying might be the reason. People say KVM is not installed by default (at least those who replied) but I see plenty KVM related files and folders when I did a search in the directory. How may I not let it force KVM to be installed?

---

### Post by falconindy on 2009-12-17
> **MKVCrazy said:**
> I have tried those kind of commands (testing if KVM installed or not) many times, and there's no outputs.

```
root@XXXXX:~# lsmod | grep kvm
root@XXXXX:~# 
```

Yes, I feel what you're saying might be the reason. People say KVM is not installed by default (at least those who replied) but I see plenty KVM related files and folders when I did a search in the directory. How may I not let it force KVM to be installed?
It's not a matter of being 'installed'. When the bozo tech compiled your kernel, he told certain KVM features (the ones preventing you from starting VBox to be compiled into the kernel, and not built as modules. Because they weren't built as modules, you have no recourse to prevent them from loading. They're just a flat out 'feature' of this kernel.

It's because VirtualBox doesn't focus on 'true' virtualization that it won't allow your kernel to operate in this state. It handles a lot of the negotiation with kernel based virtualization extensions on its own. You'll need to talk to your hosting company to have 1 of a few things happen:

- Revert back to the old kernel (if they didn't get rid of it).
- Recompile a new kernel either without the extensions at all, or with them built as modules.

In case its helpful when you're talking to them, the 3 lines below are straight out of the kernel config and what needs to be set to have the extensions built as modules:
```
CONFIG_KVM=m
CONFIG_KVM_INTEL=m
CONFIG_KVM_AMD=m
```
The noodle noggins set these lines to be 'y'.

---

### Post by lmarmisa on 2009-12-17
Try to reinstall VirtualBox from Synapctic. I had a similar problem after the installation of a new kernel version and I was able to fix it with this solution.

Best regards,

Luis

---

### Post by MKVCrazy on 2009-12-17
Yes, you're right. I cannot not use any command to stop the KVM from starting :(. I am running version 2.6.32.1 and is it possible to just change those config settings are reboot to apply or do I recompile the same kernel as installing new one and change those settings?

Sorry for the too many questions, just making sure I get things right this time. I've done several messy stuff and I'm at my best situation right now, only VirtualBox is not working :)

Do you have an IM account (MSN or Gmail) if I you can give me a couple minutes of you time?

---

### Post by falconindy on 2009-12-17
> **MKVCrazy said:**
> Yes, you're right. I cannot not use any command to stop the KVM from starting :(. I am running version 2.6.32.1 and is it possible to just change those config settings are reboot to apply or do I recompile the same kernel as installing new one and change those settings?

Sorry for the too many questions, just making sure I get things right this time. I've done several messy stuff and I'm at my best situation right now, only VirtualBox is not working :)

Do you have an IM account (MSN or Gmail) if I you can give me a couple minutes of you time?
Sorry if I haven't made this clear. The kernel config is passed to the compiler when the kernel is built. To change the config requires recompiling a new kernel.

Recompiling is your only option to get VBox working.

> **lmarmisa said:**
> Try to reinstall VirtualBox from Synapctic. I had a similar problem after the installation of a new kernel version and I was able to fix it with this solution.

Best regards,

Luis
Your problem could have been easily solved by running 'sudo /etc/init.d/vboxdrv setup'. This isn't related to building a new kernel module after installing a new kernel.

---

### Post by MKVCrazy on 2009-12-17
Ok. That sound a do-able for me. I've done a kernel recompilation myself twice BUT I am not really sure where to change those settings. I think I may, myself, have mistaken set those settings to "y's" and not them :(

Does it happen around here?
```
sudo mv MYNEWKNERNELVERSION .config
sudo make menuconfig
```

By the way, how long could you response to this thread today, I would like to recompile it now and go steps by steps checking carefully that I don't miss that step but if I don't see that option, it ain't going to be good.

---

### Post by falconindy on 2009-12-17
Oh. If you're going to recompile yourself, this is a little easier. When the build options come up after 'make menuconfig', drill down into the 'Virtualization' section (right near the end). Make sure the option for KVM extensions as well as both sub-options for Intel and AMD processors are marked 'm' and not '*'.

Feel free to PM me if you have any issues.

---

### Post by MKVCrazy on 2009-12-17
I've found the ****** right here. Just before I continue, is there any other place that you can think of needed to be changed?

[IMG]http://i48.tinypic.com/3097v9l.png[/IMG]

---

### Post by falconindy on 2009-12-17
Nope, that's all you need to change.

---

### Post by theozzlives on 2009-12-17
2.26.32.1 is Lucid Lynx, It's currently in Alpha 1 and not for production yet.

---

### Post by MKVCrazy on 2009-12-17
> **falconindy said:**
> Nope, that's all you need to change.
Thanks. It's Executing ....

Hopefully things go well.
> **theozzlives said:**
> 2.26.32.1 is Lucid Lynx, It's currently in Alpha 1 and not for production yet.
On Kernel.org it says "STABLE". So I used it but if that's the case then I'm aways ignoring all "not-fully-ready" stuff :D

---

### Post by MKVCrazy on 2009-12-17
One more thing. I've executed the kernel. Now I am at the part where I have to copy the image from arch thing to bzimage but I have question.

There are two boot in my kernel folder. Which one do I use? x86 or x86_64? The first time I did I used x86 but when I do uname -a in my terminal I still see that my kernel is running x86_64. What difference do they make?

If you don't get what I am talking about:
This
```
cp arch/x86/boot/bzImage /boot/bzImage-linux-2.6.32-mod
```
or this
```
cp arch/x86_64/boot/bzImage /boot/bzImage-linux-2.6.32-mod
```

Screenshot

[IMG]http://i48.tinypic.com/33dk0i1.png[/IMG]

Both bzimage files are 4.5MB.

---

### Post by falconindy on 2009-12-18
If you're currently running a x86_64, then stick with it. It's feasible to run a 64 bit kernel on a 32 bit install (provided you compile it correctly), but you don't want to do the opposite.

---

### Post by falconindy on 2009-12-18
> **theozzlives said:**
> 2.26.32.1 is Lucid Lynx, It's currently in Alpha 1 and not for production yet.
Just because LL is Alpha doesn't mean the kernel associated with it is. I salute the OP for wandering off on his own and learning!

---

### Post by MKVCrazy on 2009-12-18
OMG! IT WORKED! You're the man, falconindy !!! Everybody who replied in last 5 days had no idea, they were say "What? Why it does work? It should work. It's got to work.".

VirtualBox is running now and I'm at installing my guest OS'es. I can't thank you enough.

EDIT: I salute you back for posting not just replies but true answer to this specific problem.

---

### Post by falconindy on 2009-12-18
Wild. I'm shocked to hear that VBox's own forums were of no help on this. Frankly, that's a bit embarassing.

Glad to help.

---

### Post by MKVCrazy on 2009-12-18
uhm, I think they were kinda of some help. I mentioned in my first post of this thread that one of the Site Moderators suggested me to get both the kernel and header files version to be the same that was the lead which got me make this thread and solve the problem but I really glad that these happened today (before holidays) :D

---

