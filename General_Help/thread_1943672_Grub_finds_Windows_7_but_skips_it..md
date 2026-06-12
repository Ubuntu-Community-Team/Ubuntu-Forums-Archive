---
title: "Grub finds Windows 7 but skips it."
date: 2012-03-19
forum: General Help
---

### Post by gatech on 2012-03-19
Hey guys,
I'm a complete noob at Ubuntu and I have a dual-boot with Ubuntu 11.10 and Windows 7. The Windows Boot manager timeout is 0 so it boots straight to ubuntu and sometimes even skips grub but if I press the up key i think it is then grub shows. However Windows does not show up on it. There are three options. Ubuntu 11.10, Ubuntu Recovery, and Ubuntu 11.10 (generic mode)? I think anyways.
When I type sudo update-grub in terminal I get:


> Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found Windows Recovery Environment (loader) on /dev/sda1
Skipping Windows Recovery Environment (loader) on Wubi system
Found Windows 7 (loader) on /dev/sda2
Skipping Windows 7 (loader) on Wubi system
done
Any help would be greatly appreciated. I am tired of this problem. I am a student and the majority of my work requires access to Windows as my work is seated in special engineering programs that are too finicky in Ubuntu. Thanks in advance.

---

### Post by bcbc on 2012-03-20
It skips windows on purpose because it's intended to prevent users from thinking you can boot windows from the Wubi grub menu, and discourage them from setting Ubuntu as the default OS with a timeout of 0.

Because booting a wubi install goes like this:
Windows bootloader -> Windows boot sector -> Windows boot manager...
If you then select Ubuntu and go back to windows:
Grub menu -> windows boot sector -> Windows boot manager.

So I think you'll see the problem - whenever you hit the windows boot manager it goes straight through to Ubuntu and nothing you can do from Ubuntu will stop that.

The solution is to boot from a Windows repair CD, and change the timeout in the windows boot manager back to 10, or change the default. Something like this:
```
bcdedit /timeout 10
```

Some people have tried interrupting the windows boot manager with the F8 key or the Up arrow key - I've not heard it confirmed whether it has succeeded, but using the windows repair disk should fix it.

---

### Post by gatech on 2012-03-20
I tried the code you suggested and Terminal returned bcdedit: command not found.

---

### Post by bcbc on 2012-03-20
You need to do that from a Windows repair prompt, by booting a windows repair CD.

---

### Post by Flimm on 2013-01-19
Thanks for this info. I used it to answer a question on Ask Ubuntu, just FYI.

[http://askubuntu.com/a/245146/2355](http://askubuntu.com/a/245146/2355)

---

