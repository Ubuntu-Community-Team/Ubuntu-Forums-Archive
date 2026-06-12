---
title: "confusing GRUB2 - how do I set a given kernel?"
date: 2010-10-20
forum: General Help
---

### Post by TomaszC on 2010-10-20
I find GRUB2 somehow very confusing in configuration.

Supposing I have these kernel installed, plus, my own kernel in /boot/vmlinuz-custom:

# dpkg -l|grep linux-image
ii  linux-image-2.6.35-22-generic
ii  linux-image-2.6.36-020636rc8-generic

How can I make i.e. /boot/vmlinuz-custom a default boot entry?

For example, /etc/default/grub only has "GRUB_DEFAULT=0", which doesn't say which of these kernels it will be (i.e. vmlinuz-default, 2.6.35, or 2.6.36-rc*). /etc/grub.d/ is no less confusing.

In GRUB (legacy), it was a simple matter of adding a line to menu.lst - how do I do it with GRUB2?

---

### Post by drs305 on 2010-10-20
You can see how to set the default OS or kernel by visiting this thread:
[GRUB 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")


The kernel you want should be in the /boot folder.
Update grub with the following if you just added the new kernel:
```
sudo update-grub
```

In summary:
[LIST=1]
[*]View the entries in your Grub menu:
```
grep menuentry /boot/grub/grub.cfg
```
[*]Count to the entry you want, starting with 0. (The first menuentry is 0, the second is 1, etc)
[*]Open /etc/default/grub as root:
```
gksu gedit /etc/default/grub
```
[*]Change this value to the one you want:
> GRUB_DEFAULT=[COLOR="Red"]0[/COLOR]
Save the file.
[*]Update grub
```
sudo update-grub
```
[/LIST]

There are a variety of links in my signature line which explain how to understand and use Grub 2.

---

