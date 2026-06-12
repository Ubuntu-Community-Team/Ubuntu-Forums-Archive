---
title: "Display logs at boot time"
date: 2011-04-04
forum: General Help
---

### Post by sgb77 on 2011-04-04
Hi All,

Is there a way to display the boot logs as ubuntu is starting up? Call me old fashion, but I think it's better than staring at a pretty logo that does not tell me what's going on everytime I boot.
I am using 10.10

Thanks all.

---

### Post by matt_symes on 2011-04-04
Hi

You need to edit the kernel command line.

To test this and make sure you are happy reboot your PC and select your kernel.

Press the **e** key to edit your kernel command line. Look for  the line that says something like

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-30-generic root=UUID=3d48429c-7361-4ab8-8689-54407673b141 ro quiet splash
```

Delete the words quiet and splash and press ctrl + x to continue booting.

If you are happy with this you need to edit and rebuild grub. At a terminal type

```
sudo nano /etc/default/grub
```

Enter your password. It will not be echoed to the screen. This is normal.

Look for the line that says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and change to

```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

Press ctrl + o to save the file and ctrl + x to exit.

Then type 

```
sudo update-grub
```

After that reboot.

Kind regards

---

### Post by sgb77 on 2011-04-06
Worked like a charm! 
Now I know what was taking so much time during boot time.

Thanks!

---

