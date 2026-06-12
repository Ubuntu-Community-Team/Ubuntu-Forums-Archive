---
title: "my girlfriends computer is booting up to &quot;Error : ELF header smaller than expected&quot;"
date: 2012-03-05
forum: General Help
---

### Post by LilianaVess33 on 2012-03-05
as the title suggests my girlfriends computer boots up to a screen that says "error : ELF headers smaller than expected".

a little background its a dual-booting (windows 7 and Ubuntu 11.10) dell insperion 1525 laptop.

does anyone know how I can fix this?

---

### Post by hakermania on 2012-03-05
Hello, here's a similar issue: [http://ubuntuforums.org/showthread.php?t=1593369](http://ubuntuforums.org/showthread.php?t=1593369)

---

### Post by HavarN on 2012-03-05
Sounds like you have installed a boot loader ment for an apple computer, which uses ELF. Are you using grub?

Try uninstalling whatever bootloader you are using except grub, then reinstall and update grub2.
This should normally only yield grub and syslinux related results:```
dpkg -l | grep [Bb]oot | grep load | grep ii
```

Reinstall grub2:```
sudo apt-get install grub-common grub-pc grub-pc-bin grub2-common
sudo update-grub2
```

---

### Post by LilianaVess33 on 2012-03-05
at the risk of sounding like a total noob, what are the straight vertical lines in that command?

---

### Post by CharlesA on 2012-03-05
They are pipes.

[http://www.linuxjournal.com/article/2156](http://www.linuxjournal.com/article/2156)

---

### Post by matt_symes on 2012-03-05
Hi

Are you seeing this ELF error and getting dropped to the grub rescue prompt ?

I am wondering if you have a corrupted grub configuration file.

From a LiveCD/USB what's the output of (from a terminal)

```
cat /boot/grub/grub.cfg
```

Maybe it's pointing to an invalid kernel or initramfs image.

As has been pointed out, reinstalling GRUB2 may also fix it.

Kind regards

---

### Post by LilianaVess33 on 2012-03-05
@CharlesA : Thank you, and thanks for not scoffing at me, lol.
  
@ matt_symes : yes that's exactly what's going on.

---

### Post by matt_symes on 2012-03-05
Hi

> **LilianaVess33 said:**
> @CharlesA : Thank you, and thanks for not scoffing at me, lol.

CharlesA would not do that. Were here to help :)
  
> @ matt_symes : yes that's exactly what's going on.

Do you have a LiveCD/USB handy ? If you do then boot up into it.

Mount your drive by clicking on it in Nautilus. 

Press ALT and F2 together and type

```
gedit /boot/grub/grub.cfg
```

Copy and paste the contents back here between code tags like this.

[noparse]```
results
```[/noparse]

to get output like this.

```
results
```

That may, and i stress may, be your problem (the configuration file) but i'm not sure.

Kind regards

---

### Post by broham on 2012-06-02
I encountered this problem today after running Update Manager which had a GRUB update.

I fixed the problem by following the instructions here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

