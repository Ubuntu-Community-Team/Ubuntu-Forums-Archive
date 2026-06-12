---
title: "Problem with grub loader"
date: 2009-12-13
forum: General Help
---

### Post by oxas on 2009-12-13
Hey, i have installed ubuntu on my lapton(with windows running as main os). But now i have formatted the ubuntu disk from windows, and i can not start up windows anymore. it says:
GRUB loading,
error: no such disk
grub rescue>

I have tried to fix boot from windows cd, but won't work. Does anybody know how to fix this problem? i really need my computer with everything inside(on windows)

oXas.

---

### Post by lewisforlife on 2009-12-13
You will have to fix this from windows, boot into the recovery console, and run the following command:

```
fixmbr
```

This is not really a problem with grub at this point, grub was pointing to a location on your linux partition, if you formatted your Linux partition, you messed up your boot loader.  If you have any additional problems, it would be best to post on a Windows board.

---

### Post by john newbuntu on 2009-12-13
Is your BIOS set up to boot from your CD first.  If so, you should be able to put the rescue/recovery disk in and run fixmbr.

---

### Post by ShawnB391 on 2009-12-14
I'm also seeing this grub error on my laptop... I'm able to boot Linux from my usb drive but unable to boot windows. I reinstalled Linux onto my laptop, what can I do to point grub to my new Linux partition? My disc drive is broken and I can't use any CD/DVDs.

---

### Post by lewisforlife on 2009-12-14
> I'm also seeing this grub error on my laptop... I'm able to boot Linux from my usb drive but unable to boot windows. I reinstalled Linux onto my laptop, what can I do to point grub to my new Linux partition? My disc drive is broken and I can't use any CD/DVDs

Can you post the contents of your /boot/grub/menu.lst file, you can do this by running:

```
cat /boot/grub/menu.lst
```

You will have to update your menu.lst file, then run

```
update-grub
```

from a shell.

---

