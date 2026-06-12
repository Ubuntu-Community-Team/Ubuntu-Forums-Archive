---
title: "Uninstall custom kernel"
date: 2009-09-29
forum: General Help
---

### Post by itsjareds on 2009-09-29
I installed a custom kernel about 4 months ago for testing purposes -- since then I haven't had a need for the kernel and uninstalled it. I thought it was uninstalled a long time ago. However, I ran 'sudo update-initramfs -k all -u' a few days ago and was returned with this:

```
$ sudo update-initramfs -k all -u
update-initramfs: Generating /boot/initrd.img-2.6.31-11-generic
update-initramfs: Generating /boot/initrd.img-2.6.28.9-custom
Cannot find /lib/modules/2.6.28.9-custom
update-initramfs: failed for /boot/initrd.img-2.6.28.9-custom
```

I don't know why that kernel is still found by my system. I followed the manual kernel removal steps [on this article]("http://www.cyberciti.biz/faq/debian-redhat-linux-delete-kernel-command/") and I figured that would fix it. Nope, still the same error.

After running 'dpkg --list | grep linux-image', I get this:

```
$ dpkg --list | grep linux-image
ii  linux-image-2.6.31-11-generic              2.6.31-11.36                                            Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                        2.6.31.11.22                                            Generic Linux kernel image
```

So now I don't know what to do. Help?

---

### Post by Ayuthia on 2009-09-29
It looks like you still have files that exist in /boot.  Did you remove the files related to that custom kernel?

---

### Post by itsjareds on 2009-09-29
Yes, I followed these steps:

> If you have custom compiled kernel you need to remove following files/dirs:

[LIST][*]/boot/vmlinuz*KERNEL-VERSION*
[*]/boot/initrd*KERNEL-VERSION*
[*]/boot/System-map*KERNEL-VERSION*
[*]/boot/config-*KERNEL-VERSION*
[*]/lib/modules/*KERNEL-VERSION*/
[*]Update grub configuration file /etc/grub.conf or /boot/grub/menu.lst to point to correct kernel version.[/LIST]

All were removed, including /usr/src/*KERNEL-VERSION*/.

Thanks for the reply.

---

### Post by Ayuthia on 2009-09-29
Have you done a search on that kernel?  Sometimes locate can find something:
```
locate 2.6.28.9-custom
```

---

### Post by itsjareds on 2009-09-29
That worked beautifully! I had to remove another file located at /var/lib/initramfs-tools/2.6.28.9-custom. After removing that, I ran 'update-initramfs' again and it worked correctly. Thanks!

p.s. - That 'locate' command is useful, how is it different from 'find'? Locate seemed to work lightning-quick.

---

### Post by Ayuthia on 2009-09-29
> **itsjareds said:**
> That worked beautifully! I had to remove another file located at /var/lib/initramfs-tools/2.6.28.9-custom. After removing that, I ran 'update-initramfs' again and it worked correctly. Thanks!

p.s. - That 'locate' command is useful, how is it different from 'find'? Locate seemed to work lightning-quick.

locate has a database that gets updated periodically so there can be times where newer files won't be found.  However, you can always updated it before doing your search:
```
sudo updatedb
```

The locate command does have some folders that are not in the search.  I forgot what folders Ubuntu has in the database search.  find does not have that limitation.

---

