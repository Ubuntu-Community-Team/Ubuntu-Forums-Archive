---
title: "reducing /run ramdisk size and reducing ram usage"
date: 2012-04-29
forum: General Help
---

### Post by Sudo Bash on 2012-04-29
Hi,

I have a machine I am trying to save some ram on. I tried typing mount to see if there were any tmpfs mounted and I found about Ubuntu's /run. Being more used to Slackware than Ubuntu I looked for a /run entry in /etc/fstab but Ubuntu doesn't seem to use it for very much.

How can I reduce the size of /run? Is this a good idea and how much is safe to reduce it by?

If you have any other suggestions then I would be glad to hear them. The main thing which I have done is use xfce instead of Gnome for the desktop environment. I am sure there are other things I can to too,

---

### Post by matt_symes on 2012-04-29
Hi

Well you really want to keep it. Check out this link for an explanation and rationale for /run

[http://lwn.net/Articles/436012/](http://lwn.net/Articles/436012/)

The directory get mounted in the  init script in init in initrd for your kernel version.

Extract you initramfs

```
mkdir tmp/initramfs
cd tmp/initramfs
gunzip -c /boot/initrd.img-3.2.0-24-generic | cpio -i -d -H newc --no-absolute-filenames
```Change the initrd file name as required.

```
nano init
```

```
mount -t tmpfs -o "nosuid,size=20%,mode=0755" tmpfs /run
```You can change the size there.

Kind regards

---

