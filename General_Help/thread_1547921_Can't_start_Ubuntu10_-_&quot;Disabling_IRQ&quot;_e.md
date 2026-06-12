---
title: "Can't start Ubuntu10 - &quot;Disabling IRQ&quot; error, LiveCD only boots with &quot;noapic&quot;"
date: 2010-08-07
forum: General Help
---

### Post by Yaeka on 2010-08-07
I've just installed Ubuntu 10, but had to use the noapic boot option to do so.
Now I can only start the LiveCD with the noapic option, but still can't boot normally.

I keep getting the Disabling IRQ #4, #5, and #1 errors, if I don't check noapic.

I have no idea how to make it always start with noapic... ?

---

### Post by happyhamster on 2010-08-07
First, boot into the grub2 menu: keep the shift key pressed during the early stages of the boot process (it may take a few tries to get the menu to show though).

Select the kernel you want to boot (usually the first line) and press e. Now go to the huge line that starts with "linux /boot/vmlinuz-" and ends with "quiet splash" and add the noapic parameter to it. Then boot by pressing Ctrl-x.

If that works, you can make the change permanent by editing the file /etc/default/grub. Open a terminal (Applications-->Accessories-->Terminal) and run:
```

gksudo gedit /etc/default/grub

```
There should be a line, that looks like:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
Change that into:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"

```
Save (ctrl-s), and exit the text editor. Then update grub; again in the terminal:
```

sudo update-grub

```
Then do a normal reboot to see if it truly works. Good luck.

---

### Post by Yaeka on 2010-08-07
Yyyyyessss, thank youuuuu, at long last~~~
This grub2 thing was making it harder to find a solution...

Worked flawlessly <3

---

