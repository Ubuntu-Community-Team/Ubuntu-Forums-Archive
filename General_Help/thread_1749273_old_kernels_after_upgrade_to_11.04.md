---
title: "old kernels after upgrade to 11.04"
date: 2011-05-04
forum: General Help
---

### Post by marcio_mi on 2011-05-04
after the upgrade I noticed that in my grub list there was the option "Older Linux Kernel" (weird, I usually have all of them listed, but anyway), therefore I went to synaptic to eliminate all but the most recent kernel that came with natty.

However, there are no other linux-headers / linux-image files than the ones related to the current kernel.

But if I run 

```
ls /boot | grep vmlinuz
```

I get

```
vmlinuz-2.6.35-22-generic
vmlinuz-2.6.35-24-generic
vmlinuz-2.6.35-25-generic
vmlinuz-2.6.35-27-generic
vmlinuz-2.6.35-28-generic
vmlinuz-2.6.38-8-generic
```

and my /boot directory looks like this:

miccoli@netbook-N230:/boot$ ls
```
abi-2.6.35-22-generic         memtest86+_multiboot.bin
abi-2.6.35-24-generic         System.map-2.6.35-22-generic
abi-2.6.35-25-generic         System.map-2.6.35-24-generic
abi-2.6.35-27-generic         System.map-2.6.35-25-generic
abi-2.6.35-28-generic         System.map-2.6.35-27-generic
abi-2.6.38-8-generic          System.map-2.6.35-28-generic
config-2.6.35-22-generic      System.map-2.6.38-8-generic
config-2.6.35-24-generic      vmcoreinfo-2.6.35-22-generic
config-2.6.35-25-generic      vmcoreinfo-2.6.35-24-generic
config-2.6.35-27-generic      vmcoreinfo-2.6.35-25-generic
config-2.6.35-28-generic      vmcoreinfo-2.6.35-27-generic
config-2.6.38-8-generic       vmcoreinfo-2.6.35-28-generic
grub                          vmcoreinfo-2.6.38-8-generic
initrd.img-2.6.35-22-generic  vmlinuz-2.6.35-22-generic
initrd.img-2.6.35-24-generic  vmlinuz-2.6.35-24-generic
initrd.img-2.6.35-25-generic  vmlinuz-2.6.35-25-generic
initrd.img-2.6.35-27-generic  vmlinuz-2.6.35-27-generic
initrd.img-2.6.35-28-generic  vmlinuz-2.6.35-28-generic
initrd.img-2.6.38-8-generic   vmlinuz-2.6.38-8-generic
memtest86+.bin
```

what shall I do? shall I just assume that old kernels files were removed and so I should manually clean the /boot directory?

cheers

---

### Post by coffeecat on 2011-05-04
> **marcio_mi said:**
> after the upgrade I noticed that in my grub list there was the option "Older Linux Kernel" (weird, I usually have all of them listed, but anyway),

That's a new design feature with the 1.99 version of grub that comes with Natty. Makes the grub menu tidier when you have a lot of kernels.

> **marcio_mi said:**
> 
 therefore I went to synaptic to eliminate all but the most recent kernel that came with natty.

However, there are no other linux-headers / linux-image files than the ones related to the current kernel.

But if I run 

```
ls /boot | grep vmlinuz
```I get

```
vmlinuz-2.6.35-22-generic
vmlinuz-2.6.35-24-generic
vmlinuz-2.6.35-25-generic
vmlinuz-2.6.35-27-generic
vmlinuz-2.6.35-28-generic
vmlinuz-2.6.38-8-generic
```

Have another look in Synaptic, only this time use the search string "2.6.35". I'm sure they'll still be there - three packages for each version of the kernel.

---

### Post by matthewbpt on 2011-05-04
You are looking for the headers, which are used to compile kernel modules, so they aren't installed unless you installed proprietary drivers or build-essential. What you need to look for is linux-image in synaptic.

---

### Post by marcio_mi on 2011-05-04
hey coffeecat, thanks

they're not there, that is why I am puzzled! I looked at it again using your search string, but nothing comes out. Also if I run in the terminal

```
dpkg --get-selections | grep 2.6.35
```

nothing comes out. I might have run 

```
 sudo apt-get autoremove 
```

at some point, do you think it could have created this situation?

---

### Post by coffeecat on 2011-05-04
> **marcio_mi said:**
> I might have run 

```
 sudo apt-get autoremove 
```at some point, do you think it could have created this situation?

I'm not sure. If it uninstalled old kernels - which your dpkg command seems to tell us -  it ought to have removed the kernel images that are clearly in /boot. Let's see if you have the rest of the 2.6.35 kernels, whatever anything else is saying. Run:

```
ls /lib/modules
ls /usr/src
```The latter will show whether you have headers present.

---

### Post by marcio_mi on 2011-05-04
thanks, it seems that something it's showing up now. When I try:

```
miccoli@netbook-N230:~$ ls /lib/modules
2.6.38-8-generic
```

nothing new. But when I do:

```
miccoli@netbook-N230:~$ ls /usr/src
bcmwl-5.60.48.36+bdcom           linux-headers-2.6.35-25-generic
easy_slow_down_manager-0.13.7    linux-headers-2.6.35-27
ipheth-1.0                       linux-headers-2.6.35-27-generic
linux-headers-2.6.35-22          linux-headers-2.6.35-28
linux-headers-2.6.35-22-generic  linux-headers-2.6.35-28-generic
linux-headers-2.6.35-24          linux-headers-2.6.38-8
linux-headers-2.6.35-24-generic  linux-headers-2.6.38-8-generic
linux-headers-2.6.35-25          samsung_backlight-0.13.7
```

all the headers are there! how shall I do to remove them?

---

### Post by alphacrucis2 on 2011-05-04
Exactly the same thing happenned to me when upgrading to 11.04. The old kernels were removed from the package database but are still on disk, so update-grub finds them and includes them in the boot menu under older linux kernels. I just deleted them and reran sudo update-grub.

Another thing I notice probably related to this grub menu change is that the startup-manger program no longer works for changing the default OS

---

### Post by marcio_mi on 2011-05-04
hi alphacrucis2,

so you just erased the unwanted headers in /usr/src/ or you also erased something else?

---

### Post by alphacrucis2 on 2011-05-04
> **marcio_mi said:**
> hi alphacrucis2,

so you just erased the unwanted headers in /usr/src/ or you also erased something else?

I erased the files pertaining to old kernels under /boot. I hadn't actually removed the old headers but I have now :D.

---

### Post by coffeecat on 2011-05-05
That's an interesting bug. So, the upgrade removes old kernel information from the package database, and deletes everything in /lib/modules but leaves the kernel images in /boot and headers in /usr/src? Hmm. Odd. :-k I agree that removing the old vmlinuz* images and the contents of /usr/src and then running update-grub would be the best thing to do.

I've done a quick search of Launchpad, but I didn't find anything.

---

### Post by marcio_mi on 2011-05-05
Thanks to both of you! =D>
I'll file a bug in launchpad then, and I'll tag the thread as solved.

cheers

---

