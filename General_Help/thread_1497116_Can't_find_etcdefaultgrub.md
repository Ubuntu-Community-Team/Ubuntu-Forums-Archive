---
title: "Can't find /etc/default/grub"
date: 2010-05-30
forum: General Help
---

### Post by airtacable on 2010-05-30
Hey guys, Hope you're all well,

I'm trying to fix my booting problems on 10.04 by following this [guide]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml"). Except the grub file is not in /etc/default. Grub is definitely installed (0.97 legacy) and the computer boots ok-ish so it must be somewhere.

Any ideas?

---

### Post by oldos2er on 2010-05-30
Those instructions are for grub2. Grub legacy uses /boot/grub/menu.lst as its config file. I am not sure how you would translate those instructions to something useful in grub legacy.

Is there some particular reason you're not using grub2?

---

### Post by WorMzy on 2010-05-30
I'm using grub legacy too. It's what I'm used to and I'm far too stubborn to switch to grub2.

Here's how I've edited my /boot/grub/menu.lst:

I've changed the normal entry, which for me looks like:

```
title        kernel 2.6.32-22-generic
root         (hd0,1)
kernel       /boot/vmlinuz-2.6.32-22-generic root=UUID=097bbeed-7751-448f-bfb5-01f9bc9d76ac ro quiet splash 
initrd       /boot/initrd.img-2.6.32-22-generic
savedefault
boot
```

to this:

```
title        kernel 2.6.32-22-generic
root         (hd0,1)
kernel       /boot/vmlinuz-2.6.32-22-generic root=UUID=097bbeed-7751-448f-bfb5-01f9bc9d76ac ro quiet splash [COLOR="Red"]nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap[/COLOR]
initrd       /boot/initrd.img-2.6.32-22-generic
savedefault
boot
```

I've also installed v86d, as suggested [here]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml"), and edited  /etc/initramfs-tools/modules to include ```
uvesafb mode_option=1024x768-24 mtrr=3 scroll=ywrap
```

I've also created a file at /etc/initramfs-tools/conf.d/splash with ```
FRAMEBUFFER=y
``` written in it.

After all that, I ran ```
sudo update-initramfs -u
``` and now my boot looks a little better, and the tty resolution is far better.

---

