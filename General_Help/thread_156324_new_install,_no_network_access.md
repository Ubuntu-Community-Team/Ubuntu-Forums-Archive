---
title: "new install, no network access"
date: 2006-04-06
forum: General Help
---

### Post by geuis on 2006-04-06
I installed ubuntu without having the computer connected to my network and the internet. During the install I got a warning that it couldn't find the dhcp server. I skipped over that step and finished the install.

Now the machine won't access the internet. I tried launching the Networking control panel under System but it doesn't open.

Any suggestions?

---

### Post by Azrael on 2006-04-06
Can you open a terminal and do: [I]cat /etc/network/interfaces

[/I]Among others the output should contain lines similar to the following:

auto eth0
iface eth0 inet dhcp

---

### Post by Phlosten on 2006-04-06
It is possible that Breezy is not detecting your network card. I have a problem with my computer in that my sound and networking do not function unless I disable ACPI.

You can check to see if your network card has been detected by running something like this: 'dmesg | grep eth' , in the terminal.

If there is no 'ethX' device you may want to try disabling ACPI like me and see if this brings up your network card.

To do this you need to edit your grub menu file like so.
Run 'sudo nano /boot/grub/menu.lst', and enter your password.
Scroll down the text file until you find something like the following.

-------------------
title                  Ubuntu, kernel 2.6.15-20-k7
root                 (hd0,0)
kernel              /boot/vmlinuz-2.6.15-20-k7 root=/dev/hda1 ro quiet splash
initrd                /boot/initrd.img-2.6.15-20-k7
savedefault
boot
-------------------

This is my Dapper boot kernel, so your breezy one should be an earlier version.
You just need to tack on 'acpi=off' to the end of the kernel line, so it looks like this:

-------------------
title                  Ubuntu, kernel 2.6.15-20-k7
root                 (hd0,0)
kernel              /boot/vmlinuz-2.6.15-20-k7 root=/dev/hda1 ro quiet splash acpi=off
initrd                /boot/initrd.img-2.6.15-20-k7
savedefault
boot
-------------------

Save the file with 'control-o' and 'enter', then exit with 'control-x'. Reboot and see if this brings up your network card and allows you to access your networking settings.

---

### Post by geuis on 2006-04-06
ok when I do cat it doesnt show those 2 lines. additionally, when I tried to sudo nano /etc/... or anytime I try sudo, I get an error 

"sudo: unable to lookup ubuntu via gethostbyname()"

Havent run into this one before. Next step?

---

### Post by Azrael on 2006-04-06
[quote=geuis]"sudo: unable to lookup ubuntu via gethostbyname()"[/quote]
A forum search on "gethostbyname()" indicates there might be something out of the ordinary with your hosts file. That's all I know..

---

