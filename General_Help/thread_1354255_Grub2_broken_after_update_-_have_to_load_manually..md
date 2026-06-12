---
title: "Grub2 broken after update - have to load manually."
date: 2009-12-13
forum: General Help
---

### Post by detroit/zero on 2009-12-13
After an update last night or earlier today, I rebooted without running sudo update-grub2. Now, every time I try to load any of the kernels I have installed or my Windows partition, I get the error message "you need to load the kernel first."

I'm booted into my system right now, but I had to do it manually by entering the following at the grub terminal prompt:

[LIST=1]
[*]set root=(hd0,8)
[*]linux /vmlinuz-2.6.31-17-generic root=/dev/sda6 quiet splash
[*]initrd /initrd.img-2.6.31-17-generic
[*]boot
[/LIST]
Which boots me into my system as it normally would. Once in, I've tried both
```
sudo update-grub2
```and
```
sudo grub-mkconfig
```but neither command works, even though in the terminal it looks like they did:
> zero@zero-laptop:~$ sudo update-grub
[sudo] password for zero: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
Found Windows Vista (loader) on /dev/sda2
doneCan anybody tell me why I have to manually configure my bootloader every time I start my system? I've had a few kernel updates in the past and even seen grub update once or twice now, and this is the first time I've had a problem with the new grub.

I realize that documentation is available, but according to docs, the above should be solving my problem.

---

### Post by ajgreeny on 2009-12-13
I had exactly that problem when I added the stanza for ubuntu 9.10 from the grub.cfg to my 9.04 grub menu.lst file, which is waht I use as my boot loader.  Are you sure that grub2 is being used?  If you updated from 9.04 to 9.10 as an online update, it is possible you are still using legacy grub, though why that should cause you that problem after a normal update, I'm not at all sure.

Have a look to see if you have a /boot/grub/menu.lst file, and also lookclosely when you boot and see the "starting grub" statement to see which version is mentioned.

---

### Post by Leppie on 2009-12-13
Re-install grub to your mbr:
```
$sudo grub-install --recheck /dev/sda
```
Then update grub to create a correct grub.cfg.

---

### Post by detroit/zero on 2009-12-13
> **ajgreeny said:**
> I had exactly that problem when I added the stanza for ubuntu 9.10 from the grub.cfg to my 9.04 grub menu.lst file, which is waht I use as my boot loader.  Are you sure that grub2 is being used?  If you updated from 9.04 to 9.10 as an online update, it is possible you are still using legacy grub, though why that should cause you that problem after a normal update, I'm not at all sure.

Have a look to see if you have a /boot/grub/menu.lst file, and also lookclosely when you boot and see the "starting grub" statement to see which version is mentioned.
I didn't update - this was a fresh install, and grub-legacy hasn't come anywhere near it.

> **Leppie said:**
> Re-install grub to your mbr:
```
$sudo grub-install --recheck /dev/sda
```Then update grub to create a correct grub.cfg.
Not a bad idea, but I tried it and it didn't work. I still have to manually enter the same commands I listed before.

---

### Post by Leppie on 2009-12-13
that's odd...
could you post your device.map?

---

### Post by detroit/zero on 2009-12-13
> **Leppie said:**
> that's odd...
could you post your device.map?
```
zero@zero-laptop:~$ cat /boot/grub/device.map
(hd0)    /dev/sda
```
That's all there is.

---

### Post by Leppie on 2009-12-13
that looks fine.
is this a hp or dell you're on? i've read somewhere that they use some tool which apparently messes up grub.

---

### Post by detroit/zero on 2009-12-13
Nope. Toshiba Satellite a135.

---

### Post by Leppie on 2009-12-13
as a last resort you could try to change the uuid references to normal /dev references. normally grub2 prefers uuid, but in some cases that doesn't seem to work properly. if that works, you probably will have to update your fstab as well.

---

### Post by detroit/zero on 2009-12-13
I got it to work. From synaptic, I purged grub-common and grub-pc. Then I went to /var/cache/apt/archives and removed any versions of grub that were there. I reloaded the package list in synaptic, and then re-installed. 

When I rebooted, everything worked as expected. 

I'm still not sure what that was all about.

Thanks for your help, anyway..

---

