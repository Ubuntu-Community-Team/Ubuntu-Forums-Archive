---
title: "Removable Disk (MP3 Player) issue."
date: 2006-05-09
forum: General Help
---

### Post by sprinkles on 2006-05-09
A few days ago, I accidently put a few incomplete downloads on my Samsung YH-J70.

Now I can't mount it, as I guess Ubuntu thinks it's corrupt.

When I double-click on "Sansung YH-J70" in 'Computer', I get the error:
"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount"

How can I mount it to take the corrupt files off, as I can't delete them on the device?

Thank You.

---

### Post by chettyk on 2006-05-09
You might try reformatting the device. I ran into a similar problem after a friend mistaken tried to stick my memory stick into the serial port of his computer. After I reformatted it, Ubuntu could recognised it immediately and auto-mounted it.

---

### Post by s_h_a_d_o_w_s on 2006-05-09
I had the exact same problem with my sony PSP. Ask aysiu how to fix it, it will work after.

---

### Post by s_h_a_d_o_w_s on 2006-05-09
Almost forgot, put your MP3 player in USB node, boot down, wait 20 mins, reboot, it might recognize. You also might have to format your player, sry.

---

