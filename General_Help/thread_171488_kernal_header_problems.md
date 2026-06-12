---
title: "kernal header problems"
date: 2006-05-06
forum: General Help
---

### Post by jsmidt on 2006-05-06
I am running 2.6.15-20-686 kernal but have installed 2.6.15-21-686.  Why does 2.6.15-21-686 not show up in grub.  The reason this is important is I instaled the headers for 2.6.15-21-686 but they don't work since I am running 2.6.15-20-686.  There are no headers for 2.6.15-20-686 so what do I do?

---

### Post by Sutekh on 2006-05-07
You could always change the GRUB menu so that it boots the new kernel, usually this is automatic, I don't know why it would not be so this time.

You can change the GRUB menu on the fly as you boot up and then change it once you boot the 2.6.15-21-386 kernel, or you can boot the 2.6.15-20-386 kernel, change the GRUB menu and reboot into the 2.6.15-21-386 kernel.

To boot the 2.6.15-21-386 kernel, select the 2.6.15-20-386 kernel in the GRUB menu and press 'e' to edit the entry.  On the line that starts with **kernel** press 'e' again to edit that line and change the '20' to '21'.  Do the same for the **initrd** line.  Once you are done press 'b' to boot the new kernel.

Once you boot into the 2.6.15-21-386 or if you choose to boot into the 2.6.15-20-386 kernel, you can edit your GRUB menu with these commands
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```
Either change the 2.6.15-20-386 entries to 2.6.15-21-386 or copy and paste (better way) them into the GRUB menu again and change the pasted entry to the newer kernel.

---

### Post by az on 2006-05-07
[QUOTE=jsmidt]I am running 2.6.15-20-686 kernal but have installed 2.6.15-21-686.  Why does 2.6.15-21-686 not show up in grub.  [/QUOTE]

Is it really installed?

sudo apt-get -f install

dpkg -l lgrep linux-image

---

