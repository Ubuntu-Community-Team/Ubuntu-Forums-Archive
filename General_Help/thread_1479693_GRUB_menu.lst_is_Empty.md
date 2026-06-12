---
title: "GRUB menu.lst is Empty"
date: 2010-05-10
forum: General Help
---

### Post by exd7 on 2010-05-10
I don't use Ubuntu that much anymore, but I don't want to get rid of it, either (because I tried, and made a huge mistake of deleting its partitions.)
So I'm just settling for making Windows 7 the GRUB default to boot up in.

I tried GrubEd, but when I went to open up menu.lst through it, a blank file showed up. I navigated to /boot/grub, and I got the same thing on menu.lst.
Why is this, and is there another way to default to Windows?
There's another file, grub.cfg, which says in caps not to edit, but has a place that seems to select the default OS in the text. So I'm wondering if I should just ignore the do not edit part and change the default anyway.

Any suggestions?

---

### Post by uRock on 2010-05-10
Which version of ubuntu do you have installed?

---

### Post by jocko on 2010-05-10
> **exd7 said:**
> So I'm wondering if I should just ignore the do not edit part and change the default anyway.
No. You should not edit /boot/grub/grub.cfg (in fact it's even write protected to prevent you from doing it).
If you need to change the boot menu, edit the file /etc/default/grub and/or any of the files in /etc/grub.d.
To apply the changes to the boot menu, run:
```
sudo update-grub
```

---

### Post by Ozymandias_117 on 2010-05-10
You should be able to run ```
grep menuentry /boot/grub/grub.cfg
```

And find the exact name of your Windows boot. (Like my Linux boot is 'Ubuntu, with Linux 2.6.32-22-generic')

Make a backup of the file you're about to edit by typing ```
cp /etc/default/grub ~/grub.backup
```
Then type ```
gksudo gedit /etc/default/grub
``` and change ```
GRUB_DEFAULT=0
``` to ```
GRUB_DEFAULT="Ubuntu, with Linux 2.6.32-22-generic"
```(of course replace the Ubuntu, with Linux part to whatever you got for Windows)

save your changes and run ```
sudo update-grub
``` Then you're done!

---

### Post by exd7 on 2010-05-13
Sorry, I had thought I put the version in there. 10.04, beta 2 (whichever beta first supported the new Intel GPUs)

Anyway, thanks for your help! Ozymandias_117's method worked great; Windows is now the default OS in GRUB.

Thanks!

---

### Post by pqwoerituytrueiwoq on 2010-05-13
if you wanted to remove ubuntu complete from the hard disk
you will need the windows install disk you will need to 'fix' the MBR
in an xp boot cd i believe the command was ```
fixmbr
``` and answer yes to or 3 times

---

