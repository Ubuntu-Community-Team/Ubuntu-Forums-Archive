---
title: "Crashing using new Kernel."
date: 2012-05-12
forum: General Help
---

### Post by chrispche on 2012-05-12
I have the following installed.

```
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

When I boot into 3.2.0-24-generic kernel I get what can only be described as some sort of blue screen of death. Although that's a Windows thing, it's the best way to describe it. I have to say this did not happen before I did an update.

However, if I boot into 3.0.0-17-generic Kernel, I don't get the crash.

My question is, how do I make Ubuntu boot into the 3.0.0-17-generic kernel by default. While I assume any bugs in the later Kernel got ironed out. 

On my update settings I have backports and unsupport backports enabled. This is my mistake I think.

Anyway advice and answer to my question would be greatly appreciated.

Thank you.

---

### Post by Enigmapond on 2012-05-12
The easy way would be to install Grub-Customizer and just put that kernel in the top position.

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

