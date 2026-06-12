---
title: "Problem booting after reconfiguring boot screen - help!"
date: 2012-09-23
forum: General Help
---

### Post by pjrettin on 2012-09-23
After following the instructions I found below to change the boot screen, I now get the following message in a low graphics popup:

"Your system is running in low graphics mode".

I have to reboot into the grub menu and choose 'recovery' option and then choose 'resume boot' to get to my desktop.

How do I fix this?


Instructions I followed to get into this mess:

[INDENT]INSTALLATION INSTRUCTIONS

Step 1:

Download the Plymouth Sunrise deb file from here.

Step 2:

Open the Terminal (Ctrl-Alt-T) and type

gksudo nautilus

Step 3

    Copy ubuntu-sunrise folder to /lib/plymouth/themes
    Copy the file splash into /etc/initramfs-tools/conf.d (Optional, for better buffer)

Step 4:

Type in the terminal

sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-sunrise/ubuntu-sunrise.plymouth 200
sudo update-alternatives --config default.plymouth

Step 5:

Choose the number associated with ubuntu-sunrise in the options that pop up.

Step 6

Type in the terminal

sudo update-initramfs –u

Then

sudo reboot
[/INDENT]

---

